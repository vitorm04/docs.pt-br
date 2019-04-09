---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 001f509e08780ec2d9776bcd6aed109ca0ff36a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113744"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Este exemplo demonstra como criar um canal de protocolo personalizado para usar cookies HTTP para o gerenciamento de sessão. Esse canal permite a comunicação entre serviços Windows Communication Foundation (WCF) e os clientes do ASMX ou entre clientes do WCF e serviços ASMX.  
  
 Quando um cliente chama um método Web em um Web service ASMX que é baseada em sessão, o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] mecanismo faz o seguinte:  
  
-   Gera uma ID exclusiva (ID de sessão).  
  
-   Gera o objeto de sessão e a associa a ID exclusiva.  
  
-   Adiciona a ID exclusiva para um cabeçalho de resposta HTTP Set-Cookie e o envia ao cliente.  
  
-   Identifica o cliente em chamadas subsequentes com base na ID de sessão envia a ele.  
  
 O cliente inclui a ID de sessão em suas solicitações subsequentes para o servidor. O servidor usa a ID de sessão do cliente para carregar o objeto de sessão apropriado para o contexto HTTP atual.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Padrão de troca de mensagem de canal HttpCookieSession  
 Este exemplo permite que as sessões para cenários semelhantes ASMX. Na parte inferior da nossa pilha de canais, temos o transporte HTTP que dá suporte a <xref:System.ServiceModel.Channels.IRequestChannel> e <xref:System.ServiceModel.Channels.IReplyChannel>. É o trabalho do canal para fornecer sessões para os níveis mais altos da pilha de canais. O exemplo implementa dois canais, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> e <xref:System.ServiceModel.Channels.IReplySessionChannel>) que dão suporte a sessões.  
  
## <a name="service-channel"></a>Canal de serviço  
 O exemplo fornece um canal de serviço no `HttpCookieReplySessionChannelListener` classe. Essa classe implementa a <xref:System.ServiceModel.Channels.IChannelListener> interface e converte os <xref:System.ServiceModel.Channels.IReplyChannel> canal da menor na pilha de canais para um <xref:System.ServiceModel.Channels.IReplySessionChannel>. Esse processo pode ser dividido nas seguintes partes:  
  
-   Quando o ouvinte de canais é aberto, ele aceita um canal interno de seu ouvinte interno. Como o ouvinte interno é um ouvinte de datagrama e o tempo de vida de um canal aceito é dissociado do tempo de vida do ouvinte, podemos fechar o ouvinte interno e apenas manter o canal interno  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Quando o processo de abertura é concluída, configuramos um loop de mensagem para receber mensagens do canal interno.  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   Quando uma mensagem chega, o canal de serviço examina o identificador de sessão e desprovisionar multiplexa as para o canal de sessão apropriado. O ouvinte de canais mantém um dicionário que mapeia os identificadores de sessão para as instâncias de canal de sessão.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 O `HttpCookieReplySessionChannel` classe implementa <xref:System.ServiceModel.Channels.IReplySessionChannel>. Chamada de pilha de níveis superiores do canal a <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> método para solicitações de leitura para esta sessão. Cada canal de sessão tem uma fila de mensagens particular que é preenchida pelo canal de serviço.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 No caso de quando alguém chama o <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> método e não existem mensagens na fila de mensagens, o canal espera por um período especificado de tempo antes de desligar em si. Isso limpa os canais de sessão criados para clientes não WCF.  
  
 Podemos usar o `channelMapping` para acompanhar o `ReplySessionChannels`, e não vamos fechar nosso subjacente `innerChannel` até que todos os canais aceitos foram fechados. Dessa maneira `HttpCookieReplySessionChannel` podem existir além do tempo de vida de `HttpCookieReplySessionChannelListener`. Nós também não precisa se preocupar sobre o ouvinte do lixo coletado sob nós, porque os canais aceitos manter uma referência ao seu ouvinte por meio de Introdução a `OnClosed` retorno de chamada.  
  
## <a name="client-channel"></a>Canal do cliente  
 O canal do cliente correspondente está no `HttpCookieSessionChannelFactory` classe. Durante a criação do canal, a fábrica de canais encapsula o canal de solicitação interna com um `HttpCookieRequestSessionChannel`. O `HttpCookieRequestSessionChannel` classe encaminha as chamadas para o canal de solicitação subjacente. Quando o cliente fecha o proxy, `HttpCookieRequestSessionChannel` envia uma mensagem para o serviço que indica que o canal está sendo fechado. Portanto, a pilha de canais de serviço normalmente pode encerrar o canal de sessão que está em uso.  
  
## <a name="binding-and-binding-element"></a>Associação e o elemento de associação  
 Depois de criar os canais de cliente e de serviço, a próxima etapa é integrá-los ao runtime do WCF. Canais são expostos para o WCF por meio de associações e elementos de associação. Uma associação consiste em um ou vários elementos de associação. O WCF oferece várias associações definidas pelo sistema; Por exemplo, BasicHttpBinding ou WSHttpBinding. O `HttpCookieSessionBindingElement` classe contém a implementação para o elemento de associação. Ele substitui o ouvinte de canais e os métodos de criação de fábrica de canal para fazer o canal necessário instanciações de fábrica de ouvinte ou de canal.  
  
 O exemplo usa as declarações de política para a descrição do serviço. Isso permite que o exemplo publicar seus requisitos de canal para outros clientes que podem consumir o serviço. Por exemplo, este elemento de associação publica as declarações de política para permitir que clientes potenciais sabe que ele oferece suporte a sessões. Como o exemplo permite que o `ExchangeTerminateMessage` propriedade na configuração do elemento de associação, ele adiciona as declarações necessárias para mostrar que o serviço oferece suporte a uma ação de troca extras de mensagem para encerrar a conversa de sessão. Os clientes podem, em seguida, usar essa ação. O código WSDL a seguir mostra as declarações de política criadas a partir de `HttpCookieSessionBindingElement`.  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 O `HttpCookieSessionBinding` classe é uma associação fornecida pelo sistema que usa o elemento de associação descrito anteriormente.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Adicionando o canal para o sistema de configuração  
 O exemplo fornece duas classes que expõem o canal de exemplo por meio da configuração. A primeira é uma <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> para o `HttpCookieSessionBindingElement`. A maior parte da implementação é delegada para o `HttpCookieSessionBindingConfigurationElement`, que é derivada de <xref:System.ServiceModel.Configuration.StandardBindingElement>. O `HttpCookieSessionBindingConfigurationElement` tem propriedades que correspondem às propriedades no `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Seção de extensão de elemento de associação  
 A seção `HttpCookieSessionBindingElementSection` é um <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> que expõe `HttpCookieSessionBindingElement` ao sistema de configuração. Com algumas substituições, o nome da seção de configuração, o tipo do elemento de associação e como criar o elemento de associação são definidos. Em seguida, podemos pode registrar a seção de extensão em um arquivo de configuração da seguinte maneira:  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a>Código de teste  
 Código de teste para usar esse transporte de exemplo está disponível nos diretórios de cliente e serviço. Ele consiste em dois testes — um teste usa uma associação com `allowCookies` definido como `true` no cliente. O segundo teste permite que o desligamento explícito (usando a troca de mensagens terminate) na associação.  
  
 Quando você executar o exemplo, você verá a seguinte saída:  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
