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
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="ca258-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="ca258-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="ca258-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ca258-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca258-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca258-104">ID</span></span>|<span data-ttu-id="ca258-105">4208</span><span class="sxs-lookup"><span data-stu-id="ca258-105">4208</span></span>|  
|<span data-ttu-id="ca258-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ca258-106">Keywords</span></span>|<span data-ttu-id="ca258-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ca258-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ca258-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ca258-108">Level</span></span>|<span data-ttu-id="ca258-109">Informações</span><span class="sxs-lookup"><span data-stu-id="ca258-109">Information</span></span>|  
|<span data-ttu-id="ca258-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ca258-110">Channel</span></span>|<span data-ttu-id="ca258-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ca258-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca258-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca258-112">Description</span></span>  
 <span data-ttu-id="ca258-113">Indica que o provedor SQL é experimentando de novo um comando SQL devido a um erro SQL.</span><span class="sxs-lookup"><span data-stu-id="ca258-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca258-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ca258-114">Message</span></span>  
 <span data-ttu-id="ca258-115">Experimentando de novo um comando SQL por causa do erro número %1. SQL.</span><span class="sxs-lookup"><span data-stu-id="ca258-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca258-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ca258-116">Details</span></span>  
  
|<span data-ttu-id="ca258-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ca258-117">Data Item Name</span></span>|<span data-ttu-id="ca258-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ca258-118">Data Item Type</span></span>|<span data-ttu-id="ca258-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca258-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca258-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="ca258-120">ErrorNumber</span></span>|<span data-ttu-id="ca258-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca258-121">xs:string</span></span>|<span data-ttu-id="ca258-122">O número do erro SQL.</span><span class="sxs-lookup"><span data-stu-id="ca258-122">The SQL error number.</span></span>|  
|<span data-ttu-id="ca258-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca258-123">AppDomain</span></span>|<span data-ttu-id="ca258-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca258-124">xs:string</span></span>|<span data-ttu-id="ca258-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ca258-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
