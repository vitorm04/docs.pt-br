---
title: Inspetores de mensagem
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: e7846b8710fa52a5b13de245b8b7147e217533db
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039396"
---
# <a name="message-inspectors"></a><span data-ttu-id="e2106-102">Inspetores de mensagem</span><span class="sxs-lookup"><span data-stu-id="e2106-102">Message Inspectors</span></span>
<span data-ttu-id="e2106-103">Este exemplo demonstra como implementar e configurar os inspetores de mensagem de cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="e2106-104">Um inspetor de mensagem é um objeto de extensibilidade que pode ser usado no tempo de execução do cliente do modelo de serviço e no tempo de execução de expedição programaticamente ou por meio da configuração e que pode inspecionar e alterar as mensagens depois que elas são recebidas ou antes de serem enviadas.</span><span class="sxs-lookup"><span data-stu-id="e2106-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="e2106-105">Este exemplo implementa um cliente básico e um mecanismo de validação de mensagens de serviço que valida as mensagens de entrada em um conjunto de documentos de esquema XML configuráveis.</span><span class="sxs-lookup"><span data-stu-id="e2106-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="e2106-106">Observe que esse exemplo não valida mensagens para cada operação.</span><span class="sxs-lookup"><span data-stu-id="e2106-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="e2106-107">Essa é uma simplificação intencional.</span><span class="sxs-lookup"><span data-stu-id="e2106-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="e2106-108">Inspetor de mensagem</span><span class="sxs-lookup"><span data-stu-id="e2106-108">Message Inspector</span></span>  
 <span data-ttu-id="e2106-109">Os inspetores de mensagem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> do cliente implementam a interface e <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> os inspetores de mensagem de serviço implementam a interface</span><span class="sxs-lookup"><span data-stu-id="e2106-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="e2106-110">As implementações podem ser combinadas em uma única classe para formar um inspetor de mensagem que funciona para ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="e2106-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="e2106-111">Este exemplo implementa um inspetor de mensagem combinado.</span><span class="sxs-lookup"><span data-stu-id="e2106-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="e2106-112">O Inspetor é construído passando um conjunto de esquemas no qual as mensagens de entrada e saída são validadas e permite que o desenvolvedor especifique se as mensagens de entrada ou saída são validadas e se o inspetor está no modo de expedição ou cliente, que afeta o tratamento de erros conforme discutido posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e2106-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="e2106-113">Qualquer Inspetor de mensagem de serviço (Dispatcher) deve implementar <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> os <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> dois <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>métodos e.</span><span class="sxs-lookup"><span data-stu-id="e2106-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="e2106-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>é invocado pelo Dispatcher quando uma mensagem é recebida, processada pela pilha de canais e atribuída a um serviço, mas antes de ser desserializada e expedida para uma operação.</span><span class="sxs-lookup"><span data-stu-id="e2106-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="e2106-115">Se a mensagem de entrada tiver sido criptografada, a mensagem já estará descriptografada quando atingir o Inspetor de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e2106-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="e2106-116">O método obtém a `request` mensagem passada como um parâmetro de referência, que permite que a mensagem seja inspecionada, manipulada ou substituída conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e2106-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="e2106-117">O valor de retorno pode ser qualquer objeto e é usado como um objeto de estado de correlação que <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> é passado para quando o serviço retorna uma resposta à mensagem atual.</span><span class="sxs-lookup"><span data-stu-id="e2106-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="e2106-118">Neste exemplo, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delega a inspeção (validação) da mensagem para o método `ValidateMessageBody` privado e local e não retorna nenhum objeto de estado de correlação.</span><span class="sxs-lookup"><span data-stu-id="e2106-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="e2106-119">Esse método garante que nenhuma mensagem inválida passe para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="e2106-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>é invocado sempre que uma resposta estiver pronta para ser enviada de volta a um cliente ou no caso de mensagens unidirecionais, quando a mensagem de entrada tiver sido processada.</span><span class="sxs-lookup"><span data-stu-id="e2106-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="e2106-121">Isso permite que as extensões sejam chamadas de forma simétrica, independentemente de MEP.</span><span class="sxs-lookup"><span data-stu-id="e2106-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="e2106-122">Assim como <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>acontece com, a mensagem é passada como um parâmetro de referência e pode ser inspecionada, modificada ou substituída.</span><span class="sxs-lookup"><span data-stu-id="e2106-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="e2106-123">A validação da mensagem executada neste exemplo é delegada novamente para o `ValidMessageBody` método, mas o tratamento de erros de validação é um pouco diferente nesse caso.</span><span class="sxs-lookup"><span data-stu-id="e2106-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="e2106-124">Se ocorrer um erro de validação no serviço, o `ValidateMessageBody` método lançará <xref:System.ServiceModel.FaultException>as exceções derivadas.</span><span class="sxs-lookup"><span data-stu-id="e2106-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="e2106-125">No <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, essas exceções podem ser colocadas na infraestrutura do modelo de serviço, onde são transformadas automaticamente em falhas de SOAP e retransmitidas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e2106-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="e2106-126">No <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> ,<xref:System.ServiceModel.FaultException> as exceções não devem ser colocadas na infraestrutura, pois a transformação de exceções de falha geradas pelo serviço ocorre antes que o Inspetor de mensagem seja chamado.</span><span class="sxs-lookup"><span data-stu-id="e2106-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="e2106-127">Portanto, a implementação a seguir captura a `ReplyValidationFault` exceção conhecida e substitui a mensagem de resposta por uma mensagem de falha explícita.</span><span class="sxs-lookup"><span data-stu-id="e2106-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="e2106-128">Esse método garante que nenhuma mensagem inválida seja retornada pela implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="e2106-129">O Inspetor de mensagem do cliente é muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="e2106-129">The client message inspector is very similar.</span></span> <span data-ttu-id="e2106-130">Os dois métodos que devem ser implementados <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> do <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> são <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>e.</span><span class="sxs-lookup"><span data-stu-id="e2106-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="e2106-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>é invocado quando a mensagem é composta pelo aplicativo cliente ou pelo formatador de operação.</span><span class="sxs-lookup"><span data-stu-id="e2106-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="e2106-132">Assim como os inspetores de mensagem do Dispatcher, a mensagem pode ser apenas inspecionada ou totalmente substituída.</span><span class="sxs-lookup"><span data-stu-id="e2106-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="e2106-133">Neste exemplo, o Inspetor delega para o mesmo método auxiliar `ValidateMessageBody` local que também é usado para os inspetores de mensagem de expedição.</span><span class="sxs-lookup"><span data-stu-id="e2106-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="e2106-134">A diferença comportamental entre a validação do cliente e do serviço (conforme especificado no Construtor) é que a validação do cliente gera exceções locais que são colocadas no código do usuário porque elas ocorrem localmente e não devido a uma falha de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="e2106-135">Em geral, a regra é que os inspetores de distribuidor de serviço lançam falhas e os inspetores de cliente geram exceções.</span><span class="sxs-lookup"><span data-stu-id="e2106-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="e2106-136">Essa <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementação garante que nenhuma mensagem inválida seja enviada ao serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="e2106-137">A `AfterReceiveReply` implementação garante que nenhuma mensagem inválida recebida do serviço seja retransmitida para o código de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="e2106-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="e2106-138">O coração desse Inspetor de mensagem específico é o `ValidateMessageBody` método.</span><span class="sxs-lookup"><span data-stu-id="e2106-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="e2106-139">Para executar seu trabalho, ele encapsula uma validação <xref:System.Xml.XmlReader> em volta da subárvore de conteúdo do corpo da mensagem passada.</span><span class="sxs-lookup"><span data-stu-id="e2106-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="e2106-140">O leitor é populado com o conjunto de esquemas que o Inspetor de mensagem contém e o retorno de chamada de validação é definido como um `InspectionValidationHandler` delegado referente ao que é definido junto com esse método.</span><span class="sxs-lookup"><span data-stu-id="e2106-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="e2106-141">Para executar a validação, a mensagem é então lida e colocada em spool em um fluxo de memória com <xref:System.Xml.XmlDictionaryWriter>suporte.</span><span class="sxs-lookup"><span data-stu-id="e2106-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="e2106-142">Se ocorrer um erro ou aviso de validação no processo, o método de retorno de chamada será invocado.</span><span class="sxs-lookup"><span data-stu-id="e2106-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="e2106-143">Se nenhum erro ocorrer, uma nova mensagem será construída que copiará as propriedades e os cabeçalhos da mensagem original e usará o infoset validado agora no fluxo de memória, que é encapsulado por um <xref:System.Xml.XmlDictionaryReader> e adicionado à mensagem de substituição.</span><span class="sxs-lookup"><span data-stu-id="e2106-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="e2106-144">O `InspectionValidationHandler` método é chamado pela validação <xref:System.Xml.XmlReader> sempre que ocorre um erro ou aviso de validação de esquema.</span><span class="sxs-lookup"><span data-stu-id="e2106-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="e2106-145">A implementação a seguir funciona apenas com erros e ignora todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="e2106-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="e2106-146">Na primeira consideração, pode parecer possível injetar uma validação <xref:System.Xml.XmlReader> na mensagem com o Inspetor de mensagem e permitir que a validação aconteça enquanto a mensagem é processada e sem armazenar a mensagem em buffer.</span><span class="sxs-lookup"><span data-stu-id="e2106-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="e2106-147">No entanto, isso significa que esse retorno de chamada gera as exceções de validação em algum lugar na infraestrutura do modelo de serviço ou o código do usuário como nós XML inválidos são detectados, resultando em um comportamento imprevisível.</span><span class="sxs-lookup"><span data-stu-id="e2106-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="e2106-148">A abordagem de buffer protege o código do usuário de mensagens inválidas, inteiramente.</span><span class="sxs-lookup"><span data-stu-id="e2106-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="e2106-149">Conforme discutido anteriormente, as exceções geradas pelo manipulador diferem entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="e2106-150">No serviço, as exceções são derivadas de <xref:System.ServiceModel.FaultException>, no cliente, as exceções são exceções personalizadas regulares.</span><span class="sxs-lookup"><span data-stu-id="e2106-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="e2106-151">Comportamento</span><span class="sxs-lookup"><span data-stu-id="e2106-151">Behavior</span></span>  
 <span data-ttu-id="e2106-152">Os inspetores de mensagem são extensões para o tempo de execução do cliente ou de expedição.</span><span class="sxs-lookup"><span data-stu-id="e2106-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="e2106-153">Essas extensões são configuradas usando *comportamentos*.</span><span class="sxs-lookup"><span data-stu-id="e2106-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="e2106-154">Um comportamento é uma classe que altera o comportamento do tempo de execução do modelo de serviço, alterando a configuração padrão ou adicionando extensões (como inspetores de mensagem) a ela.</span><span class="sxs-lookup"><span data-stu-id="e2106-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="e2106-155">A classe `SchemaValidationBehavior` a seguir é o comportamento usado para adicionar o Inspetor de mensagem do exemplo ao cliente ou ao tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="e2106-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="e2106-156">A implementação é, em ambos os casos, básica.</span><span class="sxs-lookup"><span data-stu-id="e2106-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="e2106-157">No <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> e <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>no, o Inspetor de mensagem é <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> criado e adicionado à coleção do respectivo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e2106-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="e2106-158">Esse comportamento específico não dobra como um atributo e, portanto, não pode ser adicionado declarativamente a um tipo de contrato de um tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="e2106-159">Essa é uma decisão por design feita porque a coleção de esquema não pode ser carregada em uma declaração de atributo e se referir a um local de configuração extra (por exemplo, às configurações do aplicativo) neste atributo significa criar um elemento de configuração que Não é consistente com o restante da configuração do modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="e2106-160">Portanto, esse comportamento só pode ser adicionado imperativamente por meio de código e por meio de uma extensão de configuração de modelo de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="e2106-161">Adicionando o Inspetor de mensagem por meio da configuração</span><span class="sxs-lookup"><span data-stu-id="e2106-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="e2106-162">Para configurar um comportamento personalizado em um ponto de extremidade no arquivo de configuração do aplicativo, o modelo de serviço requer implementadores para criar um *elemento de extensão* de configuração <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>representado por uma classe derivada de.</span><span class="sxs-lookup"><span data-stu-id="e2106-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="e2106-163">Essa extensão deve ser adicionada à seção de configuração do modelo de serviço para extensões, conforme mostrado para a seguinte extensão discutida nesta seção.</span><span class="sxs-lookup"><span data-stu-id="e2106-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="e2106-164">As extensões podem ser adicionadas no arquivo de configuração Application ou ASP.NET, que é a opção mais comum ou no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="e2106-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="e2106-165">Quando a extensão é adicionada a um escopo de configuração, o comportamento pode ser adicionado a uma configuração de comportamento, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2106-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="e2106-166">As configurações de comportamento são elementos reutilizáveis que podem ser aplicados a vários pontos de extremidade, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e2106-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="e2106-167">Como o comportamento específico a ser configurado aqui implementa <xref:System.ServiceModel.Description.IEndpointBehavior>, ele só é válido na seção de configuração respectiva no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2106-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="e2106-168">O `<schemaValidator>` elemento que configura o Inspetor de mensagem é apoiado `SchemaValidationBehaviorExtensionElement` pela classe.</span><span class="sxs-lookup"><span data-stu-id="e2106-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="e2106-169">A classe expõe duas propriedades públicas booleanas chamadas `ValidateRequest` e `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="e2106-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="e2106-170">Ambos são marcados com um <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e2106-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="e2106-171">Esse atributo constitui o link entre as propriedades de código e os atributos XML que podem ser vistos no elemento de configuração XML anterior.</span><span class="sxs-lookup"><span data-stu-id="e2106-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="e2106-172">A classe também tem uma propriedade `Schemas` marcada com o <xref:System.Configuration.ConfigurationCollectionAttribute> e é do tipo `SchemaCollection`, que também faz parte desse exemplo, mas que é omitido deste documento para fins de brevidade.</span><span class="sxs-lookup"><span data-stu-id="e2106-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="e2106-173">Essa propriedade junto com a coleção e a classe `SchemaConfigElement` de elemento de coleção faz backup do `<schemas>` elemento no trecho de configuração anterior e permite adicionar uma coleção de esquemas ao conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="e2106-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="e2106-174">O método `CreateBehavior` substituído transforma os dados de configuração em um objeto de comportamento quando o tempo de execução avalia os dados de configuração à medida que cria um cliente ou um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e2106-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="e2106-175">Adição imperativa de inspetores de mensagem</span><span class="sxs-lookup"><span data-stu-id="e2106-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="e2106-176">Exceto por meio de atributos (que não tem suporte neste exemplo para o motivo citado anteriormente) e configuração, os comportamentos podem ser facilmente adicionados a um tempo de execução de cliente e serviço usando código imperativo.</span><span class="sxs-lookup"><span data-stu-id="e2106-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="e2106-177">Neste exemplo, isso é feito no aplicativo cliente para testar o Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="e2106-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="e2106-178">A `GenericClient` classe é derivada de <xref:System.ServiceModel.ClientBase%601>, que expõe a configuração do ponto de extremidade ao código do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2106-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="e2106-179">Antes que o cliente seja aberto implicitamente, a configuração do ponto de extremidade pode ser alterada, por exemplo, adicionando comportamentos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2106-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="e2106-180">A adição do comportamento no serviço é amplamente equivalente à técnica do cliente mostrada aqui e deve ser executada antes da abertura do host de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2106-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2106-181">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e2106-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e2106-182">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2106-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e2106-183">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2106-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e2106-184">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2106-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2106-185">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e2106-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2106-186">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e2106-186">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e2106-187">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="e2106-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2106-188">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e2106-188">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
