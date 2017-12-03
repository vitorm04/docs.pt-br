---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="82396-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="82396-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="82396-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="82396-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82396-104">ID</span><span class="sxs-lookup"><span data-stu-id="82396-104">ID</span></span>|<span data-ttu-id="82396-105">39458</span><span class="sxs-lookup"><span data-stu-id="82396-105">39458</span></span>|  
|<span data-ttu-id="82396-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="82396-106">Keywords</span></span>|<span data-ttu-id="82396-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="82396-107">WFTracking</span></span>|  
|<span data-ttu-id="82396-108">Nível</span><span class="sxs-lookup"><span data-stu-id="82396-108">Level</span></span>|<span data-ttu-id="82396-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="82396-109">Warning</span></span>|  
|<span data-ttu-id="82396-110">Canal</span><span class="sxs-lookup"><span data-stu-id="82396-110">Channel</span></span>|<span data-ttu-id="82396-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="82396-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="82396-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="82396-112">Description</span></span>  
 <span data-ttu-id="82396-113">Indica que um registro de rastreamento foi truncado.</span><span class="sxs-lookup"><span data-stu-id="82396-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="82396-114">Variáveis/anotações/dados do usuário serem removidos.</span><span class="sxs-lookup"><span data-stu-id="82396-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="82396-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82396-115">Message</span></span>  
 <span data-ttu-id="82396-116">Registro truncado %1 de rastreamento gravados para a sessão de ETW com provedor %2.</span><span class="sxs-lookup"><span data-stu-id="82396-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="82396-117">Dados de variáveis/anotações/usuários foram removidos</span><span class="sxs-lookup"><span data-stu-id="82396-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="82396-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="82396-118">Details</span></span>  
  
|<span data-ttu-id="82396-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="82396-119">Data Item Name</span></span>|<span data-ttu-id="82396-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="82396-120">Data Item Type</span></span>|<span data-ttu-id="82396-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="82396-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="82396-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="82396-122">RecordNumber</span></span>|<span data-ttu-id="82396-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="82396-123">xs:string</span></span>|<span data-ttu-id="82396-124">O número de registro controlando.</span><span class="sxs-lookup"><span data-stu-id="82396-124">The tracking record number.</span></span>|  
|<span data-ttu-id="82396-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="82396-125">ProviderId</span></span>|<span data-ttu-id="82396-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="82396-126">xs:string</span></span>|<span data-ttu-id="82396-127">A identificação do provedor de ETW</span><span class="sxs-lookup"><span data-stu-id="82396-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="82396-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="82396-128">AppDomain</span></span>|<span data-ttu-id="82396-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="82396-129">xs:string</span></span>|<span data-ttu-id="82396-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="82396-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
