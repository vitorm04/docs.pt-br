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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fabe6f2c023bf9b997d2a4e19b4a3755c93f408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="5cc13-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="5cc13-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="5cc13-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5cc13-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cc13-104">ID</span><span class="sxs-lookup"><span data-stu-id="5cc13-104">ID</span></span>|<span data-ttu-id="5cc13-105">4203</span><span class="sxs-lookup"><span data-stu-id="5cc13-105">4203</span></span>|  
|<span data-ttu-id="5cc13-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5cc13-106">Keywords</span></span>|<span data-ttu-id="5cc13-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5cc13-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5cc13-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5cc13-108">Level</span></span>|<span data-ttu-id="5cc13-109">Erro</span><span class="sxs-lookup"><span data-stu-id="5cc13-109">Error</span></span>|  
|<span data-ttu-id="5cc13-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5cc13-110">Channel</span></span>|<span data-ttu-id="5cc13-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="5cc13-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5cc13-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cc13-112">Description</span></span>  
 <span data-ttu-id="5cc13-113">Indica que o provedor SQL não estendeu a validade de bloqueio ou devido à validade de bloqueio já passada ou o proprietário de bloqueio foi excluído.</span><span class="sxs-lookup"><span data-stu-id="5cc13-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="5cc13-114">O SqlWorkflowInstanceStore será anuladas.</span><span class="sxs-lookup"><span data-stu-id="5cc13-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5cc13-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5cc13-115">Message</span></span>  
 <span data-ttu-id="5cc13-116">Falha em estender a validade do bloqueio; a validade do bloqueio já terminou ou o proprietário do bloqueio foi excluído.</span><span class="sxs-lookup"><span data-stu-id="5cc13-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="5cc13-117">Anulando SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="5cc13-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5cc13-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5cc13-118">Details</span></span>  
  
|<span data-ttu-id="5cc13-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5cc13-119">Data Item Name</span></span>|<span data-ttu-id="5cc13-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5cc13-120">Data Item Type</span></span>|<span data-ttu-id="5cc13-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cc13-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5cc13-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5cc13-122">AppDomain</span></span>|<span data-ttu-id="5cc13-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="5cc13-123">xs:string</span></span>|<span data-ttu-id="5cc13-124">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5cc13-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
