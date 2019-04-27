---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982248"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="c2ad6-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="c2ad6-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c2ad6-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c2ad6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2ad6-104">ID</span><span class="sxs-lookup"><span data-stu-id="c2ad6-104">ID</span></span>|<span data-ttu-id="c2ad6-105">1011</span><span class="sxs-lookup"><span data-stu-id="c2ad6-105">1011</span></span>|  
|<span data-ttu-id="c2ad6-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c2ad6-106">Keywords</span></span>|<span data-ttu-id="c2ad6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c2ad6-107">WFRuntime</span></span>|  
|<span data-ttu-id="c2ad6-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c2ad6-108">Level</span></span>|<span data-ttu-id="c2ad6-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c2ad6-109">Verbose</span></span>|  
|<span data-ttu-id="c2ad6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c2ad6-110">Channel</span></span>|<span data-ttu-id="c2ad6-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c2ad6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c2ad6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2ad6-112">Description</span></span>  
 <span data-ttu-id="c2ad6-113">Indica que um ExecuteActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="c2ad6-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c2ad6-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c2ad6-114">Message</span></span>  
 <span data-ttu-id="c2ad6-115">Um ExecuteActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="c2ad6-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c2ad6-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c2ad6-116">Details</span></span>  
  
|<span data-ttu-id="c2ad6-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c2ad6-117">Data Item Name</span></span>|<span data-ttu-id="c2ad6-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c2ad6-118">Data Item Type</span></span>|<span data-ttu-id="c2ad6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2ad6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c2ad6-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="c2ad6-120">Activity</span></span>|<span data-ttu-id="c2ad6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2ad6-121">xs:string</span></span>|<span data-ttu-id="c2ad6-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2ad6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c2ad6-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c2ad6-123">DisplayName</span></span>|<span data-ttu-id="c2ad6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2ad6-124">xs:string</span></span>|<span data-ttu-id="c2ad6-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2ad6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c2ad6-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c2ad6-126">InstanceId</span></span>|<span data-ttu-id="c2ad6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2ad6-127">xs:string</span></span>|<span data-ttu-id="c2ad6-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="c2ad6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c2ad6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c2ad6-129">AppDomain</span></span>|<span data-ttu-id="c2ad6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2ad6-130">xs:string</span></span>|<span data-ttu-id="c2ad6-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c2ad6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
