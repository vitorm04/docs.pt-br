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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="707fb-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="707fb-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="707fb-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="707fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="707fb-104">ID</span><span class="sxs-lookup"><span data-stu-id="707fb-104">ID</span></span>|<span data-ttu-id="707fb-105">39458</span><span class="sxs-lookup"><span data-stu-id="707fb-105">39458</span></span>|  
|<span data-ttu-id="707fb-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="707fb-106">Keywords</span></span>|<span data-ttu-id="707fb-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="707fb-107">WFTracking</span></span>|  
|<span data-ttu-id="707fb-108">Nível</span><span class="sxs-lookup"><span data-stu-id="707fb-108">Level</span></span>|<span data-ttu-id="707fb-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="707fb-109">Warning</span></span>|  
|<span data-ttu-id="707fb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="707fb-110">Channel</span></span>|<span data-ttu-id="707fb-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="707fb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="707fb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="707fb-112">Description</span></span>  
 <span data-ttu-id="707fb-113">Indica que um registro de rastreamento foi truncado.</span><span class="sxs-lookup"><span data-stu-id="707fb-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="707fb-114">Variáveis/anotações/dados do usuário serem removidos.</span><span class="sxs-lookup"><span data-stu-id="707fb-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="707fb-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="707fb-115">Message</span></span>  
 <span data-ttu-id="707fb-116">Registro truncado %1 de rastreamento gravados para a sessão de ETW com provedor %2.</span><span class="sxs-lookup"><span data-stu-id="707fb-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="707fb-117">Dados de variáveis/anotações/usuários foram removidos</span><span class="sxs-lookup"><span data-stu-id="707fb-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="707fb-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="707fb-118">Details</span></span>  
  
|<span data-ttu-id="707fb-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="707fb-119">Data Item Name</span></span>|<span data-ttu-id="707fb-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="707fb-120">Data Item Type</span></span>|<span data-ttu-id="707fb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="707fb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="707fb-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="707fb-122">RecordNumber</span></span>|<span data-ttu-id="707fb-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="707fb-123">xs:string</span></span>|<span data-ttu-id="707fb-124">O número de registro controlando.</span><span class="sxs-lookup"><span data-stu-id="707fb-124">The tracking record number.</span></span>|  
|<span data-ttu-id="707fb-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="707fb-125">ProviderId</span></span>|<span data-ttu-id="707fb-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="707fb-126">xs:string</span></span>|<span data-ttu-id="707fb-127">A identificação do provedor de ETW</span><span class="sxs-lookup"><span data-stu-id="707fb-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="707fb-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="707fb-128">AppDomain</span></span>|<span data-ttu-id="707fb-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="707fb-129">xs:string</span></span>|<span data-ttu-id="707fb-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="707fb-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
