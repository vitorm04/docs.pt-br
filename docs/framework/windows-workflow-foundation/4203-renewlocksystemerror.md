---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="80cfb-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="80cfb-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="80cfb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="80cfb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80cfb-104">ID</span><span class="sxs-lookup"><span data-stu-id="80cfb-104">ID</span></span>|<span data-ttu-id="80cfb-105">4203</span><span class="sxs-lookup"><span data-stu-id="80cfb-105">4203</span></span>|  
|<span data-ttu-id="80cfb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="80cfb-106">Keywords</span></span>|<span data-ttu-id="80cfb-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="80cfb-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="80cfb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="80cfb-108">Level</span></span>|<span data-ttu-id="80cfb-109">Erro</span><span class="sxs-lookup"><span data-stu-id="80cfb-109">Error</span></span>|  
|<span data-ttu-id="80cfb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="80cfb-110">Channel</span></span>|<span data-ttu-id="80cfb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="80cfb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80cfb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="80cfb-112">Description</span></span>  
 <span data-ttu-id="80cfb-113">Indica que o provedor SQL não estendeu a validade de bloqueio ou devido à validade de bloqueio já passada ou o proprietário de bloqueio foi excluído.</span><span class="sxs-lookup"><span data-stu-id="80cfb-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="80cfb-114">O SqlWorkflowInstanceStore será anuladas.</span><span class="sxs-lookup"><span data-stu-id="80cfb-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80cfb-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="80cfb-115">Message</span></span>  
 <span data-ttu-id="80cfb-116">Falha em estender a validade do bloqueio; a validade do bloqueio já terminou ou o proprietário do bloqueio foi excluído.</span><span class="sxs-lookup"><span data-stu-id="80cfb-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="80cfb-117">Anulando SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="80cfb-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80cfb-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="80cfb-118">Details</span></span>  
  
|<span data-ttu-id="80cfb-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="80cfb-119">Data Item Name</span></span>|<span data-ttu-id="80cfb-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="80cfb-120">Data Item Type</span></span>|<span data-ttu-id="80cfb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="80cfb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80cfb-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80cfb-122">AppDomain</span></span>|<span data-ttu-id="80cfb-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="80cfb-123">xs:string</span></span>|<span data-ttu-id="80cfb-124">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80cfb-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
