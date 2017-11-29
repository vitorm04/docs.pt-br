---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc60af91088fd61910dc0301b93844f4771177af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="aed62-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="aed62-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="aed62-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aed62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aed62-104">ID</span><span class="sxs-lookup"><span data-stu-id="aed62-104">ID</span></span>|<span data-ttu-id="aed62-105">1012</span><span class="sxs-lookup"><span data-stu-id="aed62-105">1012</span></span>|  
|<span data-ttu-id="aed62-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="aed62-106">Keywords</span></span>|<span data-ttu-id="aed62-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aed62-107">WFRuntime</span></span>|  
|<span data-ttu-id="aed62-108">Nível</span><span class="sxs-lookup"><span data-stu-id="aed62-108">Level</span></span>|<span data-ttu-id="aed62-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="aed62-109">Verbose</span></span>|  
|<span data-ttu-id="aed62-110">Canal</span><span class="sxs-lookup"><span data-stu-id="aed62-110">Channel</span></span>|<span data-ttu-id="aed62-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="aed62-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aed62-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="aed62-112">Description</span></span>  
 <span data-ttu-id="aed62-113">Indica que um ExecuteActivityWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="aed62-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aed62-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="aed62-114">Message</span></span>  
 <span data-ttu-id="aed62-115">Iniciar a execução de um ExecuteActivityWorkItem para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="aed62-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aed62-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="aed62-116">Details</span></span>  
  
|<span data-ttu-id="aed62-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="aed62-117">Data Item Name</span></span>|<span data-ttu-id="aed62-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="aed62-118">Data Item Type</span></span>|<span data-ttu-id="aed62-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="aed62-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aed62-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="aed62-120">Activity</span></span>|<span data-ttu-id="aed62-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="aed62-121">xs:string</span></span>|<span data-ttu-id="aed62-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="aed62-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="aed62-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="aed62-123">DisplayName</span></span>|<span data-ttu-id="aed62-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="aed62-124">xs:string</span></span>|<span data-ttu-id="aed62-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="aed62-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="aed62-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="aed62-126">InstanceId</span></span>|<span data-ttu-id="aed62-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="aed62-127">xs:string</span></span>|<span data-ttu-id="aed62-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="aed62-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aed62-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aed62-129">AppDomain</span></span>|<span data-ttu-id="aed62-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="aed62-130">xs:string</span></span>|<span data-ttu-id="aed62-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aed62-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
