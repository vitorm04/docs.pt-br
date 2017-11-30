---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f430e7b58d5aba277b0a35a20f1f5fdb707bce9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="767a3-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="767a3-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="767a3-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="767a3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="767a3-104">ID</span><span class="sxs-lookup"><span data-stu-id="767a3-104">ID</span></span>|<span data-ttu-id="767a3-105">1013</span><span class="sxs-lookup"><span data-stu-id="767a3-105">1013</span></span>|  
|<span data-ttu-id="767a3-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="767a3-106">Keywords</span></span>|<span data-ttu-id="767a3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="767a3-107">WFRuntime</span></span>|  
|<span data-ttu-id="767a3-108">Nível</span><span class="sxs-lookup"><span data-stu-id="767a3-108">Level</span></span>|<span data-ttu-id="767a3-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="767a3-109">Verbose</span></span>|  
|<span data-ttu-id="767a3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="767a3-110">Channel</span></span>|<span data-ttu-id="767a3-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="767a3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="767a3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="767a3-112">Description</span></span>  
 <span data-ttu-id="767a3-113">Indica que um ExecuteActivityWorkItem concluiu</span><span class="sxs-lookup"><span data-stu-id="767a3-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="767a3-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="767a3-114">Message</span></span>  
 <span data-ttu-id="767a3-115">Um ExecuteActivityWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="767a3-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="767a3-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="767a3-116">Details</span></span>  
  
|<span data-ttu-id="767a3-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="767a3-117">Data Item Name</span></span>|<span data-ttu-id="767a3-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="767a3-118">Data Item Type</span></span>|<span data-ttu-id="767a3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="767a3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="767a3-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="767a3-120">Activity</span></span>|<span data-ttu-id="767a3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="767a3-121">xs:string</span></span>|<span data-ttu-id="767a3-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="767a3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="767a3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="767a3-123">DisplayName</span></span>|<span data-ttu-id="767a3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="767a3-124">xs:string</span></span>|<span data-ttu-id="767a3-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="767a3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="767a3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="767a3-126">InstanceId</span></span>|<span data-ttu-id="767a3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="767a3-127">xs:string</span></span>|<span data-ttu-id="767a3-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="767a3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="767a3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="767a3-129">AppDomain</span></span>|<span data-ttu-id="767a3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="767a3-130">xs:string</span></span>|<span data-ttu-id="767a3-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="767a3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
