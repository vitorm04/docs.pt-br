---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774212"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="6f29a-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="6f29a-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="6f29a-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6f29a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f29a-104">ID</span><span class="sxs-lookup"><span data-stu-id="6f29a-104">ID</span></span>|<span data-ttu-id="6f29a-105">4212</span><span class="sxs-lookup"><span data-stu-id="6f29a-105">4212</span></span>|  
|<span data-ttu-id="6f29a-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="6f29a-106">Keywords</span></span>|<span data-ttu-id="6f29a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6f29a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6f29a-108">Nível</span><span class="sxs-lookup"><span data-stu-id="6f29a-108">Level</span></span>|<span data-ttu-id="6f29a-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="6f29a-109">Warning</span></span>|  
|<span data-ttu-id="6f29a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="6f29a-110">Channel</span></span>|<span data-ttu-id="6f29a-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="6f29a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6f29a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f29a-112">Description</span></span>  
 <span data-ttu-id="6f29a-113">O provedor SQL após um tempo limite tentar obter o bloqueio de instância.</span><span class="sxs-lookup"><span data-stu-id="6f29a-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6f29a-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="6f29a-114">Message</span></span>  
 <span data-ttu-id="6f29a-115">Tempo limite ao tentar adquirir o bloqueio da instância.</span><span class="sxs-lookup"><span data-stu-id="6f29a-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="6f29a-116">A operação não concluiu dentro do tempo limite distribuído de %1.</span><span class="sxs-lookup"><span data-stu-id="6f29a-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="6f29a-117">O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.</span><span class="sxs-lookup"><span data-stu-id="6f29a-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6f29a-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6f29a-118">Details</span></span>  
  
|<span data-ttu-id="6f29a-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="6f29a-119">Data Item Name</span></span>|<span data-ttu-id="6f29a-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="6f29a-120">Data Item Type</span></span>|<span data-ttu-id="6f29a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f29a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6f29a-122">Atraso</span><span class="sxs-lookup"><span data-stu-id="6f29a-122">Delay</span></span>|<span data-ttu-id="6f29a-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="6f29a-123">xs:string</span></span>|<span data-ttu-id="6f29a-124">O atraso entre o tenta.</span><span class="sxs-lookup"><span data-stu-id="6f29a-124">The delay between retries.</span></span>|  
|<span data-ttu-id="6f29a-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6f29a-125">AppDomain</span></span>|<span data-ttu-id="6f29a-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="6f29a-126">xs:string</span></span>|<span data-ttu-id="6f29a-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6f29a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
