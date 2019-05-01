---
title: Configurando rastreamento de fluxo de mensagem
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999512"
---
# <a name="configuring-message-flow-tracing"></a><span data-ttu-id="ed228-102">Configurando rastreamento de fluxo de mensagem</span><span class="sxs-lookup"><span data-stu-id="ed228-102">Configuring Message Flow Tracing</span></span>
<span data-ttu-id="ed228-103">Quando o rastreamento de atividades do Windows Communication Foundation (WCF) é habilitado, as IDs de atividade de ponta a ponta são atribuídas a lógicas atividades em toda a pilha do WCF.</span><span class="sxs-lookup"><span data-stu-id="ed228-103">When Windows Communication Foundation (WCF) activity tracing is enabled, End-To-End Activity IDs are assigned to logical activities throughout the WCF stack.</span></span> <span data-ttu-id="ed228-104">No [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], agora há uma versão posterior do desempenho desse recurso que funciona com o ETW rastreamento de eventos para Windows () chamado de rastreamento de fluxo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ed228-104">In [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], there is now a higher performance version of this feature that works with Event Tracing for Windows (ETW) called message flow tracing.</span></span> <span data-ttu-id="ed228-105">Quando habilitado, IDs de atividade de ponta a ponta são tiradas (ou atribuídas a, se estiver vazia) mensagens de entrada e são propagadas para todos os eventos de rastreamento que são emitidos depois que a mensagem tiver sido decodificada pelo canal.</span><span class="sxs-lookup"><span data-stu-id="ed228-105">When enabled, End-To-End activity IDs are taken from (or assigned to if empty) incoming messages and are propagated to all tracing events that are emitted after the message has been decoded by the channel.</span></span> <span data-ttu-id="ed228-106">Os clientes podem usar esse recurso para reconstruir os fluxos de mensagens com os logs de rastreamento de serviços diferentes após a decodificação.</span><span class="sxs-lookup"><span data-stu-id="ed228-106">Customers can use this feature to reconstruct message flows with trace logs from different services after decoding.</span></span>  
  
 <span data-ttu-id="ed228-107">O rastreamento pode ser habilitado depois que for detectado um problema com o aplicativo e, em seguida, desabilitado depois que o problema seja resolvido.</span><span class="sxs-lookup"><span data-stu-id="ed228-107">Tracing can be enabled after a problem is detected with the application and then disabled once the problem is resolved.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="ed228-108">A habilitação do rastreamento</span><span class="sxs-lookup"><span data-stu-id="ed228-108">Enabling Tracing</span></span>  
 <span data-ttu-id="ed228-109">Você pode habilitar o rastreamento de fluxo de mensagens, definindo o .NET Framework 4 `messageFlowTracing` elemento de configuração para `true`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ed228-109">You can enable message flow tracing by setting the .NET Framework 4 `messageFlowTracing` configuration element to `true`, as shown in the following example.</span></span>  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="ed228-110">Porque o `endToEndTracing` elemento de configuração reside em um arquivo Web. config, não pode ser configurado dinamicamente da mesma maneira como o ETW.</span><span class="sxs-lookup"><span data-stu-id="ed228-110">Because the `endToEndTracing` configuration element resides in a Web.config file, it cannot be dynamically configured in the same way as ETW.</span></span> <span data-ttu-id="ed228-111">Para o `endToEndTracing` elemento de configuração entrem em vigor, o aplicativo deve ser reciclado.</span><span class="sxs-lookup"><span data-stu-id="ed228-111">For the `endToEndTracing` configuration element to take effect, the application must be recycled.</span></span>  
  
 <span data-ttu-id="ed228-112">As atividades estão correlacionadas por intercâmbio de um identificador chamado de ID de atividade.</span><span class="sxs-lookup"><span data-stu-id="ed228-112">Activities are correlated by the interchange of an identifier called the activity ID.</span></span> <span data-ttu-id="ed228-113">Esse identificador é um GUID e é gerado pela classe System.Diagnostics.CorrelationManager.</span><span class="sxs-lookup"><span data-stu-id="ed228-113">This identifier is a GUID, and is generated by the System.Diagnostics.CorrelationManager class.</span></span> <span data-ttu-id="ed228-114">Se você manipular System.Diagnostics.Trace.CorrelationManager.ActivityID, certifique-se de que o valor é definido para original quando transfere o controle de execução para código do WCF.</span><span class="sxs-lookup"><span data-stu-id="ed228-114">If you manipulate System.Diagnostics.Trace.CorrelationManager.ActivityID, ensure that the value is set to original when execution control transfers back to WCF code.</span></span>  <span data-ttu-id="ed228-115">Além disso, se você usar um modelo de programação assíncrona do WCF Certifique-se de que System.Diagnostics.Trace.CorrelationManager.ActivityID é transferida entre os threads.</span><span class="sxs-lookup"><span data-stu-id="ed228-115">Also, if you use an asynchronous WCF programming model ensure that System.Diagnostics.Trace.CorrelationManager.ActivityID is transferred between the threads.</span></span>  
  
## <a name="message-flow-tracing-and-rest-services"></a><span data-ttu-id="ed228-116">Rastreamento de fluxo de mensagens e serviços REST</span><span class="sxs-lookup"><span data-stu-id="ed228-116">Message Flow Tracing and REST Services</span></span>  
 <span data-ttu-id="ed228-117">Rastreamento de fluxo de mensagem permite que você rastrear uma solicitação de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="ed228-117">Message flow tracing allows you to trace a request end to end.</span></span>  <span data-ttu-id="ed228-118">Com serviços baseados em SOAP, uma ID de atividade é enviada em um cabeçalho de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="ed228-118">With SOAP-based services an Activity ID is sent in a SOAP message header.</span></span> <span data-ttu-id="ed228-119">Solicitações REST não contêm esse cabeçalho para que um cabeçalho especial de evento HTTP é usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ed228-119">REST requests do not contain this header so a special HTTP event header is used instead.</span></span> <span data-ttu-id="ed228-120">O trecho de código a seguir mostra como você pode recuperar programaticamente o valor da ID de atividade:</span><span class="sxs-lookup"><span data-stu-id="ed228-120">The following code snippet shows how you can programmatically retrieve the Activity ID value:</span></span>  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 <span data-ttu-id="ed228-121">Você pode adicionar programaticamente o cabeçalho usando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed228-121">You can programmatically add the header using the following code:</span></span>  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
