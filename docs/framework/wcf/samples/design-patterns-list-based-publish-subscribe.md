---
title: 'Padrões de design: publicação-assinatura baseada em lista'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 2807cc8cc197ff39417e3b6375ebbd595cf73c54
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265020"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Padrões de design: publicação-assinatura baseada em lista
Este exemplo ilustra o padrão baseado em lista publicar-assinar, implementado como um programa do Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O padrão de design baseada em lista publicar-assinar a publicação do Microsoft Patterns & Practices, descrito [padrões de integração](https://go.microsoft.com/fwlink/?LinkId=95894). O padrão de publicação-assinatura passa informações para uma coleção de destinatários que tenha se inscrito para um tópico de informações. Baseada em lista de publicação / assinatura mantém uma lista de assinantes. Quando há informações para compartilhar, uma cópia é enviada para cada assinante na lista. Este exemplo demonstra um dinâmico baseado em lista padrão, em que os clientes podem assinar ou cancelar a assinatura quantas vezes for necessário publicar-assinar.  
  
 O exemplo de lista com base publicar-assinar consiste em um cliente, um serviço e um programa de fonte de dados. Pode haver mais de um cliente e mais de um programa de fonte de dados em execução. Os clientes assinarem o serviço, recebem notificações e cancelar a assinatura. Programas de origem de dados enviam informações para o serviço para ser compartilhado com todos os assinantes atuais.  
  
 Nessa fonte de exemplo, o cliente e os dados são programas de console (.exe arquivos) e o serviço é uma biblioteca (. dll) hospedada no Internet Information Services (IIS). Atividade de origem do cliente e os dados são visíveis na área de trabalho.  
  
 O serviço usa comunicação duplex. O `ISampleContract` contrato de serviço é associado a um `ISampleClientCallback` contrato de retorno de chamada. O serviço implementa as operações de serviço Subscribe e Unsubscribe, quais os clientes usam para ingressar ou deixar a lista de assinantes. O serviço também implementa o `PublishPriceChange` operação de serviço, que chama o programa de origem de dados para fornecer o serviço com novas informações. O programa cliente implementa o `PriceChange` operação de serviço, que o serviço é chamado para notificar todos os assinantes de uma alteração de preço.  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 O serviço usa um evento do .NET Framework como o mecanismo para informar a todos os assinantes sobre novas informações. Quando um cliente se associa o serviço por chamada para inscrição, ele fornece um manipulador de eventos. Quando um cliente sair, ele cancela a assinatura de seu manipulador de eventos do evento. Quando uma fonte de dados chama o serviço para relatar uma alteração de preço, o serviço gera o evento. Isso chama cada instância do serviço, uma para cada cliente que se inscreveu e faz com que os manipuladores de evento executar. Cada manipulador de eventos passa as informações para seu cliente por meio de sua função de retorno de chamada.  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 Quando você executar o exemplo, inicie vários clientes. Os clientes assinem o serviço. Em seguida, execute o programa de fonte de dados, que envia informações ao serviço. O serviço passa as informações para todos os assinantes. Você pode ver a atividade em cada console do cliente confirmando que as informações foram recebidas. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina  
  
1.  Teste que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: http://localhost/servicemodelsamples/service.svc. Uma página de confirmação deve ser exibida na resposta.  
  
2.  Executar Client.exe de \Client\Bin.\\, sob a pasta de idioma específico. Atividade do cliente é exibida na janela do console do cliente. Inicie vários clientes.  
  
3.  Executar Datasource.exe de \datasource\bin\\, sob a pasta de idioma específico. Atividade de origem de dados é exibida na janela do console. Depois que a fonte de dados envia informações ao serviço, ela deve ser passada para cada cliente.  
  
4.  Se o cliente, fonte de dados e programas de serviço não ficam capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo entre máquinas  
  
1.  Configure o computador de serviço:  
  
    1.  No computador do serviço, crie um diretório virtual chamado ServiceModelSamples. O lote de Setupvroot.bat do arquivo a [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.  
  
    2.  Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ao diretório virtual ServiceModelSamples na máquina do serviço. Certifique-se de incluir os arquivos no diretório \bin.  
  
    3.  Teste que você pode acessar o serviço no computador cliente usando um navegador.  
  
2.  Configure os computadores cliente:  
  
    1.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para os computadores cliente.  
  
    2.  Em cada arquivo de configuração do cliente, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
3.  Configure o computador de origem de dados:  
  
    1.  Copie os arquivos de programa da fonte de dados da pasta \datasource\bin\, sob a pasta de idioma específico, o computador de origem de dados.  
  
    2.  No arquivo de configuração de fonte de dados, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
4.  Em computadores cliente, inicie o Client.exe em um prompt de comando.  
  
5.  No computador de origem de dados, inicie Datasource.exe em um prompt de comando.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a>Consulte também
