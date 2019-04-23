---
title: Inspetores de mensagem
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: c9d2c47a816e7fd8c5d219009128ed530564b81b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334946"
---
# <a name="message-inspectors"></a><span data-ttu-id="b0ba4-102">Inspetores de mensagem</span><span class="sxs-lookup"><span data-stu-id="b0ba4-102">Message Inspectors</span></span>
<span data-ttu-id="b0ba4-103">Este exemplo demonstra como implementar e configurar o cliente e serviço inspetores de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="b0ba4-104">Um Inspetor de mensagens é um objeto de extensibilidade que pode ser usado em tempo de execução do modelo de serviço cliente e o tempo de execução de expedição programaticamente ou por meio de configuração e que pode inspecionar e alterar mensagens depois de serem recebidas ou antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="b0ba4-105">Este exemplo implementa um cliente básico e o mecanismo de validação de mensagens de serviço que valida as mensagens de entrada em relação a um conjunto de documentos de esquema XML configuráveis.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="b0ba4-106">Observe que, neste exemplo não valida mensagens para cada operação.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="b0ba4-107">Isso é uma simplificação intencional.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="b0ba4-108">Inspetor de mensagens</span><span class="sxs-lookup"><span data-stu-id="b0ba4-108">Message Inspector</span></span>  
 <span data-ttu-id="b0ba4-109">Implemente de inspetores de mensagem do cliente do <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface e serviço implementar de inspetores de mensagem o <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="b0ba4-110">As implementações podem ser combinadas em uma única classe para formar um Inspetor de mensagens que funciona para ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="b0ba4-111">Este exemplo implementa tal um Inspetor de mensagens combinada.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="b0ba4-112">O Inspetor é construído passando um conjunto de esquemas em relação ao qual as mensagens de entrada e saídas são validadas e permite que o desenvolvedor especificar se as mensagens de entrada ou saídas são validadas e se o Inspetor está no modo de expedição ou cliente, que afeta o tratamento de erros, como discutido posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-113">Qualquer Inspetor de mensagens do serviço (dispatcher) deve implementar os dois <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> métodos <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="b0ba4-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> é invocado pelo dispatcher quando uma mensagem foi recebida, processada pela pilha de canais e atribuída a um serviço, mas antes de ser desserializado e despachada para uma operação.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="b0ba4-115">Se a mensagem de entrada foi criptografada, a mensagem já é descriptografada quando ele atinge o Inspetor de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="b0ba4-116">O método obtém o `request` mensagem passada como um parâmetro de referência, que permite que a mensagem a ser inspecionado, manipulado ou substituídos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="b0ba4-117">O valor de retorno pode ser qualquer objeto e é usado como um objeto de estado de correlação que é passado para <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> quando o serviço retornará uma resposta para a mensagem atual.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="b0ba4-118">Neste exemplo, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delega a inspeção (validação) da mensagem para o método local, privado, `ValidateMessageBody` e não retorna nenhum objeto de estado de correlação.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="b0ba4-119">Esse método garante que nenhuma mensagem inválida passa para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> é invocado sempre que uma resposta estiver pronta para ser enviada para um cliente ou, no caso de mensagens unidirecionais, quando a mensagem de entrada tiver sido processada.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="b0ba4-121">Isso permite que extensões contar que está sendo chamado simetricamente, independentemente do MEP.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="b0ba4-122">Assim como acontece com <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, a mensagem é passada como um parâmetro de referência e pode ser inspecionada, modificada ou substituída.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="b0ba4-123">Novamente, a validação da mensagem que é executada neste exemplo é delegada ao `ValidMessageBody` método, mas o tratamento de erros de validação é ligeiramente diferente nesse caso.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="b0ba4-124">Se ocorrer um erro de validação no serviço, o `ValidateMessageBody` método lança <xref:System.ServiceModel.FaultException>-derivado exceções.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="b0ba4-125">No <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, essas exceções podem ser colocadas na infra-estrutura de modelo de serviço, onde são transformados em falhas de SOAP e de retransmissão para o cliente automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="b0ba4-126">Na <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceções não devem ser colocadas à infra-estrutura, como a transformação de exceções de falha geradas pelo serviço ocorre antes do Inspetor de mensagens é chamado.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="b0ba4-127">Portanto a implementação a seguir captura conhecidos `ReplyValidationFault` exceção e substitui a resposta de mensagem com uma mensagem de falha explícita.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="b0ba4-128">Esse método garante que nenhum mensagens inválidas são retornadas pela implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-129">O Inspetor de mensagens do cliente é muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-129">The client message inspector is very similar.</span></span> <span data-ttu-id="b0ba4-130">Os dois métodos que devem ser implementados da <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> estão <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> e <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="b0ba4-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> é invocado quando a mensagem tiver sido composta pelo aplicativo cliente ou pelo formatador de operação.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="b0ba4-132">Como com os inspetores de mensagem do dispatcher, a mensagem pode apenas ser inspecionados ou totalmente substituídas.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="b0ba4-133">Neste exemplo, o Inspetor de delega para o mesmo local `ValidateMessageBody` método auxiliar que também é usado para os inspetores de mensagem de expedição.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="b0ba4-134">A diferença comportamental entre a validação de cliente e serviço (conforme especificado no construtor) é que a validação de cliente gerará exceções de locais que são colocadas no código do usuário, porque eles ocorrem localmente e não devido a uma falha de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="b0ba4-135">Em geral, a regra é que os inspetores do serviço dispatcher geram falhas e inspetores de cliente lançam exceções.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="b0ba4-136">Isso <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementação garante que nenhuma mensagem inválidas sejam enviadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-137">O `AfterReceiveReply` implementação garante que nenhuma mensagem inválida recebida do serviço é retransmitidas para o código de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="b0ba4-138">O coração do Inspetor de mensagem específica é o `ValidateMessageBody` método.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="b0ba4-139">Para realizar seu trabalho, ele encapsula uma validação <xref:System.Xml.XmlReader> em torno do corpo conteúdo subárvore da mensagem passada.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="b0ba4-140">O leitor é preenchido com o conjunto de esquemas que mantém o Inspetor de mensagens e o retorno de chamada de validação é definido como um delegado referindo-se para o `InspectionValidationHandler` que é definida juntamente com esse método.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="b0ba4-141">Para executar a validação, a mensagem é, em seguida, ler e colocados no spool em um fluxo com suporte de memória <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="b0ba4-142">Se um erro de validação ou aviso ocorrer no processo, o método de retorno de chamada é invocado.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="b0ba4-143">Se nenhum erro ocorrer, uma nova mensagem é construída que copia as propriedades e os cabeçalhos da mensagem original e usa o infoset agora validada no fluxo de memória, que é encapsulado por um <xref:System.Xml.XmlDictionaryReader> e adicionado à mensagem de substituição.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-144">O `InspectionValidationHandler` método é chamado pela validação <xref:System.Xml.XmlReader> sempre que um erro de validação de esquema ou o aviso ocorre.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="b0ba4-145">A implementação a seguir funciona apenas com erros e ignora todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="b0ba4-146">Na primeira consideração, pode parecer possível inserir uma validação <xref:System.Xml.XmlReader> na mensagem com o Inspetor de mensagens e permitem que a validação ocorrem conforme a mensagem é processada e sem buffer a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="b0ba4-147">Que, no entanto, significa que esse retorno de chamada gera as exceções de validação em algum lugar no serviço de modelo infraestrutura ou o código do usuário como nós XML inválidos são detectadas, resultando em comportamento imprevisível.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="b0ba4-148">A abordagem de armazenamento em buffer protege o código do usuário de mensagens inválidas, inteiramente.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="b0ba4-149">Conforme discutido anteriormente, as exceções geradas pelo manipulador diferem entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="b0ba4-150">No serviço, as exceções são derivadas de <xref:System.ServiceModel.FaultException>, no cliente, as exceções são exceções personalizadas regulares.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="b0ba4-151">Comportamento</span><span class="sxs-lookup"><span data-stu-id="b0ba4-151">Behavior</span></span>  
 <span data-ttu-id="b0ba4-152">Inspetores de mensagem são extensões para o tempo de execução do cliente ou o tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="b0ba4-153">Essas extensões são configuradas usando *comportamentos*.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="b0ba4-154">Um comportamento é uma classe que altera o comportamento do tempo de execução de modelo de serviço alterando a configuração padrão ou adicionando extensões (por exemplo, inspetores de mensagem) a ele.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="b0ba4-155">O seguinte `SchemaValidationBehavior` classe é o comportamento usado para adicionar o Inspetor de mensagens de trabalho deste exemplo para o cliente ou tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="b0ba4-156">A implementação é bastante básica em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="b0ba4-157">Na <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> e <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, o Inspetor de mensagens é criado e adicionado ao <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> coleção do respectivo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
