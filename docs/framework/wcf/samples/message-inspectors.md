---
title: Inspetores de mensagem
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 705401a182d5d816bc2682f5f21ff09ca95f21c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144442"
---
# <a name="message-inspectors"></a>Inspetores de mensagem
Esta amostra demonstra como implementar e configurar inspetores de mensagens de clientee serviço.  
  
 Um inspetor de mensagens é um objeto de extensibilidade que pode ser usado no tempo de execução do cliente do modelo de serviço e despachar tempo de execução programática ou através da configuração e que pode inspecionar e alterar mensagens depois de recebidas ou antes de serem enviadas.  
  
 Esta amostra implementa um mecanismo básico de validação de mensagens de cliente e serviço que valida mensagens recebidas contra um conjunto de documentos XML Schema configuráveis. Observe que esta amostra não valida mensagens para cada operação. É uma simplificação intencional.  
  
## <a name="message-inspector"></a>Inspetor de Mensagens  
 Os inspetores de <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> mensagens do cliente <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> implementam a interface e os inspetores de mensagens de serviço implementam a interface. As implementações podem ser combinadas em uma única classe para formar um inspetor de mensagens que funcione para ambos os lados. Esta amostra implementa um inspetor de mensagens combinado. O inspetor é construído passando em um conjunto de esquemas contra os quais as mensagens recebidas e enviadas são validadas e permite que o desenvolvedor especifique se as mensagens recebidas ou enviadas são validadas e se o inspetor está no modo de expedição ou cliente, que afeta o tratamento de erros como discutido posteriormente neste tópico.  
  
```csharp
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
  
 Qualquer inspetor de mensagens de serviço <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> (despachante) deve implementar os dois métodos <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>é invocado pelo despachante quando uma mensagem foi recebida, processada pela pilha de canais e atribuída a um serviço, mas antes de ser desserializada e enviada para uma operação. Se a mensagem recebida foi criptografada, a mensagem já será descriptografada quando chegar ao inspetor de mensagens. O método `request` faz com que a mensagem seja passada como um parâmetro de referência, o que permite que a mensagem seja inspecionada, manipulada ou substituída conforme necessário. O valor de devolução pode ser qualquer objeto e <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> é usado como um objeto de estado de correlação que é passado para quando o serviço retorna uma resposta à mensagem atual. Nesta amostra, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delega a inspeção (validação) da mensagem ao método `ValidateMessageBody` privado local e não retorna nenhum objeto de estado de correlação. Este método garante que nenhuma mensagem inválida passe para o serviço.  
  
```csharp  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>é invocado sempre que uma resposta está pronta para ser enviada de volta para um cliente, ou no caso de mensagens unidirecionais, quando a mensagem recebida foi processada. Isso permite que as extensões contem em ser chamadas simetricamente, independentemente do MEP. Como <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>acontece, a mensagem é passada como parâmetro de referência e pode ser inspecionada, modificada ou substituída. A validação da mensagem que é realizada nesta `ValidMessageBody` amostra é novamente delegada ao método, mas o manuseio de erros de validação é ligeiramente diferente neste caso.  
  
 Se ocorrer um erro de `ValidateMessageBody` validação <xref:System.ServiceModel.FaultException>no serviço, o método lançará exceções derivadas. Em <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, essas exceções podem ser colocadas na infra-estrutura do modelo de serviço onde são automaticamente transformadas em falhas soap e retransmitidas ao cliente. Em <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> , exceções não devem ser colocadas na infra-estrutura, porque a transformação de exceções de falhas lançadas pelo serviço ocorre antes do inspetor de mensagens ser chamado. Portanto, a implementação `ReplyValidationFault` a seguir captura a exceção conhecida e substitui a mensagem de resposta por uma mensagem de falha explícita. Este método garante que nenhuma mensagem inválida seja devolvida pela implementação do serviço.  
  
```csharp  
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
  
 O inspetor de mensagens do cliente é muito parecido. Os dois métodos que <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> devem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>ser implementados são e .  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>é invocado quando a mensagem foi composta pelo aplicativo do cliente ou pela operação formatter. Como acontece com os inspetores de mensagens do despachante, a mensagem pode ser inspecionada ou totalmente substituída. Nesta amostra, o inspetor delega `ValidateMessageBody` o mesmo método auxiliar local que também é usado para os inspetores de mensagens de despacho.  
  
 A diferença comportamental entre a validação do cliente e do serviço (conforme especificado no construtor) é que a validação do cliente lança exceções locais que são colocadas no código do usuário porque ocorrem localmente e não por causa de uma falha de serviço. Geralmente, a regra é que os inspetores de serviço saem com falhas e que os inspetores de clientes atiram exceções.  
  
 Essa <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementação garante que nenhuma mensagem inválida seja enviada ao serviço.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 A `AfterReceiveReply` implementação garante que nenhuma mensagem inválida recebida do serviço seja retransmitida para o código do usuário cliente.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 O coração deste inspetor de `ValidateMessageBody` mensagens em particular é o método. Para realizar seu trabalho, ele envolve <xref:System.Xml.XmlReader> uma validação em torno da subárvore de conteúdo corporal da mensagem passada. O leitor é preenchido com o conjunto de esquemas que o inspetor de mensagens possui `InspectionValidationHandler` e o retorno de chamada de validação é definido para um delegado referente ao que é definido ao lado deste método. Para realizar a validação, a mensagem é então lida <xref:System.Xml.XmlDictionaryWriter>e colocada em um fluxo de memória apoiado . Se ocorrer um erro de validação ou aviso no processo, o método de retorno de chamada será invocado.  
  
 Se não ocorrer nenhum erro, uma nova mensagem é construída que copia as propriedades e os cabeçalhos da <xref:System.Xml.XmlDictionaryReader> mensagem original e usa o infoset agora validado no fluxo de memória, que é embrulhado por um e adicionado à mensagem de substituição.  
  
```csharp  
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
  
 O `InspectionValidationHandler` método é chamado pela <xref:System.Xml.XmlReader> validação sempre que ocorre um erro de validação de esquema ou aviso. A implementação a seguir só funciona com erros e ignora todos os avisos.  
  
 Em primeira consideração, pode parecer possível injetar <xref:System.Xml.XmlReader> uma validação na mensagem com o inspetor de mensagens e deixar que a validação aconteça à medida que a mensagem é processada e sem buffer da mensagem. Isso, no entanto, significa que esse retorno de chamada lança as exceções de validação em algum lugar na infra-estrutura do modelo de serviço ou no código do usuário à medida que os nós XML inválidos são detectados, resultando em comportamento imprevisível. A abordagem de buffering protege o código do usuário de mensagens inválidas, inteiramente.  
  
 Como discutido anteriormente, as exceções lançadas pelo manipulador diferem entre o cliente e o serviço. No serviço, as exceções são <xref:System.ServiceModel.FaultException>derivadas, no cliente, as exceções são exceções personalizadas regulares.  
  
