---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924209"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="57fe5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="57fe5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="57fe5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="57fe5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57fe5-104">ID</span><span class="sxs-lookup"><span data-stu-id="57fe5-104">ID</span></span>|<span data-ttu-id="57fe5-105">1132</span><span class="sxs-lookup"><span data-stu-id="57fe5-105">1132</span></span>|  
|<span data-ttu-id="57fe5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="57fe5-106">Keywords</span></span>|<span data-ttu-id="57fe5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="57fe5-107">WFRuntime</span></span>|  
|<span data-ttu-id="57fe5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="57fe5-108">Level</span></span>|<span data-ttu-id="57fe5-109">Informações</span><span class="sxs-lookup"><span data-stu-id="57fe5-109">Information</span></span>|  
|<span data-ttu-id="57fe5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="57fe5-110">Channel</span></span>|<span data-ttu-id="57fe5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="57fe5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57fe5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="57fe5-112">Description</span></span>  
 <span data-ttu-id="57fe5-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que não está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="57fe5-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57fe5-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="57fe5-114">Message</span></span>  
 <span data-ttu-id="57fe5-115">InvokeMethod “%1" - o método não usa o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="57fe5-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57fe5-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="57fe5-116">Details</span></span>  
  
|<span data-ttu-id="57fe5-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="57fe5-117">Data Item Name</span></span>|<span data-ttu-id="57fe5-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="57fe5-118">Data Item Type</span></span>|<span data-ttu-id="57fe5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="57fe5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57fe5-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="57fe5-120">InvokeMethod</span></span>|<span data-ttu-id="57fe5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="57fe5-121">xs:string</span></span>|<span data-ttu-id="57fe5-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="57fe5-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="57fe5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="57fe5-123">AppDomain</span></span>|<span data-ttu-id="57fe5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="57fe5-124">xs:string</span></span>|<span data-ttu-id="57fe5-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="57fe5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
