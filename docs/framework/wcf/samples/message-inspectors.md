---
title: Inspetores de mensagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d601a2dfb0daab4e54d6caac6940b4826cee0b01
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="message-inspectors"></a>Inspetores de mensagem
Este exemplo demonstra como implementar e configurar o cliente e o serviço inspetores de mensagem.  
  
 Um Inspetor de mensagens é um objeto de extensibilidade que pode ser usado em tempo de execução do modelo de serviço cliente e o tempo de execução de despacho programaticamente ou por meio de configuração e que pode inspecionar e alterar mensagens depois de serem recebidas ou antes de serem enviados.  
  
 Este exemplo implementa um cliente básico e o mecanismo de validação de mensagem de serviço que valida as mensagens de entrada em relação a um conjunto de documentos de esquema XML configuráveis. Observe que esse exemplo não valida mensagens para cada operação. Este é uma simplificação intencional.  
  
## <a name="message-inspector"></a>Inspetor de mensagem  
 Implementação de inspetores de mensagem do cliente a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface e o serviço implementar de inspetores de mensagem a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface. As implementações podem ser combinadas em uma única classe para formar um Inspetor de mensagem que funciona para ambos os lados. Este exemplo implementa tal um Inspetor de mensagem combinado. O Inspetor é construído passando um conjunto de esquemas em relação à qual as mensagens de entrada e saídas são validadas e permite que o desenvolvedor especificar se as mensagens de entrada ou saídas são validadas e se o Inspetor está no modo de expedição ou cliente, que afeta o tratamento de erro, conforme discutido posteriormente neste tópico.  
  
```  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Inspetor de mensagem qualquer serviço (distribuidor) deve implementar os dois <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> métodos <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>é invocado pelo dispatcher quando uma mensagem foi recebida, processada pela pilha de canais e atribuída a um serviço, mas antes de ser desserializado e enviada para uma operação. Se a mensagem de entrada foi criptografada, a mensagem já é descriptografada quando atingir o Inspetor de mensagem. O método obtém o `request` mensagem passada como um parâmetro de referência, que permite que a mensagem a ser inspecionado, manipulados ou substituído conforme necessário. O valor de retorno pode ser qualquer objeto e é usado como um objeto de estado de correlação que é passado para <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> quando o serviço retorna uma resposta para a mensagem atual. Neste exemplo, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delega a inspeção (validação) da mensagem para o método particular, local `ValidateMessageBody` e não retorna nenhum objeto de estado de correlação. Esse método garante que nenhuma mensagem inválida passa para o serviço.  
  
```  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>é invocado sempre que uma resposta está pronta para ser enviado para um cliente ou, no caso de mensagens unidirecionais, quando a mensagem de entrada foi processada. Isso permite que extensões de contagem que está sendo chamado simetricamente, independentemente de MEPS. Assim como acontece com <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, a mensagem é passada como um parâmetro de referência e pode ser inspecionada, modificada ou substituída. A validação da mensagem que é executada neste exemplo é delegada novamente para o `ValidMessageBody` método, mas o tratamento de erros de validação é ligeiramente diferente nesse caso.  
  
 Se ocorrer um erro de validação do serviço, o `ValidateMessageBody` método lança <xref:System.ServiceModel.FaultException>-derivado exceções. Em <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, essas exceções podem ser colocadas na infraestrutura do modelo de serviço em que eles são automaticamente transformados em falhas de SOAP e retransmitidos para o cliente. Em <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceções não devem ser colocadas em infraestrutura, como a transformação de exceções de falha geradas pelo serviço ocorre antes do Inspetor de mensagem é chamado. Portanto, a implementação a seguir captura o conhecido `ReplyValidationFault` exceção e substitui a resposta de mensagem com uma mensagem de falha explícita. Esse método garante que nenhum mensagens inválidas são retornadas pela implementação de serviço.  
  
```  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 O Inspetor de mensagem do cliente é muito semelhante. Os dois métodos que devem ser implementados de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> são <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> e <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>é invocado quando a mensagem tiver sido composta pelo aplicativo cliente ou pelo formatador de operação. Como com os inspetores de mensagem do dispatcher, a mensagem pode simplesmente ser inspecionado ou totalmente substituídos. Neste exemplo, o Inspetor de delega para o mesmo local `ValidateMessageBody` método auxiliar que também é usado para os inspetores de mensagem de expedição.  
  
 A diferença de comportamento entre a validação de cliente e de serviço (conforme especificado no construtor) é que a validação do cliente gera exceções locais que são colocadas em código de usuário porque eles ocorrem localmente e não devido a uma falha de serviço. Em geral, a regra é inspetores do serviço dispatcher geram falhas e inspetores de cliente lançam exceções.  
  
 Isso <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementação garante que nenhum inválido são enviadas para o serviço.  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 O `AfterReceiveReply` implementação garante que nenhuma mensagem inválida recebida do serviço é retransmitidas para o código de usuário do cliente.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 É a essência desse Inspetor de mensagem específica a `ValidateMessageBody` método. Para realizar seu trabalho, ele encapsula uma validação <xref:System.Xml.XmlReader> em torno do corpo conteúdo subárvore da mensagem passada. O leitor é preenchido com o conjunto de esquemas que contém o Inspetor de mensagem e o retorno de chamada de validação é definido como um delegado referindo-se para o `InspectionValidationHandler` que é definida com esse método. Para executar a validação, a mensagem é, em seguida, ler e em spool em uma memória baseado em fluxo <xref:System.Xml.XmlDictionaryWriter>. Se um erro de validação ou aviso ocorrer no processo, o método de retorno de chamada é invocado.  
  
 Se nenhum erro ocorrer, uma nova mensagem é construída que copia as propriedades e os cabeçalhos da mensagem original e usa o infoset validado agora no fluxo de memória, que é encapsulado por um <xref:System.Xml.XmlDictionaryReader> e adicionado à mensagem de substituição.  
  
```  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 O `InspectionValidationHandler` método é chamado pela validação <xref:System.Xml.XmlReader> sempre que um erro de validação de esquema ou o aviso ocorre. A implementação a seguir só funciona com erros e ignora todos os avisos.  
  
 Na primeira questão, pode parecer possível inserir uma validação <xref:System.Xml.XmlReader> na mensagem com o Inspetor de mensagens e permitem a validação ocorrer conforme a mensagem é processada e sem buffer de mensagem. Que, no entanto, significa que esse retorno de chamada gera as exceções de validação em algum lugar no serviço de modelo infraestrutura ou código de usuário como nós XML inválidos for detectados, resultando em um comportamento imprevisível. A abordagem de buffer protege o código de usuário de mensagens inválidas, inteiramente.  
  
 Como discutido anteriormente, as exceções geradas pelo manipulador diferem entre o cliente e o serviço. Sobre o serviço, as exceções são derivadas de <xref:System.ServiceModel.FaultException>, no cliente, as exceções são exceções personalizadas regulares.  
  
