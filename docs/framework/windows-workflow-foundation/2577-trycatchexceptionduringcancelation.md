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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="61879-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="61879-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="61879-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="61879-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61879-104">ID</span><span class="sxs-lookup"><span data-stu-id="61879-104">ID</span></span>|<span data-ttu-id="61879-105">2577</span><span class="sxs-lookup"><span data-stu-id="61879-105">2577</span></span>|  
|<span data-ttu-id="61879-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="61879-106">Keywords</span></span>|<span data-ttu-id="61879-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="61879-107">WFActivities</span></span>|  
|<span data-ttu-id="61879-108">Nível</span><span class="sxs-lookup"><span data-stu-id="61879-108">Level</span></span>|<span data-ttu-id="61879-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="61879-109">Warning</span></span>|  
|<span data-ttu-id="61879-110">Canal</span><span class="sxs-lookup"><span data-stu-id="61879-110">Channel</span></span>|<span data-ttu-id="61879-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="61879-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="61879-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="61879-112">Description</span></span>  
 <span data-ttu-id="61879-113">Indica que uma atividade filho de atividade de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="61879-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="61879-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="61879-114">Message</span></span>  
 <span data-ttu-id="61879-115">Uma atividade filho da atividade “%1 " de TryCatch apresentou uma exceção durante o cancelar.</span><span class="sxs-lookup"><span data-stu-id="61879-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="61879-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="61879-116">Details</span></span>  
  
|<span data-ttu-id="61879-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="61879-117">Data Item Name</span></span>|<span data-ttu-id="61879-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="61879-118">Data Item Type</span></span>|<span data-ttu-id="61879-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="61879-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="61879-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="61879-120">DisplayName</span></span>|<span data-ttu-id="61879-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="61879-121">xs:string</span></span>|<span data-ttu-id="61879-122">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="61879-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="61879-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="61879-123">AppDomain</span></span>|<span data-ttu-id="61879-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="61879-124">xs:string</span></span>|<span data-ttu-id="61879-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="61879-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
