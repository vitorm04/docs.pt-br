---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="4d48f-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="4d48f-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="4d48f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4d48f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d48f-104">ID</span><span class="sxs-lookup"><span data-stu-id="4d48f-104">ID</span></span>|<span data-ttu-id="4d48f-105">1126</span><span class="sxs-lookup"><span data-stu-id="4d48f-105">1126</span></span>|  
|<span data-ttu-id="4d48f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="4d48f-106">Keywords</span></span>|<span data-ttu-id="4d48f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4d48f-107">WFRuntime</span></span>|  
|<span data-ttu-id="4d48f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="4d48f-108">Level</span></span>|<span data-ttu-id="4d48f-109">Informações</span><span class="sxs-lookup"><span data-stu-id="4d48f-109">Information</span></span>|  
|<span data-ttu-id="4d48f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4d48f-110">Channel</span></span>|<span data-ttu-id="4d48f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="4d48f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d48f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d48f-112">Description</span></span>  
 <span data-ttu-id="4d48f-113">Indica que uma exceção foi lançada pelo método chamado pela atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="4d48f-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d48f-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4d48f-114">Message</span></span>  
 <span data-ttu-id="4d48f-115">Uma exceção foi lançada no método chamado pela atividade “%1 ".</span><span class="sxs-lookup"><span data-stu-id="4d48f-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="4d48f-116">%2</span><span class="sxs-lookup"><span data-stu-id="4d48f-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d48f-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4d48f-117">Details</span></span>  
  
|<span data-ttu-id="4d48f-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="4d48f-118">Data Item Name</span></span>|<span data-ttu-id="4d48f-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="4d48f-119">Data Item Type</span></span>|<span data-ttu-id="4d48f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d48f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d48f-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4d48f-121">InvokeMethod</span></span>|<span data-ttu-id="4d48f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d48f-122">xs:string</span></span>|<span data-ttu-id="4d48f-123">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="4d48f-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="4d48f-124">Exceção</span><span class="sxs-lookup"><span data-stu-id="4d48f-124">Exception</span></span>|<span data-ttu-id="4d48f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d48f-125">xs:string</span></span>|<span data-ttu-id="4d48f-126">Os detalhes de exceção para a exceção</span><span class="sxs-lookup"><span data-stu-id="4d48f-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="4d48f-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d48f-127">AppDomain</span></span>|<span data-ttu-id="4d48f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d48f-128">xs:string</span></span>|<span data-ttu-id="4d48f-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4d48f-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
