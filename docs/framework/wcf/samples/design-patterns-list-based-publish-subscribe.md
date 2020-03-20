---
title: 'Padrões de design: publicação-assinatura baseada em lista'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144754"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Padrões de design: publicação-assinatura baseada em lista
Esta amostra ilustra o padrão Publish-Subscribe baseado em lista implementado como um programa da Windows Communication Foundation (WCF).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O padrão de design Publish-Subscribe baseado em lista é descrito na publicação Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)). O padrão Publish-Subscribe passa informações para uma coleção de destinatários que se inscreveram em um tópico de informação. A assinatura de publicação baseada em listas mantém uma lista de assinantes. Quando há informações a serem compartilhadas, uma cópia é enviada a cada assinante da lista. Esta amostra demonstra um padrão dinâmico de assinatura de publicação baseado em lista, onde os clientes podem assinar ou cancelar a inscrição quantas vezes necessário.  
  
 A amostra Publish-Subscribe baseada em lista consiste em um cliente, um serviço e um programa de origem de dados. Pode haver mais de um cliente e mais de um programa de fonte de dados em execução. Os clientes assinam o serviço, recebem notificações e cancelam a inscrição. Os programas de fonte de dados enviam informações para o serviço para serem compartilhadas com todos os assinantes atuais.  
  
 Nesta amostra, o cliente e a fonte de dados são programas de console (.exe files) e o serviço é uma biblioteca (.dll) hospedada no Internet Information Services (IIS). A atividade do cliente e da fonte de dados são visíveis na área de trabalho.  
  
 O serviço usa comunicação duplex. O `ISampleContract` contrato de serviço é `ISampleClientCallback` emparelhado com um contrato de retorno de chamada. O serviço implementa operações de serviço de Assinatura e Cancelamento, que os clientes usam para participar ou sair da lista de assinantes. O serviço também `PublishPriceChange` implementa a operação do serviço, que o programa de fonte de dados chama para fornecer ao serviço novas informações. O programa cliente `PriceChange` implementa a operação do serviço, que o serviço chama para notificar todos os assinantes de uma mudança de preço.  
  
```csharp  
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
  
 O serviço usa um evento .NET Framework como mecanismo para informar todos os assinantes sobre novas informações. Quando um cliente entra no serviço ligando para Assinar, ele fornece um manipulador de eventos. Quando um cliente sai, ele cancela a inscrição de seu manipulador de eventos do evento. Quando uma fonte de dados liga para o serviço para relatar uma mudança de preço, o serviço aumenta o evento. Isso chama cada instância do serviço, uma para cada cliente que se inscreveu e faz com que seus manipuladores de eventos executem. Cada manipulador de eventos passa as informações ao seu cliente através de sua função de retorno de chamada.  
  
```csharp
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
  
 Quando você executar a amostra, lance vários clientes. Os clientes assinam o serviço. Em seguida, execute o programa de origem de dados, que envia informações para o serviço. O serviço repassa as informações a todos os assinantes. Você pode ver a atividade em cada console do cliente confirmando que as informações foram recebidas. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar a amostra na mesma máquina  
  
1. Teste que você pode acessar o serviço usando `http://localhost/servicemodelsamples/service.svc`um navegador inserindo o seguinte endereço: . Uma página de confirmação deve ser exibida em resposta.  
  
2. Executar Client.exe a partir\\de \client\bin , a partir da pasta específica do idioma. A atividade do cliente é exibida na janela do console do cliente. Lançar vários clientes.  
  
3. Executar Datasource.exe a partir\\de \datasource\bin , a partir da pasta específica do idioma. A atividade de origem de dados é exibida na janela do console. Uma vez que a fonte de dados envia informações para o serviço, ela deve ser repassada a cada cliente.  
  
4. Se o cliente, a fonte de dados e os programas de serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar a amostra através de máquinas  
  
1. Configure a máquina de serviço:  
  
    1. Na máquina de serviço, crie um diretório virtual chamado ServiceModelSamples. O arquivo em lote Setupvroot.bat do [Procedimento de Configuração Única para a Fundação de Comunicação do Windows Amostras](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.  
  
    2. Copie os arquivos do programa de serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples na máquina de serviço. Certifique-se de incluir os arquivos no diretório \bin.  
  
    3. Teste que você pode acessar o serviço a partir da máquina cliente usando um navegador.  
  
2. Configure as máquinas clientes:  
  
    1. Copie os arquivos do programa cliente da pasta \client\bin\\ na pasta específica do idioma para as máquinas clientes.  
  
    2. Em cada arquivo de configuração do cliente, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço. Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.  
  
3. Configure a máquina de origem de dados:  
  
    1. Copie os arquivos do programa de origem de dados da pasta \datasource\bin\\ na pasta específica do idioma para a máquina de origem de dados.  
  
    2. No arquivo de configuração de origem de dados, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço. Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.  
  
4. Nas máquinas clientes, inicie client.exe a partir de um prompt de comando.  
  
5. Na máquina de origem de dados, inicie Datasource.exe a partir de um prompt de comando.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
