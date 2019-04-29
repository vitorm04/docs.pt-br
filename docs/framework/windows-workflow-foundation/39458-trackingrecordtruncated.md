---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774407"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="36f1f-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="36f1f-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="36f1f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="36f1f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36f1f-104">ID</span><span class="sxs-lookup"><span data-stu-id="36f1f-104">ID</span></span>|<span data-ttu-id="36f1f-105">39458</span><span class="sxs-lookup"><span data-stu-id="36f1f-105">39458</span></span>|  
|<span data-ttu-id="36f1f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="36f1f-106">Keywords</span></span>|<span data-ttu-id="36f1f-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="36f1f-107">WFTracking</span></span>|  
|<span data-ttu-id="36f1f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="36f1f-108">Level</span></span>|<span data-ttu-id="36f1f-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="36f1f-109">Warning</span></span>|  
|<span data-ttu-id="36f1f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="36f1f-110">Channel</span></span>|<span data-ttu-id="36f1f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="36f1f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="36f1f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="36f1f-112">Description</span></span>  
 <span data-ttu-id="36f1f-113">Indica que um registro de rastreamento foi truncado.</span><span class="sxs-lookup"><span data-stu-id="36f1f-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="36f1f-114">Variáveis/anotações/dados do usuário serem removidos.</span><span class="sxs-lookup"><span data-stu-id="36f1f-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="36f1f-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="36f1f-115">Message</span></span>  
 <span data-ttu-id="36f1f-116">Registro truncado %1 de rastreamento gravados para a sessão de ETW com provedor %2.</span><span class="sxs-lookup"><span data-stu-id="36f1f-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="36f1f-117">Dados de variáveis/anotações/usuários foram removidos</span><span class="sxs-lookup"><span data-stu-id="36f1f-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="36f1f-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="36f1f-118">Details</span></span>  
  
|<span data-ttu-id="36f1f-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="36f1f-119">Data Item Name</span></span>|<span data-ttu-id="36f1f-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="36f1f-120">Data Item Type</span></span>|<span data-ttu-id="36f1f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="36f1f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="36f1f-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="36f1f-122">RecordNumber</span></span>|<span data-ttu-id="36f1f-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="36f1f-123">xs:string</span></span>|<span data-ttu-id="36f1f-124">O número de registro controlando.</span><span class="sxs-lookup"><span data-stu-id="36f1f-124">The tracking record number.</span></span>|  
|<span data-ttu-id="36f1f-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="36f1f-125">ProviderId</span></span>|<span data-ttu-id="36f1f-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="36f1f-126">xs:string</span></span>|<span data-ttu-id="36f1f-127">A identificação do provedor de ETW</span><span class="sxs-lookup"><span data-stu-id="36f1f-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="36f1f-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="36f1f-128">AppDomain</span></span>|<span data-ttu-id="36f1f-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="36f1f-129">xs:string</span></span>|<span data-ttu-id="36f1f-130">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="36f1f-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
