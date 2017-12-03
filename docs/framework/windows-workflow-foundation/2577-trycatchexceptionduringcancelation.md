---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11781bcab37a5034f3bbfadf2c50cbc1c6d378a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="d461e-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="d461e-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="d461e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d461e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d461e-104">ID</span><span class="sxs-lookup"><span data-stu-id="d461e-104">ID</span></span>|<span data-ttu-id="d461e-105">2577</span><span class="sxs-lookup"><span data-stu-id="d461e-105">2577</span></span>|  
|<span data-ttu-id="d461e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d461e-106">Keywords</span></span>|<span data-ttu-id="d461e-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="d461e-107">WFActivities</span></span>|  
|<span data-ttu-id="d461e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="d461e-108">Level</span></span>|<span data-ttu-id="d461e-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="d461e-109">Warning</span></span>|  
|<span data-ttu-id="d461e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d461e-110">Channel</span></span>|<span data-ttu-id="d461e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="d461e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d461e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d461e-112">Description</span></span>  
 <span data-ttu-id="d461e-113">Indica que uma atividade filho de atividade de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="d461e-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d461e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d461e-114">Message</span></span>  
 <span data-ttu-id="d461e-115">Uma atividade filho da atividade “%1 " de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="d461e-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d461e-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d461e-116">Details</span></span>  
  
|<span data-ttu-id="d461e-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="d461e-117">Data Item Name</span></span>|<span data-ttu-id="d461e-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="d461e-118">Data Item Type</span></span>|<span data-ttu-id="d461e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d461e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d461e-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d461e-120">DisplayName</span></span>|<span data-ttu-id="d461e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d461e-121">xs:string</span></span>|<span data-ttu-id="d461e-122">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="d461e-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="d461e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d461e-123">AppDomain</span></span>|<span data-ttu-id="d461e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d461e-124">xs:string</span></span>|<span data-ttu-id="d461e-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d461e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
