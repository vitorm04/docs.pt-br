---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="4e3be-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="4e3be-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="4e3be-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4e3be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e3be-104">ID</span><span class="sxs-lookup"><span data-stu-id="4e3be-104">ID</span></span>|<span data-ttu-id="4e3be-105">39458</span><span class="sxs-lookup"><span data-stu-id="4e3be-105">39458</span></span>|  
|<span data-ttu-id="4e3be-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4e3be-106">Keywords</span></span>|<span data-ttu-id="4e3be-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="4e3be-107">WFTracking</span></span>|  
|<span data-ttu-id="4e3be-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4e3be-108">Level</span></span>|<span data-ttu-id="4e3be-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="4e3be-109">Warning</span></span>|  
|<span data-ttu-id="4e3be-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4e3be-110">Channel</span></span>|<span data-ttu-id="4e3be-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="4e3be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e3be-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e3be-112">Description</span></span>  
 <span data-ttu-id="4e3be-113">Indica que um registro de rastreamento foi truncado.</span><span class="sxs-lookup"><span data-stu-id="4e3be-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="4e3be-114">Variáveis/anotações/dados do usuário serem removidos.</span><span class="sxs-lookup"><span data-stu-id="4e3be-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e3be-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4e3be-115">Message</span></span>  
 <span data-ttu-id="4e3be-116">Registro truncado %1 de rastreamento gravados para a sessão de ETW com provedor %2.</span><span class="sxs-lookup"><span data-stu-id="4e3be-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="4e3be-117">Dados de variáveis/anotações/usuários foram removidos</span><span class="sxs-lookup"><span data-stu-id="4e3be-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e3be-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4e3be-118">Details</span></span>  
  
|<span data-ttu-id="4e3be-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4e3be-119">Data Item Name</span></span>|<span data-ttu-id="4e3be-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4e3be-120">Data Item Type</span></span>|<span data-ttu-id="4e3be-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e3be-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e3be-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="4e3be-122">RecordNumber</span></span>|<span data-ttu-id="4e3be-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e3be-123">xs:string</span></span>|<span data-ttu-id="4e3be-124">O número de registro controlando.</span><span class="sxs-lookup"><span data-stu-id="4e3be-124">The tracking record number.</span></span>|  
|<span data-ttu-id="4e3be-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="4e3be-125">ProviderId</span></span>|<span data-ttu-id="4e3be-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e3be-126">xs:string</span></span>|<span data-ttu-id="4e3be-127">A identificação do provedor de ETW</span><span class="sxs-lookup"><span data-stu-id="4e3be-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="4e3be-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4e3be-128">AppDomain</span></span>|<span data-ttu-id="4e3be-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="4e3be-129">xs:string</span></span>|<span data-ttu-id="4e3be-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4e3be-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
