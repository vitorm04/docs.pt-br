---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 9a9d48cc49b19f737236939c83a4e9421013f48f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486595"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="ebb69-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="ebb69-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="ebb69-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="ebb69-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebb69-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ebb69-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ebb69-105">Methods</span></span>  
 <span data-ttu-id="ebb69-106">A classe MsmqBindingElementBase não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="ebb69-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ebb69-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ebb69-107">Properties</span></span>  
 <span data-ttu-id="ebb69-108">A classe MsmqBindingElementBase tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ebb69-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="ebb69-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="ebb69-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="ebb69-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ebb69-110">Data type: string</span></span>  
  
 <span data-ttu-id="ebb69-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-112">Um URI que contém o local da fila de mensagens mortas para cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.</span><span class="sxs-lookup"><span data-stu-id="ebb69-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="ebb69-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="ebb69-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="ebb69-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ebb69-114">Data type: string</span></span>  
  
 <span data-ttu-id="ebb69-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-116">Um valor de enumeração que indica o tipo de fila de mensagens mortas a usar.</span><span class="sxs-lookup"><span data-stu-id="ebb69-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="ebb69-117">duráveis</span><span class="sxs-lookup"><span data-stu-id="ebb69-117">Durable</span></span>  
 <span data-ttu-id="ebb69-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ebb69-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebb69-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-120">Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.</span><span class="sxs-lookup"><span data-stu-id="ebb69-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="ebb69-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="ebb69-121">ExactlyOnce</span></span>  
 <span data-ttu-id="ebb69-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ebb69-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebb69-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-124">Um valor booliano que indica se as mensagens processadas por essa associação serão recebidas exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="ebb69-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="ebb69-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="ebb69-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="ebb69-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ebb69-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="ebb69-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-128">O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo receptor.</span><span class="sxs-lookup"><span data-stu-id="ebb69-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="ebb69-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="ebb69-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="ebb69-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ebb69-130">Data type: string</span></span>  
  
 <span data-ttu-id="ebb69-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-132">As configurações para manipulação de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="ebb69-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="ebb69-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="ebb69-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="ebb69-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ebb69-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="ebb69-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-136">O número máximo de repetição imediatas tentativas em uma mensagem que é lida da fila de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ebb69-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="ebb69-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="ebb69-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="ebb69-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="ebb69-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="ebb69-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-140">Um valor que indica o tempo de espera entre os ciclos de tentativa de entregar uma mensagem que não pôde ser entregue imediatamente.</span><span class="sxs-lookup"><span data-stu-id="ebb69-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="ebb69-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="ebb69-141">TimeToLive</span></span>  
 <span data-ttu-id="ebb69-142">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="ebb69-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="ebb69-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-144">O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.</span><span class="sxs-lookup"><span data-stu-id="ebb69-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="ebb69-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="ebb69-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="ebb69-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ebb69-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebb69-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-148">Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="ebb69-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="ebb69-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="ebb69-149">UseSourceJournal</span></span>  
 <span data-ttu-id="ebb69-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ebb69-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="ebb69-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ebb69-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ebb69-152">Um valor booliano que indica se cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.</span><span class="sxs-lookup"><span data-stu-id="ebb69-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb69-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebb69-153">Requirements</span></span>  
  
|<span data-ttu-id="ebb69-154">MOF</span><span class="sxs-lookup"><span data-stu-id="ebb69-154">MOF</span></span>|<span data-ttu-id="ebb69-155">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ebb69-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ebb69-156">Namespace</span><span class="sxs-lookup"><span data-stu-id="ebb69-156">Namespace</span></span>|<span data-ttu-id="ebb69-157">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ebb69-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebb69-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebb69-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