```csharp  
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
 Os inspetores de mensagens são extensões para o tempo de execução do cliente ou o tempo de execução do despacho. Tais extensões são configuradas usando *comportamentos*. Um comportamento é uma classe que altera o comportamento do tempo de execução do modelo de serviço alterando a configuração padrão ou adicionando extensões (como inspetores de mensagens) a ele.  
  
 A `SchemaValidationBehavior` classe a seguir é o comportamento usado para adicionar o inspetor de mensagens desta amostra ao cliente ou despachar tempo de execução. A implementação é bastante básica em ambos os casos. Dentro <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>e , o inspetor de mensagens é criado e adicionado à <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> coleta do respectivo tempo de execução.  
  
```csharp
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
> Esse comportamento em particular não dobra como um atributo e, portanto, não pode ser adicionado declarativamente a um tipo de contrato de um tipo de serviço. Esta é uma decisão por design tomada porque a coleção de esquemas não pode ser carregada em uma declaração de atributo e referindo-se a um local de configuração extra (por exemplo, para as configurações do aplicativo) neste atributo significa criar um elemento de configuração que não é consistente com o resto da configuração do modelo de serviço. Portanto, esse comportamento só pode ser adicionado imperativamente através de código e através de uma extensão de configuração do modelo de serviço.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Adicionando o Inspetor de Mensagens através da configuração  
 Para configurar um comportamento personalizado em um ponto final no arquivo de configuração do aplicativo, o modelo <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>de serviço requer que os implementadores criem um elemento de *extensão* de configuração representado por uma classe derivada de . Essa extensão deve então ser adicionada à seção de configuração do modelo de serviço para extensões, conforme mostrado para a seguinte extensão discutida nesta seção.  
  
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
  
 As extensões podem ser adicionadas no aplicativo ou ASP.NET arquivo de configuração, que é a escolha mais comum, ou no arquivo de configuração da máquina.  
  
 Quando a extensão é adicionada a um escopo de configuração, o comportamento pode ser adicionado a uma configuração de comportamento como é mostrado no código a seguir. As configurações de comportamento são elementos reutilizáveis que podem ser aplicados a vários pontos finais, conforme necessário. Como o comportamento específico a ser <xref:System.ServiceModel.Description.IEndpointBehavior>configurado aqui é implementado, ele só é válido na respectiva seção de configuração no arquivo de configuração.  
  
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
  
 O `<schemaValidator>` elemento que configura o inspetor `SchemaValidationBehaviorExtensionElement` de mensagens é apoiado pela classe. A classe expõe duas propriedades `ValidateRequest` públicas `ValidateReply`booleanas nomeadas e . Ambos estão marcados <xref:System.Configuration.ConfigurationPropertyAttribute>com um . Este atributo constitui o link entre as propriedades do código e os atributos XML que podem ser vistos no elemento de configuração XML anterior. A classe também `Schemas` possui uma propriedade que <xref:System.Configuration.ConfigurationCollectionAttribute> é adicionalmente `SchemaCollection`marcada com o e é do tipo , que também faz parte desta amostra, mas omitida deste documento para brevidade. Esta propriedade juntamente com a `SchemaConfigElement` coleção e `<schemas>` a classe elemento de coleta apoia o elemento no trecho de configuração anterior e permite adicionar uma coleção de esquemas ao conjunto de validação.  
  
 O método `CreateBehavior` substituído transforma os dados de configuração em um objeto de comportamento quando o tempo de execução avalia os dados de configuração à medida que ele constrói um cliente ou um ponto final.  
  
```csharp
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
  
## <a name="adding-message-inspectors-imperatively"></a>Adicionando inspetores de mensagens imperativamente  
 Exceto através de atributos (que não são suportados nesta amostra pela razão citada anteriormente) e configuração, comportamentos podem ser facilmente adicionados a um cliente e tempo de execução de serviço usando código imperativo. Nesta amostra, isso é feito no aplicativo cliente para testar o inspetor de mensagens do cliente. A `GenericClient` classe é <xref:System.ServiceModel.ClientBase%601>derivada, que expõe a configuração do ponto final ao código do usuário. Antes que o cliente seja aberto implicitamente, a configuração do ponto final pode ser alterada, por exemplo, adicionando comportamentos como mostrado no código a seguir. Adicionar o comportamento no serviço é em grande parte equivalente à técnica do cliente mostrada aqui e deve ser realizada antes que o host de serviço seja aberto.  
  
```csharp  
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
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
