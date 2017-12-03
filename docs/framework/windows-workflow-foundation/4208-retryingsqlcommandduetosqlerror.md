---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="99a86-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="99a86-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="99a86-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="99a86-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99a86-104">ID</span><span class="sxs-lookup"><span data-stu-id="99a86-104">ID</span></span>|<span data-ttu-id="99a86-105">4208</span><span class="sxs-lookup"><span data-stu-id="99a86-105">4208</span></span>|  
|<span data-ttu-id="99a86-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="99a86-106">Keywords</span></span>|<span data-ttu-id="99a86-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="99a86-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="99a86-108">Nível</span><span class="sxs-lookup"><span data-stu-id="99a86-108">Level</span></span>|<span data-ttu-id="99a86-109">Informações</span><span class="sxs-lookup"><span data-stu-id="99a86-109">Information</span></span>|  
|<span data-ttu-id="99a86-110">Canal</span><span class="sxs-lookup"><span data-stu-id="99a86-110">Channel</span></span>|<span data-ttu-id="99a86-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="99a86-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="99a86-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="99a86-112">Description</span></span>  
 <span data-ttu-id="99a86-113">Indica que o provedor SQL é experimentando de novo um comando SQL devido a um erro SQL.</span><span class="sxs-lookup"><span data-stu-id="99a86-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="99a86-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="99a86-114">Message</span></span>  
 <span data-ttu-id="99a86-115">Experimentando de novo um comando SQL por causa do erro número %1. SQL.</span><span class="sxs-lookup"><span data-stu-id="99a86-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="99a86-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="99a86-116">Details</span></span>  
  
|<span data-ttu-id="99a86-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="99a86-117">Data Item Name</span></span>|<span data-ttu-id="99a86-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="99a86-118">Data Item Type</span></span>|<span data-ttu-id="99a86-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="99a86-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="99a86-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="99a86-120">ErrorNumber</span></span>|<span data-ttu-id="99a86-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="99a86-121">xs:string</span></span>|<span data-ttu-id="99a86-122">O número do erro SQL.</span><span class="sxs-lookup"><span data-stu-id="99a86-122">The SQL error number.</span></span>|  
|<span data-ttu-id="99a86-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="99a86-123">AppDomain</span></span>|<span data-ttu-id="99a86-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="99a86-124">xs:string</span></span>|<span data-ttu-id="99a86-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="99a86-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
