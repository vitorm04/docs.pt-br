---
title: Interface IAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 2493b5338824e1eab3f82a9023bbcced59a98fc8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134460"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="c3f68-102">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="c3f68-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="c3f68-103">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="c3f68-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3f68-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c3f68-104">Methods</span></span>  
  
|<span data-ttu-id="c3f68-105">Método</span><span class="sxs-lookup"><span data-stu-id="c3f68-105">Method</span></span>|<span data-ttu-id="c3f68-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f68-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3f68-107">Método AbortItem</span><span class="sxs-lookup"><span data-stu-id="c3f68-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="c3f68-108">Permite que o assembly no cache de assembly global execute operações de limpeza antes que ele seja liberado.</span><span class="sxs-lookup"><span data-stu-id="c3f68-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="c3f68-109">Método Commit</span><span class="sxs-lookup"><span data-stu-id="c3f68-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="c3f68-110">Confirma a referência de assembly armazenada em cache para a memória.</span><span class="sxs-lookup"><span data-stu-id="c3f68-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="c3f68-111">Método CreateStream</span><span class="sxs-lookup"><span data-stu-id="c3f68-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="c3f68-112">Cria um fluxo com o nome e o formato especificados.</span><span class="sxs-lookup"><span data-stu-id="c3f68-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3f68-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3f68-113">Requirements</span></span>  
 <span data-ttu-id="c3f68-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f68-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f68-115">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c3f68-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c3f68-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f68-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3f68-117">See also</span></span>

- [<span data-ttu-id="c3f68-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="c3f68-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="c3f68-119">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="c3f68-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="c3f68-120">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="c3f68-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
