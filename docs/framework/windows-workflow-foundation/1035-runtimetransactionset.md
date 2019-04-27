---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924846"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="462c0-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="462c0-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="462c0-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="462c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="462c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="462c0-104">ID</span></span>|<span data-ttu-id="462c0-105">1035</span><span class="sxs-lookup"><span data-stu-id="462c0-105">1035</span></span>|  
|<span data-ttu-id="462c0-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="462c0-106">Keywords</span></span>|<span data-ttu-id="462c0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="462c0-107">WFRuntime</span></span>|  
|<span data-ttu-id="462c0-108">Nível</span><span class="sxs-lookup"><span data-stu-id="462c0-108">Level</span></span>|<span data-ttu-id="462c0-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="462c0-109">Verbose</span></span>|  
|<span data-ttu-id="462c0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="462c0-110">Channel</span></span>|<span data-ttu-id="462c0-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="462c0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="462c0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="462c0-112">Description</span></span>  
 <span data-ttu-id="462c0-113">Indica que uma atividade definiu a transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="462c0-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="462c0-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="462c0-114">Message</span></span>  
 <span data-ttu-id="462c0-115">A transação de tempo de execução foi definida pela atividade "%1", DisplayName: "%2", InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="462c0-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="462c0-116">Execução isolada a atividade "%4', DisplayName:"%5", InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="462c0-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="462c0-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="462c0-117">Details</span></span>  
  
|<span data-ttu-id="462c0-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="462c0-118">Data Item Name</span></span>|<span data-ttu-id="462c0-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="462c0-119">Data Item Type</span></span>|<span data-ttu-id="462c0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="462c0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="462c0-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="462c0-121">Activity</span></span>|<span data-ttu-id="462c0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-122">xs:string</span></span>|<span data-ttu-id="462c0-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="462c0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="462c0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="462c0-124">DisplayName</span></span>|<span data-ttu-id="462c0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-125">xs:string</span></span>|<span data-ttu-id="462c0-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="462c0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="462c0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="462c0-127">InstanceId</span></span>|<span data-ttu-id="462c0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-128">xs:string</span></span>|<span data-ttu-id="462c0-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="462c0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="462c0-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="462c0-130">IsolatedActivity</span></span>|<span data-ttu-id="462c0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-131">xs:string</span></span>|<span data-ttu-id="462c0-132">O nome do tipo de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="462c0-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="462c0-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="462c0-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="462c0-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-134">xs:string</span></span>|<span data-ttu-id="462c0-135">O nome para exibição de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="462c0-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="462c0-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="462c0-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="462c0-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-137">xs:string</span></span>|<span data-ttu-id="462c0-138">A identificação de instância de que a atividade isolada a transação está.</span><span class="sxs-lookup"><span data-stu-id="462c0-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="462c0-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="462c0-139">AppDomain</span></span>|<span data-ttu-id="462c0-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="462c0-140">xs:string</span></span>|<span data-ttu-id="462c0-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="462c0-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