>  <span data-ttu-id="b0ba4-158">Esse comportamento em particular não funcionar como um atributo e, portanto, não é possível adicionar declarativamente em um tipo de contrato de um tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="b0ba4-159">Essa é uma decisão de design feita porque a coleção de esquema não pode ser carregada em uma declaração de atributo e fazer referência a um local de configuração adicional (por exemplo, para as configurações do aplicativo) nesse atributo significa a criação de um elemento de configuração não é consistente com o restante da configuração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="b0ba4-160">Portanto, esse comportamento só pode ser adicionado imperativamente por meio de código e uma extensão de configuração de modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="b0ba4-161">Adicionando o Inspetor de mensagens por meio da configuração</span><span class="sxs-lookup"><span data-stu-id="b0ba4-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="b0ba4-162">Para configurar um comportamento personalizado em um ponto de extremidade no arquivo de configuração do aplicativo, o modelo de serviço exige que os implementadores de criar uma configuração de *elemento de extensão* representado por uma classe derivada de <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="b0ba4-163">Essa extensão, em seguida, deve ser adicionada à seção de configuração do modelo de serviço para as extensões conforme mostrado para a seguinte extensão abordada nesta seção.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-164">As extensões podem ser adicionadas no aplicativo ou arquivo de configuração do ASP.NET, que é a opção mais comum, ou no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="b0ba4-165">Quando a extensão é adicionada a um escopo de configuração, o comportamento pode ser adicionado a uma configuração de comportamento, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="b0ba4-166">As configurações de comportamento são elementos reutilizáveis que podem ser aplicados a vários pontos de extremidade conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="b0ba4-167">Porque o comportamento específico a ser configurado aqui implementa <xref:System.ServiceModel.Description.IEndpointBehavior>, só é válida na seção respectiva configuração no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b0ba4-168">O `<schemaValidator>` elemento que configura o Inspetor de mensagens é apoiado pelo `SchemaValidationBehaviorExtensionElement` classe.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="b0ba4-169">A classe expõe duas propriedades públicas Boolianas denominadas `ValidateRequest` e `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="b0ba4-170">Ambos são marcados com um <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="b0ba4-171">Esse atributo constitui o link entre as propriedades de código e os atributos XML que podem ser vistos no elemento de configuração XML anterior.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="b0ba4-172">A classe também tem uma propriedade `Schemas` Além disso, que é marcado com o <xref:System.Configuration.ConfigurationCollectionAttribute> e é do tipo `SchemaCollection`, que também faz parte deste exemplo, mas omitidos deste documento para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="b0ba4-173">Essa propriedade juntamente com a coleção e a classe de elemento da coleção `SchemaConfigElement` faz o `<schemas>` elemento no trecho de configuração anterior e permite a adição de uma coleção de esquemas para o conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="b0ba4-174">Substituído `CreateBehavior` método transforma os dados de configuração em um objeto de comportamento quando o tempo de execução avalia os dados de configuração ao criar um cliente ou um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="b0ba4-175">Adição de inspetores de mensagem imperativa</span><span class="sxs-lookup"><span data-stu-id="b0ba4-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="b0ba4-176">Exceto por meio de atributos (que não é suportado neste exemplo para o motivo citado anteriormente) e configuração, comportamentos podem facilmente ser adicionados a um tempo de execução do cliente e o serviço usando o código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="b0ba4-177">Neste exemplo, isso é feito no aplicativo cliente para testar o Inspetor de mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="b0ba4-178">O `GenericClient` classe é derivada de <xref:System.ServiceModel.ClientBase%601>, que expõe a configuração de ponto de extremidade para o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="b0ba4-179">Antes do cliente é aberto implicitamente a configuração de ponto de extremidade pode ser alterada, por exemplo, adicionando comportamentos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="b0ba4-180">Adicionar o comportamento do serviço é basicamente equivalente à técnica de cliente mostrada aqui e deve ser executado antes que o host de serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b0ba4-181">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b0ba4-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b0ba4-182">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ba4-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b0ba4-183">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ba4-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b0ba4-184">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0ba4-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0ba4-185">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0ba4-186">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0ba4-187">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0ba4-188">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b0ba4-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
