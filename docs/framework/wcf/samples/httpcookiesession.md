---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183622"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Esta amostra demonstra como construir um canal de protocolo personalizado para usar cookies HTTP para gerenciamento de sessões. Este canal permite a comunicação entre os serviços da Windows Communication Foundation (WCF) e os clientes ASMX ou entre clientes WCF e serviços ASMX.  
  
 Quando um cliente chama um método Web em um serviço WEB ASMX baseado em sessão, o mecanismo ASP.NET faz o seguinte:  
  
- Gera um ID único (ID de sessão).  
  
- Gera o objeto de sessão e o associa ao ID único.  
  
- Adiciona o ID exclusivo a um cabeçalho de resposta HTTP do Set-Cookie e envia-o ao cliente.  
  
- Identifica o cliente em chamadas subseqüentes com base no ID de sessão que ele envia para ele.  
  
 O cliente inclui este ID de sessão em suas solicitações subseqüentes ao servidor. O servidor usa o ID de sessão do cliente para carregar o objeto de sessão apropriado para o contexto HTTP atual.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Padrão de troca de mensagens do canal httpcookiesession  
 Esta amostra permite sessões para cenários semelhantes ao ASMX. Na parte inferior da nossa pilha de canais, <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel>temos o transporte HTTP que suporta e . É trabalho do canal fornecer sessões para os níveis mais altos da pilha de canais. A amostra implementa dois<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>canais, (e ) que suportam sessões.  
  
## <a name="service-channel"></a>Canal de Serviços  
 A amostra fornece um `HttpCookieReplySessionChannelListener` canal de serviço na classe. Esta classe implementa a <xref:System.ServiceModel.Channels.IChannelListener> interface <xref:System.ServiceModel.Channels.IReplyChannel> e converte o canal <xref:System.ServiceModel.Channels.IReplySessionChannel>de inferior na pilha de canais para um . Este processo pode ser dividido nas seguintes partes:  
  
- Quando o ouvinte do canal é aberto, ele aceita um canal interno de seu ouvinte interno. Como o ouvinte interno é um ouvinte de datagrama e a vida de um canal aceito é dissociada da vida do ouvinte, podemos fechar o ouvinte interno e apenas segurar o canal interno  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Quando o processo aberto é concluído, configuramos um loop de mensagem para receber mensagens do canal interno.  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- Quando uma mensagem chega, o canal de serviço examina o identificador de sessão e os desmultiplexes para o canal de sessão apropriado. O ouvinte do canal mantém um dicionário que mapeia os identificadores de sessão para as instâncias do canal de sessão.  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 A `HttpCookieReplySessionChannel` classe <xref:System.ServiceModel.Channels.IReplySessionChannel>implementa. Níveis mais altos da <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> pilha de canais chamam o método para ler solicitações para esta sessão. Cada canal de sessão tem uma fila de mensagens privada que é preenchida pelo canal de serviço.  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 No caso em que <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> alguém chama o método e não há mensagens na fila de mensagens, o canal espera por um determinado período de tempo antes de se desligar. Isso limpa os canais de sessão criados para clientes não-WCF.  
  
 Usamos o `channelMapping` para `ReplySessionChannels`rastrear o , e não `innerChannel` fechamos nosso si mesmo até que todos os canais aceitos tenham sido fechados. Desta `HttpCookieReplySessionChannel` forma pode existir `HttpCookieReplySessionChannelListener`além da vida de . Também não temos que nos preocupar com o ouvinte recebendo lixo coletado em baixo `OnClosed` de nós porque os canais aceitos mantêm uma referência ao seu ouvinte através do retorno de chamada.  
  
## <a name="client-channel"></a>Canal do cliente  
 O canal do cliente `HttpCookieSessionChannelFactory` correspondente está na classe. Durante a criação do canal, a fábrica `HttpCookieRequestSessionChannel`do canal envolve o canal de solicitação interna com um . A `HttpCookieRequestSessionChannel` classe encaminha as chamadas para o canal de solicitação subjacente. Quando o cliente fecha `HttpCookieRequestSessionChannel` o proxy, envia uma mensagem para o serviço que indica que o canal está sendo fechado. Assim, a pilha de canais de serviço pode desligar graciosamente o canal de sessão que está em uso.  
  
## <a name="binding-and-binding-element"></a>Elemento de vinculação e vinculação  
 Depois de criar os canais de atendimento e cliente, o próximo passo é integrá-los ao tempo de execução do WCF. Os canais são expostos ao WCF através de amarras e elementos de ligação. Uma ligação consiste em um ou muitos elementos de ligação. O WCF oferece várias vinculações definidas pelo sistema; por exemplo, BasicHttpBinding ou WSHttpBinding. A `HttpCookieSessionBindingElement` classe contém a implementação para o elemento de vinculação. Ele substitui os métodos de criação do ouvinte do canal e da fábrica do canal para fazer as instanciações necessárias do ouvinte do canal ou da fábrica do canal.  
  
 A amostra usa afirmações de políticas para a descrição do serviço. Isso permite que a amostra publique suas necessidades de canal para outros clientes que possam consumir o serviço. Por exemplo, esse elemento vinculante publica afirmações de políticas para que os clientes em potencial saibam que ele suporta sessões. Como a amostra `ExchangeTerminateMessage` habilita a propriedade na configuração do elemento de vinculação, ela adiciona as afirmações necessárias para mostrar que o serviço suporta uma ação extra de troca de mensagens para encerrar a conversa da sessão. Os clientes podem então usar essa ação. O código WSDL a seguir mostra as `HttpCookieSessionBindingElement`afirmações de políticas criadas a partir do .  
  
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
  
 A `HttpCookieSessionBinding` classe é uma vinculação fornecida pelo sistema que usa o elemento de vinculação descrito anteriormente.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Adicionando o Canal ao Sistema de Configuração  
 A amostra fornece duas classes que expõem o canal amostral através da configuração. O primeiro <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> é `HttpCookieSessionBindingElement`um para o . A maior parte da implementação `HttpCookieSessionBindingConfigurationElement`é delegada <xref:System.ServiceModel.Configuration.StandardBindingElement>ao , que deriva de . O `HttpCookieSessionBindingConfigurationElement` tem propriedades que correspondem às propriedades em `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Seção de extensão do elemento de vinculação  
 A `HttpCookieSessionBindingElementSection` seção <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> é `HttpCookieSessionBindingElement` uma que se expõe ao sistema de configuração. Com algumas substituições do nome da seção de configuração, o tipo do elemento de vinculação e como criar o elemento de vinculação são definidos. Podemos então registrar a seção de extensão em um arquivo de configuração da seguinte forma:  
  
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
 O código de teste para o uso deste transporte de amostra está disponível nos diretórios Cliente e Serviço. Ele consiste em dois testes — um `allowCookies` teste `true` usa uma vinculação com set para o cliente. O segundo teste permite o desligamento explícito (usando a troca de mensagens de término) na vinculação.  
  
 Ao executar a amostra, você deve ver a seguinte saída:  
  
```console  
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
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
