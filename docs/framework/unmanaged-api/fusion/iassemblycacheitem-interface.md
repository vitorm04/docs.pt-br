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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796711"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="5bbad-102">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="5bbad-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="5bbad-103">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="5bbad-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5bbad-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5bbad-104">Methods</span></span>  
  
|<span data-ttu-id="5bbad-105">Método</span><span class="sxs-lookup"><span data-stu-id="5bbad-105">Method</span></span>|<span data-ttu-id="5bbad-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bbad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bbad-107">Método AbortItem</span><span class="sxs-lookup"><span data-stu-id="5bbad-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="5bbad-108">Permite que o assembly no cache de assembly global execute operações de limpeza antes que ele seja liberado.</span><span class="sxs-lookup"><span data-stu-id="5bbad-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="5bbad-109">Método Commit</span><span class="sxs-lookup"><span data-stu-id="5bbad-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="5bbad-110">Confirma a referência de assembly armazenada em cache para a memória.</span><span class="sxs-lookup"><span data-stu-id="5bbad-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="5bbad-111">Método CreateStream</span><span class="sxs-lookup"><span data-stu-id="5bbad-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="5bbad-112">Cria um fluxo com o nome e o formato especificados.</span><span class="sxs-lookup"><span data-stu-id="5bbad-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bbad-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bbad-113">Requirements</span></span>  
 <span data-ttu-id="5bbad-114">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bbad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bbad-115">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5bbad-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5bbad-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bbad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbad-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bbad-117">See also</span></span>

- [<span data-ttu-id="5bbad-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="5bbad-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="5bbad-119">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="5bbad-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="5bbad-120">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="5bbad-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
