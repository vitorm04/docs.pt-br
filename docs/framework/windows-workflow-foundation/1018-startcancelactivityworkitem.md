---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f74a133a685699bcefc014269a9ecb3ebea4e505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="bea30-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="bea30-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="bea30-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bea30-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bea30-104">ID</span><span class="sxs-lookup"><span data-stu-id="bea30-104">ID</span></span>|<span data-ttu-id="bea30-105">1018</span><span class="sxs-lookup"><span data-stu-id="bea30-105">1018</span></span>|  
|<span data-ttu-id="bea30-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="bea30-106">Keywords</span></span>|<span data-ttu-id="bea30-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bea30-107">WFRuntime</span></span>|  
|<span data-ttu-id="bea30-108">Nível</span><span class="sxs-lookup"><span data-stu-id="bea30-108">Level</span></span>|<span data-ttu-id="bea30-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="bea30-109">Verbose</span></span>|  
|<span data-ttu-id="bea30-110">Canal</span><span class="sxs-lookup"><span data-stu-id="bea30-110">Channel</span></span>|<span data-ttu-id="bea30-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="bea30-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bea30-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bea30-112">Description</span></span>  
 <span data-ttu-id="bea30-113">Indica que um CancelActivityWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="bea30-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bea30-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="bea30-114">Message</span></span>  
 <span data-ttu-id="bea30-115">Iniciar a execução de um CancelActivityWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="bea30-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bea30-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bea30-116">Details</span></span>  
  
|<span data-ttu-id="bea30-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="bea30-117">Data Item Name</span></span>|<span data-ttu-id="bea30-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="bea30-118">Data Item Type</span></span>|<span data-ttu-id="bea30-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="bea30-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bea30-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="bea30-120">Activity</span></span>|<span data-ttu-id="bea30-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bea30-121">xs:string</span></span>|<span data-ttu-id="bea30-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="bea30-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bea30-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bea30-123">DisplayName</span></span>|<span data-ttu-id="bea30-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bea30-124">xs:string</span></span>|<span data-ttu-id="bea30-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="bea30-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bea30-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bea30-126">InstanceId</span></span>|<span data-ttu-id="bea30-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bea30-127">xs:string</span></span>|<span data-ttu-id="bea30-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="bea30-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bea30-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bea30-129">AppDomain</span></span>|<span data-ttu-id="bea30-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bea30-130">xs:string</span></span>|<span data-ttu-id="bea30-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bea30-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
