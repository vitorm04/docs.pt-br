---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924482"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="fb457-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="fb457-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fb457-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fb457-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb457-104">ID</span><span class="sxs-lookup"><span data-stu-id="fb457-104">ID</span></span>|<span data-ttu-id="fb457-105">1017</span><span class="sxs-lookup"><span data-stu-id="fb457-105">1017</span></span>|  
|<span data-ttu-id="fb457-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fb457-106">Keywords</span></span>|<span data-ttu-id="fb457-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fb457-107">WFRuntime</span></span>|  
|<span data-ttu-id="fb457-108">Nível</span><span class="sxs-lookup"><span data-stu-id="fb457-108">Level</span></span>|<span data-ttu-id="fb457-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="fb457-109">Verbose</span></span>|  
|<span data-ttu-id="fb457-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fb457-110">Channel</span></span>|<span data-ttu-id="fb457-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="fb457-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fb457-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb457-112">Description</span></span>  
 <span data-ttu-id="fb457-113">Indica que um CancelActivityWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="fb457-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fb457-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fb457-114">Message</span></span>  
 <span data-ttu-id="fb457-115">Um CancelActivityWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="fb457-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fb457-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fb457-116">Details</span></span>  
  
|<span data-ttu-id="fb457-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="fb457-117">Data Item Name</span></span>|<span data-ttu-id="fb457-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="fb457-118">Data Item Type</span></span>|<span data-ttu-id="fb457-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb457-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fb457-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="fb457-120">Activity</span></span>|<span data-ttu-id="fb457-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb457-121">xs:string</span></span>|<span data-ttu-id="fb457-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="fb457-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="fb457-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fb457-123">DisplayName</span></span>|<span data-ttu-id="fb457-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb457-124">xs:string</span></span>|<span data-ttu-id="fb457-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="fb457-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="fb457-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fb457-126">InstanceId</span></span>|<span data-ttu-id="fb457-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb457-127">xs:string</span></span>|<span data-ttu-id="fb457-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="fb457-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fb457-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fb457-129">AppDomain</span></span>|<span data-ttu-id="fb457-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb457-130">xs:string</span></span>|<span data-ttu-id="fb457-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fb457-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
