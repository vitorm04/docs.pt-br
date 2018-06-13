---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511858"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="c5706-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="c5706-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="c5706-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c5706-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5706-104">ID</span><span class="sxs-lookup"><span data-stu-id="c5706-104">ID</span></span>|<span data-ttu-id="c5706-105">1132</span><span class="sxs-lookup"><span data-stu-id="c5706-105">1132</span></span>|  
|<span data-ttu-id="c5706-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c5706-106">Keywords</span></span>|<span data-ttu-id="c5706-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c5706-107">WFRuntime</span></span>|  
|<span data-ttu-id="c5706-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c5706-108">Level</span></span>|<span data-ttu-id="c5706-109">Informações</span><span class="sxs-lookup"><span data-stu-id="c5706-109">Information</span></span>|  
|<span data-ttu-id="c5706-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c5706-110">Channel</span></span>|<span data-ttu-id="c5706-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c5706-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c5706-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5706-112">Description</span></span>  
 <span data-ttu-id="c5706-113">Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que não está usando o padrão de async ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="c5706-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c5706-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c5706-114">Message</span></span>  
 <span data-ttu-id="c5706-115">InvokeMethod “%1" - o método não usa o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c5706-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c5706-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c5706-116">Details</span></span>  
  
|<span data-ttu-id="c5706-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c5706-117">Data Item Name</span></span>|<span data-ttu-id="c5706-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c5706-118">Data Item Type</span></span>|<span data-ttu-id="c5706-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5706-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c5706-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="c5706-120">InvokeMethod</span></span>|<span data-ttu-id="c5706-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c5706-121">xs:string</span></span>|<span data-ttu-id="c5706-122">O nome para exibição de atividade de InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="c5706-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="c5706-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c5706-123">AppDomain</span></span>|<span data-ttu-id="c5706-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c5706-124">xs:string</span></span>|<span data-ttu-id="c5706-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c5706-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
