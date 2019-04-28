---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924859"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="12e39-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="12e39-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="12e39-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="12e39-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12e39-104">ID</span><span class="sxs-lookup"><span data-stu-id="12e39-104">ID</span></span>|<span data-ttu-id="12e39-105">1032</span><span class="sxs-lookup"><span data-stu-id="12e39-105">1032</span></span>|  
|<span data-ttu-id="12e39-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="12e39-106">Keywords</span></span>|<span data-ttu-id="12e39-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="12e39-107">WFRuntime</span></span>|  
|<span data-ttu-id="12e39-108">Nível</span><span class="sxs-lookup"><span data-stu-id="12e39-108">Level</span></span>|<span data-ttu-id="12e39-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="12e39-109">Verbose</span></span>|  
|<span data-ttu-id="12e39-110">Canal</span><span class="sxs-lookup"><span data-stu-id="12e39-110">Channel</span></span>|<span data-ttu-id="12e39-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="12e39-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="12e39-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="12e39-112">Description</span></span>  
 <span data-ttu-id="12e39-113">Indica que um RuntimeWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="12e39-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="12e39-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="12e39-114">Message</span></span>  
 <span data-ttu-id="12e39-115">Um item de trabalho de tempo de execução foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="12e39-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="12e39-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="12e39-116">Details</span></span>  
  
|<span data-ttu-id="12e39-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="12e39-117">Data Item Name</span></span>|<span data-ttu-id="12e39-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="12e39-118">Data Item Type</span></span>|<span data-ttu-id="12e39-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="12e39-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="12e39-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="12e39-120">Activity</span></span>|<span data-ttu-id="12e39-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="12e39-121">xs:string</span></span>|<span data-ttu-id="12e39-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="12e39-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="12e39-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="12e39-123">DisplayName</span></span>|<span data-ttu-id="12e39-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="12e39-124">xs:string</span></span>|<span data-ttu-id="12e39-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="12e39-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="12e39-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="12e39-126">InstanceId</span></span>|<span data-ttu-id="12e39-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="12e39-127">xs:string</span></span>|<span data-ttu-id="12e39-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="12e39-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="12e39-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="12e39-129">AppDomain</span></span>|<span data-ttu-id="12e39-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="12e39-130">xs:string</span></span>|<span data-ttu-id="12e39-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="12e39-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
