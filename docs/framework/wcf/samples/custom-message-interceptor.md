---
title: Interceptor de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344267"
---
# <a name="custom-message-interceptor"></a>Interceptor de mensagem personalizado
Este exemplo demonstra o uso do modelo de extensibilidade do canal. Em particular, ele mostra como implementar um elemento de associação personalizado que cria as fábricas de canais e ouvintes de canais para interceptar todas as mensagens de entrada e saídas em um ponto específico na pilha de tempo de execução. O exemplo também inclui um cliente e servidor que demonstram o uso dessas fábricas personalizadas.  
  
 Neste exemplo, o cliente e o serviço são programas de console (.exe). O cliente e o serviço que ambos fazer usam de uma biblioteca comum (. dll) que contém o elemento de associação personalizado e seus objetos de tempo de execução associados.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 O exemplo descreve o procedimento recomendado para a criação de um canal personalizado de em camadas no Windows Communication Foundation (WCF), usando a estrutura de canais e seguir as práticas recomendadas do WCF. As etapas para criar um canal personalizado de em camadas são da seguinte maneira:  
  
1. Decida quais das formas de canal oferecerá suporte a sua fábrica de canais e o ouvinte de canais.  
  
2. Crie uma fábrica de canais e um ouvinte de canais que dão suporte a suas formas de canal.  
  
3. Adicione um elemento de associação que adiciona o canal em camadas personalizado a uma pilha de canais.  
  
4. Adicione uma seção de extensão de elemento de associação para expor o novo elemento de associação para o sistema de configuração.  
  
## <a name="channel-shapes"></a>Formas de canal  
 A primeira etapa ao escrever um canal personalizado de em camadas é decidir quais formas são necessárias para o canal. Para nosso Inspetor de mensagens, há suporte para qualquer forma que a camada abaixo nos dá suporte a (por exemplo, se a camada abaixo nos pode compilar <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, em seguida, podemos também expor <xref:System.ServiceModel.Channels.IOutputChannel> e <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Fábrica de canais e fábrica de escuta  
 A próxima etapa na escrita de um canal personalizado de em camadas é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço.  
  
 Essas classes levar um alocador interno e um ouvinte e delegar tudo, exceto os `OnCreateChannel` e `OnAcceptChannel` chamadas para a fábrica interna e o ouvinte.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 O exemplo define um elemento de associação personalizada: `InterceptingBindingElement`. `InterceptingBindingElement` leva um `ChannelMessageInterceptor` como uma entrada e usa isso `ChannelMessageInterceptor` para manipular as mensagens que passam por ela. Isso é a única classe que deve ser pública. O factory, o ouvinte e canais podem ser internas implementações das interfaces públicas do tempo de execução.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para integrar com a configuração de associação, a biblioteca define um manipulador de seção de configuração como uma seção de extensão de elemento de associação. Os arquivos de configuração do cliente e o servidor devem registrar a extensão de elemento de associação com o sistema de configuração. Os implementadores que desejam expor seu elemento de associação para o sistema de configuração podem derivar dessa classe.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Adicionar política  
 Integrar com nosso sistema de política, `InterceptingBindingElement` implementa IPolicyExportExtension para sinalizar que podemos deve participar de geração de política. Para dar suporte à importação de política em um cliente gerado, o usuário pode registrar uma classe derivada de `InterceptingBindingElementImporter` e substituir `CreateMessageInterceptor`() para gerar a sua política habilitada `ChannelMessageInterceptor` classe.  
  
## <a name="example-droppable-message-inspector"></a>Exemplo: Inspetor de mensagens droppable  
 Incluído no exemplo é um exemplo de implementação de `ChannelMessageInspector` que descarta mensagens.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Você pode acessá-lo da configuração da seguinte maneira:  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 O cliente e servidor usam esta seção de configuração recém-criada para inserir as fábricas personalizadas no nível mais baixo de suas pilhas de canal do tempo de execução (acima do nível de transporte).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 O cliente usa o `MessageInterceptor` numerados de biblioteca para adicionar um cabeçalho personalizado para até mesmo mensagens. O serviço por outro lado usa `MessageInterceptor` biblioteca para descartar todas as mensagens que não têm esse cabeçalho especial.  
  
 Você verá a seguinte saída de cliente depois de executar o serviço e, em seguida, o cliente.  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 O cliente relata 10 velocidades de vento diferentes para o serviço, mas somente marcas metade com o cabeçalho especial.  
  
 No serviço, você deverá ver a saída a seguir:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Execute Service.exe primeiro, em seguida, executar Client.exe e assista a ambas as janelas do console de saída.  
