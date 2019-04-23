---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 1df4b32feda246a536183a42ac11b113bc4bb259
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768391"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="11525-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="11525-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="11525-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="11525-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11525-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11525-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="11525-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="11525-105">Methods</span></span>  
 <span data-ttu-id="11525-106">A classe MsmqBindingElementBase não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="11525-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11525-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="11525-107">Properties</span></span>  
 <span data-ttu-id="11525-108">A classe MsmqBindingElementBase tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="11525-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="11525-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="11525-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="11525-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11525-110">Data type: string</span></span>  
  
 <span data-ttu-id="11525-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-112">Um URI que contém o local da fila de mensagens mortas de cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.</span><span class="sxs-lookup"><span data-stu-id="11525-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="11525-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="11525-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="11525-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11525-114">Data type: string</span></span>  
  
 <span data-ttu-id="11525-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-116">Um valor de enumeração que indica o tipo de fila de mensagens mortas a ser usada.</span><span class="sxs-lookup"><span data-stu-id="11525-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="11525-117">duráveis</span><span class="sxs-lookup"><span data-stu-id="11525-117">Durable</span></span>  
 <span data-ttu-id="11525-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11525-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="11525-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-120">Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.</span><span class="sxs-lookup"><span data-stu-id="11525-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="11525-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="11525-121">ExactlyOnce</span></span>  
 <span data-ttu-id="11525-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11525-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="11525-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-124">Um valor booliano que indica se as mensagens processadas por essa associação são recebidas exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="11525-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="11525-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="11525-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="11525-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="11525-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="11525-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-128">O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="11525-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="11525-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="11525-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="11525-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11525-130">Data type: string</span></span>  
  
 <span data-ttu-id="11525-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-132">As configurações para manipulação de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="11525-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="11525-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="11525-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="11525-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="11525-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="11525-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-136">O número máximo de repetição imediata tentativas em uma mensagem que é lida da fila de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="11525-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="11525-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="11525-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="11525-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="11525-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="11525-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-140">Um valor que indica o tempo de espera entre ciclos ao tentar entregar uma mensagem que não pôde ser entregue imediatamente.</span><span class="sxs-lookup"><span data-stu-id="11525-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="11525-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="11525-141">TimeToLive</span></span>  
 <span data-ttu-id="11525-142">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="11525-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="11525-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-144">O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.</span><span class="sxs-lookup"><span data-stu-id="11525-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="11525-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="11525-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="11525-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11525-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="11525-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-148">Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="11525-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="11525-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="11525-149">UseSourceJournal</span></span>  
 <span data-ttu-id="11525-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="11525-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="11525-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="11525-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11525-152">Um valor booliano que indica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.</span><span class="sxs-lookup"><span data-stu-id="11525-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11525-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11525-153">Requirements</span></span>  
  
|<span data-ttu-id="11525-154">MOF</span><span class="sxs-lookup"><span data-stu-id="11525-154">MOF</span></span>|<span data-ttu-id="11525-155">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11525-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11525-156">Namespace</span><span class="sxs-lookup"><span data-stu-id="11525-156">Namespace</span></span>|<span data-ttu-id="11525-157">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11525-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11525-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11525-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
