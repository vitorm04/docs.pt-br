---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f87e99585ccbdf3b89653f026860e7b66dc6c9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="ca580-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="ca580-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="ca580-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ca580-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca580-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca580-104">ID</span></span>|<span data-ttu-id="ca580-105">4209</span><span class="sxs-lookup"><span data-stu-id="ca580-105">4209</span></span>|  
|<span data-ttu-id="ca580-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ca580-106">Keywords</span></span>|<span data-ttu-id="ca580-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ca580-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ca580-108">Nível</span><span class="sxs-lookup"><span data-stu-id="ca580-108">Level</span></span>|<span data-ttu-id="ca580-109">Erro</span><span class="sxs-lookup"><span data-stu-id="ca580-109">Error</span></span>|  
|<span data-ttu-id="ca580-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ca580-110">Channel</span></span>|<span data-ttu-id="ca580-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="ca580-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca580-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca580-112">Description</span></span>  
 <span data-ttu-id="ca580-113">Indica que um tempo limite foi encontrado ao tentar abrir uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="ca580-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca580-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ca580-114">Message</span></span>  
 <span data-ttu-id="ca580-115">O tempo limite está tentando abrir uma conexão de SQL.</span><span class="sxs-lookup"><span data-stu-id="ca580-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="ca580-116">A operação não concluiu dentro do tempo limite distribuído de %1.</span><span class="sxs-lookup"><span data-stu-id="ca580-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="ca580-117">O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.</span><span class="sxs-lookup"><span data-stu-id="ca580-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca580-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ca580-118">Details</span></span>  
  
|<span data-ttu-id="ca580-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="ca580-119">Data Item Name</span></span>|<span data-ttu-id="ca580-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="ca580-120">Data Item Type</span></span>|<span data-ttu-id="ca580-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca580-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca580-122">Tempo limite</span><span class="sxs-lookup"><span data-stu-id="ca580-122">Timeout</span></span>|<span data-ttu-id="ca580-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca580-123">xs:string</span></span>|<span data-ttu-id="ca580-124">O valor de tempo limite para abrir a conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="ca580-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="ca580-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca580-125">AppDomain</span></span>|<span data-ttu-id="ca580-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca580-126">xs:string</span></span>|<span data-ttu-id="ca580-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ca580-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
