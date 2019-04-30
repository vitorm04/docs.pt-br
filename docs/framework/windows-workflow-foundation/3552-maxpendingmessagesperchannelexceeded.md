---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945932"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="524cd-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="524cd-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="524cd-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="524cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="524cd-104">ID</span><span class="sxs-lookup"><span data-stu-id="524cd-104">ID</span></span>|<span data-ttu-id="524cd-105">3552</span><span class="sxs-lookup"><span data-stu-id="524cd-105">3552</span></span>|  
|<span data-ttu-id="524cd-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="524cd-106">Keywords</span></span>|<span data-ttu-id="524cd-107">Cota, WFServices</span><span class="sxs-lookup"><span data-stu-id="524cd-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="524cd-108">Nível</span><span class="sxs-lookup"><span data-stu-id="524cd-108">Level</span></span>|<span data-ttu-id="524cd-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="524cd-109">Warning</span></span>|  
|<span data-ttu-id="524cd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="524cd-110">Channel</span></span>|<span data-ttu-id="524cd-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="524cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="524cd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="524cd-112">Description</span></span>  
 <span data-ttu-id="524cd-113">Indica que o limite de “MaxPendingMessagesPerChannel” de regulador de pressão foi atingido.</span><span class="sxs-lookup"><span data-stu-id="524cd-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="524cd-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="524cd-114">Message</span></span>  
 <span data-ttu-id="524cd-115">O Acelerador de pressão "MaxPendingMessagesPerChannel" limite de '%1' foi atingido.</span><span class="sxs-lookup"><span data-stu-id="524cd-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="524cd-116">Para aumentar esse limite, ajuste a propriedade MaxPendingMessagesPerChannel no BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="524cd-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="524cd-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="524cd-117">Details</span></span>  
  
|<span data-ttu-id="524cd-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="524cd-118">Data Item Name</span></span>|<span data-ttu-id="524cd-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="524cd-119">Data Item Type</span></span>|<span data-ttu-id="524cd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="524cd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="524cd-121">Limite</span><span class="sxs-lookup"><span data-stu-id="524cd-121">Limit</span></span>|<span data-ttu-id="524cd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="524cd-122">xs:string</span></span>|<span data-ttu-id="524cd-123">O limite de regulador de pressão de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="524cd-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="524cd-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="524cd-124">AppDomain</span></span>|<span data-ttu-id="524cd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="524cd-125">xs:string</span></span>|<span data-ttu-id="524cd-126">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="524cd-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
