---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: a0e2ac250da3837b41134d3a04a21579a2fe923a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569031"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="e0821-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="e0821-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="e0821-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="e0821-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0821-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0821-104">Syntax</span></span>  
  
```csharp  
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
  
## <a name="methods"></a><span data-ttu-id="e0821-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e0821-105">Methods</span></span>  
 <span data-ttu-id="e0821-106">A classe MsmqBindingElementBase não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e0821-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0821-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e0821-107">Properties</span></span>  
 <span data-ttu-id="e0821-108">A classe MsmqBindingElementBase tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e0821-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="e0821-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="e0821-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="e0821-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e0821-110">Data type: string</span></span>  
  
 <span data-ttu-id="e0821-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-112">Um URI que contém o local da fila de mensagens mortas de cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.</span><span class="sxs-lookup"><span data-stu-id="e0821-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="e0821-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="e0821-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="e0821-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e0821-114">Data type: string</span></span>  
  
 <span data-ttu-id="e0821-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-116">Um valor de enumeração que indica o tipo de fila de mensagens mortas a ser usada.</span><span class="sxs-lookup"><span data-stu-id="e0821-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="e0821-117">duráveis</span><span class="sxs-lookup"><span data-stu-id="e0821-117">Durable</span></span>  
 <span data-ttu-id="e0821-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e0821-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0821-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-120">Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.</span><span class="sxs-lookup"><span data-stu-id="e0821-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="e0821-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="e0821-121">ExactlyOnce</span></span>  
 <span data-ttu-id="e0821-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e0821-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0821-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-124">Um valor booliano que indica se as mensagens processadas por essa associação são recebidas exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="e0821-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="e0821-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="e0821-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="e0821-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e0821-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="e0821-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-128">O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="e0821-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="e0821-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="e0821-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="e0821-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e0821-130">Data type: string</span></span>  
  
 <span data-ttu-id="e0821-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-132">As configurações para manipulação de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="e0821-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="e0821-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="e0821-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="e0821-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e0821-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e0821-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-136">O número máximo de repetição imediata tentativas em uma mensagem que é lida da fila de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e0821-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="e0821-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="e0821-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="e0821-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e0821-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="e0821-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-140">Um valor que indica o tempo de espera entre ciclos ao tentar entregar uma mensagem que não pôde ser entregue imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e0821-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="e0821-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="e0821-141">TimeToLive</span></span>  
 <span data-ttu-id="e0821-142">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="e0821-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="e0821-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-144">O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.</span><span class="sxs-lookup"><span data-stu-id="e0821-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="e0821-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="e0821-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="e0821-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e0821-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0821-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-148">Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="e0821-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="e0821-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="e0821-149">UseSourceJournal</span></span>  
 <span data-ttu-id="e0821-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e0821-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0821-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e0821-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0821-152">Um valor booliano que indica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.</span><span class="sxs-lookup"><span data-stu-id="e0821-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0821-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0821-153">Requirements</span></span>  
  
|<span data-ttu-id="e0821-154">MOF</span><span class="sxs-lookup"><span data-stu-id="e0821-154">MOF</span></span>|<span data-ttu-id="e0821-155">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e0821-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e0821-156">Namespace</span><span class="sxs-lookup"><span data-stu-id="e0821-156">Namespace</span></span>|<span data-ttu-id="e0821-157">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e0821-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0821-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0821-158">See also</span></span>
- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
