---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924625"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="e92b2-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="e92b2-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e92b2-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e92b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e92b2-104">ID</span><span class="sxs-lookup"><span data-stu-id="e92b2-104">ID</span></span>|<span data-ttu-id="e92b2-105">1026</span><span class="sxs-lookup"><span data-stu-id="e92b2-105">1026</span></span>|  
|<span data-ttu-id="e92b2-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e92b2-106">Keywords</span></span>|<span data-ttu-id="e92b2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e92b2-107">WFRuntime</span></span>|  
|<span data-ttu-id="e92b2-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e92b2-108">Level</span></span>|<span data-ttu-id="e92b2-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="e92b2-109">Verbose</span></span>|  
|<span data-ttu-id="e92b2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e92b2-110">Channel</span></span>|<span data-ttu-id="e92b2-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="e92b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e92b2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e92b2-112">Description</span></span>  
 <span data-ttu-id="e92b2-113">Indica que um TransactionContextWorkItem foi agendada.</span><span class="sxs-lookup"><span data-stu-id="e92b2-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e92b2-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e92b2-114">Message</span></span>  
 <span data-ttu-id="e92b2-115">Um TransactionContextWorkItem foi agendada para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="e92b2-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e92b2-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e92b2-116">Details</span></span>  
  
|<span data-ttu-id="e92b2-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e92b2-117">Data Item Name</span></span>|<span data-ttu-id="e92b2-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e92b2-118">Data Item Type</span></span>|<span data-ttu-id="e92b2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e92b2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e92b2-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="e92b2-120">Activity</span></span>|<span data-ttu-id="e92b2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e92b2-121">xs:string</span></span>|<span data-ttu-id="e92b2-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="e92b2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e92b2-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e92b2-123">DisplayName</span></span>|<span data-ttu-id="e92b2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e92b2-124">xs:string</span></span>|<span data-ttu-id="e92b2-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="e92b2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e92b2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e92b2-126">InstanceId</span></span>|<span data-ttu-id="e92b2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e92b2-127">xs:string</span></span>|<span data-ttu-id="e92b2-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="e92b2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e92b2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e92b2-129">AppDomain</span></span>|<span data-ttu-id="e92b2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e92b2-130">xs:string</span></span>|<span data-ttu-id="e92b2-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e92b2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
