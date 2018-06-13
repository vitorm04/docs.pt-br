---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509750"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="2760d-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="2760d-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2760d-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2760d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2760d-104">ID</span><span class="sxs-lookup"><span data-stu-id="2760d-104">ID</span></span>|<span data-ttu-id="2760d-105">1021</span><span class="sxs-lookup"><span data-stu-id="2760d-105">1021</span></span>|  
|<span data-ttu-id="2760d-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="2760d-106">Keywords</span></span>|<span data-ttu-id="2760d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2760d-107">WFRuntime</span></span>|  
|<span data-ttu-id="2760d-108">Nível</span><span class="sxs-lookup"><span data-stu-id="2760d-108">Level</span></span>|<span data-ttu-id="2760d-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="2760d-109">Verbose</span></span>|  
|<span data-ttu-id="2760d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2760d-110">Channel</span></span>|<span data-ttu-id="2760d-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="2760d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2760d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2760d-112">Description</span></span>  
 <span data-ttu-id="2760d-113">Indica que um BookmarkWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="2760d-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2760d-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2760d-114">Message</span></span>  
 <span data-ttu-id="2760d-115">Um BookmarkWorkItem foi agendado para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2760d-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="2760d-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="2760d-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2760d-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2760d-117">Details</span></span>  
  
|<span data-ttu-id="2760d-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="2760d-118">Data Item Name</span></span>|<span data-ttu-id="2760d-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="2760d-119">Data Item Type</span></span>|<span data-ttu-id="2760d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2760d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2760d-121">Atividade</span><span class="sxs-lookup"><span data-stu-id="2760d-121">Activity</span></span>|<span data-ttu-id="2760d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-122">xs:string</span></span>|<span data-ttu-id="2760d-123">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="2760d-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="2760d-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2760d-124">DisplayName</span></span>|<span data-ttu-id="2760d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-125">xs:string</span></span>|<span data-ttu-id="2760d-126">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="2760d-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="2760d-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2760d-127">InstanceId</span></span>|<span data-ttu-id="2760d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-128">xs:string</span></span>|<span data-ttu-id="2760d-129">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="2760d-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2760d-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="2760d-130">BookmarkName</span></span>|<span data-ttu-id="2760d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-131">xs:string</span></span>|<span data-ttu-id="2760d-132">O nome do indicador.</span><span class="sxs-lookup"><span data-stu-id="2760d-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="2760d-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="2760d-133">BookmarkScope</span></span>|<span data-ttu-id="2760d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-134">xs:string</span></span>|<span data-ttu-id="2760d-135">O escopo do indexador.</span><span class="sxs-lookup"><span data-stu-id="2760d-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="2760d-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2760d-136">AppDomain</span></span>|<span data-ttu-id="2760d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="2760d-137">xs:string</span></span>|<span data-ttu-id="2760d-138">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2760d-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