```  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Comportamento  
 Inspetores de mensagem são extensões para o tempo de execução do cliente ou o tempo de execução de expedição. Essas extensões são configurados usando *comportamentos*. Um comportamento é uma classe que altera o comportamento do tempo de execução de modelo de serviço alterando a configuração padrão ou adicionando extensões (como inspetores de mensagem) a ele.  
  
 O seguinte `SchemaValidationBehavior` classe é o comportamento usado para adicionar o Inspetor de mensagem neste exemplo para o cliente ou expedir o tempo de execução. A implementação é bastante básica em ambos os casos. Em <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> e <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, o Inspetor de mensagem é criado e adicionado para o <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> coleção de tempo de execução do respectivo.  
  
```  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
>  Esse comportamento específico não funcionar como um atributo e, portanto, não pode ser adicionado declarativamente para um tipo de contrato de um tipo de serviço. Esta é uma decisão de design feita porque a coleção de esquema não pode ser carregada em uma declaração de atributo e fazer referência a um local de configuração adicional (por exemplo, para as configurações do aplicativo) nesse atributo consiste na criação de um elemento de configuração não é consistente com o restante da configuração do modelo de serviço. Portanto, esse comportamento só pode ser adicionado imperativa por meio de código e uma extensão de configuração de modelo de serviço.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Adicionando o Inspetor de mensagem por meio da configuração  
 Para configurar um comportamento personalizado em um ponto de extremidade no arquivo de configuração do aplicativo, o modelo de serviço requer implementadores criar uma configuração *elemento de extensão* representado por uma classe derivada de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Essa extensão, em seguida, deve ser adicionada à seção de configuração do modelo de serviço para as extensões conforme mostrado para a seguinte extensão abordada nesta seção.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 As extensões podem ser adicionadas no aplicativo ou arquivo de configuração do ASP.NET, que é a opção mais comum, ou no arquivo de configuração da máquina.  
  
 Quando a extensão é adicionada a um escopo de configuração, o comportamento pode ser adicionado a uma configuração de comportamento, conforme mostrado no código a seguir. Configurações de comportamento são elementos reutilizáveis que podem ser aplicados a vários pontos de extremidade conforme necessário. Como o comportamento específico a ser configurada aqui implementa <xref:System.ServiceModel.Description.IEndpointBehavior>, só é válido na seção de configuração do respectivos no arquivo de configuração.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 O `<schemaValidator>` elemento que configura o Inspetor de mensagens é apoiado pela `SchemaValidationBehaviorExtensionElement` classe. A classe expõe duas propriedades públicas Boolianas denominadas `ValidateRequest` e `ValidateReply`. Ambos são marcados com um <xref:System.Configuration.ConfigurationPropertyAttribute>. Esse atributo constitui o vínculo entre as propriedades de código e os atributos XML que podem ser vistos no elemento de configuração XML anterior. A classe também tem uma propriedade `Schemas` Além disso, que é marcado com o <xref:System.Configuration.ConfigurationCollectionAttribute> e é do tipo `SchemaCollection`, que também faz parte deste exemplo mas omitido deste documento para fins de brevidade. Essa propriedade juntamente com a coleção e a classe de elemento de coleção `SchemaConfigElement` faz o `<schemas>` elemento no trecho de configuração anterior e permite adicionar uma coleção de esquemas para o conjunto de validação.  
  
 Substituído `CreateBehavior` método transforma os dados de configuração em um objeto de comportamento quando o tempo de execução avalia os dados de configuração, pois ele cria um cliente ou um ponto de extremidade.  
  
```  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>Adicionando inspetores de mensagem imperativa  
 Exceto por meio de atributos (que não é suportado neste exemplo para a razão citada anteriormente) e configuração, comportamentos podem facilmente ser adicionados a um tempo de execução do cliente e o serviço usando o código obrigatório. Neste exemplo, isso é feito no aplicativo cliente para testar o Inspetor de mensagem do cliente. O `GenericClient` classe é derivada de <xref:System.ServiceModel.ClientBase%601>, que expõe a configuração de ponto de extremidade para o código do usuário. Antes do cliente é implicitamente aberto a configuração de ponto de extremidade pode ser alterada, por exemplo adicionando comportamentos, conforme mostrado no código a seguir. Adicionar o comportamento do serviço é praticamente equivalente a técnica de cliente mostrado aqui e deve ser executado antes que o host de serviço é aberto.  
  
```  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a>Consulte também
