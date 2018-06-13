---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511225"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="9ef8f-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="9ef8f-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="9ef8f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9ef8f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ef8f-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ef8f-104">ID</span></span>|<span data-ttu-id="9ef8f-105">3552</span><span class="sxs-lookup"><span data-stu-id="9ef8f-105">3552</span></span>|  
|<span data-ttu-id="9ef8f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="9ef8f-106">Keywords</span></span>|<span data-ttu-id="9ef8f-107">Cota, WFServices</span><span class="sxs-lookup"><span data-stu-id="9ef8f-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="9ef8f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="9ef8f-108">Level</span></span>|<span data-ttu-id="9ef8f-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="9ef8f-109">Warning</span></span>|  
|<span data-ttu-id="9ef8f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9ef8f-110">Channel</span></span>|<span data-ttu-id="9ef8f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="9ef8f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ef8f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ef8f-112">Description</span></span>  
 <span data-ttu-id="9ef8f-113">Indica que o limite de “MaxPendingMessagesPerChannel” de regulador de pressão foi atingido.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ef8f-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9ef8f-114">Message</span></span>  
 <span data-ttu-id="9ef8f-115">Foi atingido o limite 'MaxPendingMessagesPerChannel' de '%1' do acelerador.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="9ef8f-116">Para aumentar esse limite, ajuste a propriedade MaxPendingMessagesPerChannel no BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ef8f-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9ef8f-117">Details</span></span>  
  
|<span data-ttu-id="9ef8f-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="9ef8f-118">Data Item Name</span></span>|<span data-ttu-id="9ef8f-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="9ef8f-119">Data Item Type</span></span>|<span data-ttu-id="9ef8f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ef8f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ef8f-121">Limite</span><span class="sxs-lookup"><span data-stu-id="9ef8f-121">Limit</span></span>|<span data-ttu-id="9ef8f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef8f-122">xs:string</span></span>|<span data-ttu-id="9ef8f-123">O limite de regulador de pressão de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="9ef8f-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ef8f-124">AppDomain</span></span>|<span data-ttu-id="9ef8f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef8f-125">xs:string</span></span>|<span data-ttu-id="9ef8f-126">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
