---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: e7f4cf41168bd1e5483524195e20541d896a6569
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49370907"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="1f995-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="1f995-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="1f995-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="1f995-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f995-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f995-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1f995-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1f995-105">Methods</span></span>  
 <span data-ttu-id="1f995-106">A classe MsmqBindingElementBase não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="1f995-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f995-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1f995-107">Properties</span></span>  
 <span data-ttu-id="1f995-108">A classe MsmqBindingElementBase tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1f995-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="1f995-109">customDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="1f995-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="1f995-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1f995-110">Data type: string</span></span>  
  
 <span data-ttu-id="1f995-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-112">Um URI que contém o local da fila de mensagens mortas de cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.</span><span class="sxs-lookup"><span data-stu-id="1f995-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="1f995-113">deadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="1f995-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="1f995-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1f995-114">Data type: string</span></span>  
  
 <span data-ttu-id="1f995-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-116">Um valor de enumeração que indica o tipo de fila de mensagens mortas a ser usada.</span><span class="sxs-lookup"><span data-stu-id="1f995-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="1f995-117">duráveis</span><span class="sxs-lookup"><span data-stu-id="1f995-117">Durable</span></span>  
 <span data-ttu-id="1f995-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1f995-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f995-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-120">Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.</span><span class="sxs-lookup"><span data-stu-id="1f995-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="1f995-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="1f995-121">ExactlyOnce</span></span>  
 <span data-ttu-id="1f995-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1f995-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f995-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-124">Um valor booliano que indica se as mensagens processadas por essa associação são recebidas exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="1f995-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="1f995-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="1f995-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="1f995-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1f995-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="1f995-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-128">O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="1f995-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="1f995-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="1f995-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="1f995-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1f995-130">Data type: string</span></span>  
  
 <span data-ttu-id="1f995-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-132">As configurações para manipulação de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="1f995-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="1f995-133">receiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="1f995-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="1f995-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1f995-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="1f995-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-136">O número máximo de repetição imediata tentativas em uma mensagem que é lida da fila de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1f995-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="1f995-137">retryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="1f995-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="1f995-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="1f995-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="1f995-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-140">Um valor que indica o tempo de espera entre ciclos ao tentar entregar uma mensagem que não pôde ser entregue imediatamente.</span><span class="sxs-lookup"><span data-stu-id="1f995-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="1f995-141">timeToLive</span><span class="sxs-lookup"><span data-stu-id="1f995-141">TimeToLive</span></span>  
 <span data-ttu-id="1f995-142">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="1f995-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="1f995-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-144">O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.</span><span class="sxs-lookup"><span data-stu-id="1f995-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="1f995-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="1f995-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="1f995-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1f995-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f995-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-148">Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="1f995-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="1f995-149">useSourceJournal</span><span class="sxs-lookup"><span data-stu-id="1f995-149">UseSourceJournal</span></span>  
 <span data-ttu-id="1f995-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1f995-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f995-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1f995-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f995-152">Um valor booliano que indica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.</span><span class="sxs-lookup"><span data-stu-id="1f995-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f995-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f995-153">Requirements</span></span>  
  
|<span data-ttu-id="1f995-154">MOF</span><span class="sxs-lookup"><span data-stu-id="1f995-154">MOF</span></span>|<span data-ttu-id="1f995-155">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1f995-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f995-156">Namespace</span><span class="sxs-lookup"><span data-stu-id="1f995-156">Namespace</span></span>|<span data-ttu-id="1f995-157">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f995-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f995-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f995-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
