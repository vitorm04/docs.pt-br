---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512659"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="431ca-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="431ca-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="431ca-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="431ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="431ca-104">ID</span><span class="sxs-lookup"><span data-stu-id="431ca-104">ID</span></span>|<span data-ttu-id="431ca-105">1131</span><span class="sxs-lookup"><span data-stu-id="431ca-105">1131</span></span>|  
|<span data-ttu-id="431ca-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="431ca-106">Keywords</span></span>|<span data-ttu-id="431ca-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="431ca-107">WFRuntime</span></span>|  
|<span data-ttu-id="431ca-108">Nível</span><span class="sxs-lookup"><span data-stu-id="431ca-108">Level</span></span>|<span data-ttu-id="431ca-109">Informações</span><span class="sxs-lookup"><span data-stu-id="431ca-109">Information</span></span>|  
|<span data-ttu-id="431ca-110">Canal</span><span class="sxs-lookup"><span data-stu-id="431ca-110">Channel</span></span>|<span data-ttu-id="431ca-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="431ca-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="431ca-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="431ca-112">Description</span></span>  
 <span data-ttu-id="431ca-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="431ca-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="431ca-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="431ca-114">Message</span></span>  
 <span data-ttu-id="431ca-115">InvokeMethod “%1 " - o método utiliza o padrão assíncrono de “%2 " e “%3 ".</span><span class="sxs-lookup"><span data-stu-id="431ca-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="431ca-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="431ca-116">Details</span></span>  
  
|<span data-ttu-id="431ca-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="431ca-117">Data Item Name</span></span>|<span data-ttu-id="431ca-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="431ca-118">Data Item Type</span></span>|<span data-ttu-id="431ca-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="431ca-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="431ca-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="431ca-120">InvokeMethod</span></span>|<span data-ttu-id="431ca-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="431ca-121">xs:string</span></span>|<span data-ttu-id="431ca-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="431ca-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="431ca-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="431ca-123">BeginMethod</span></span>|<span data-ttu-id="431ca-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="431ca-124">xs:string</span></span>|<span data-ttu-id="431ca-125">O nome do método inicial.</span><span class="sxs-lookup"><span data-stu-id="431ca-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="431ca-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="431ca-126">EndMethod</span></span>|<span data-ttu-id="431ca-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="431ca-127">xs:string</span></span>|<span data-ttu-id="431ca-128">O nome do método final.</span><span class="sxs-lookup"><span data-stu-id="431ca-128">The name of the end method.</span></span>|  
|<span data-ttu-id="431ca-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="431ca-129">AppDomain</span></span>|<span data-ttu-id="431ca-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="431ca-130">xs:string</span></span>|<span data-ttu-id="431ca-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="431ca-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
