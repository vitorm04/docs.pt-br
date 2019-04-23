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
ms.openlocfilehash: fba17a2ffad9220acdbc79726efe0d3d4184978a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188546"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="cd7cb-102">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="cd7cb-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="cd7cb-103">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd7cb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cd7cb-104">Methods</span></span>  
  
|<span data-ttu-id="cd7cb-105">Método</span><span class="sxs-lookup"><span data-stu-id="cd7cb-105">Method</span></span>|<span data-ttu-id="cd7cb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd7cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd7cb-107">Método AbortItem</span><span class="sxs-lookup"><span data-stu-id="cd7cb-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="cd7cb-108">Permite que o assembly no cache de assembly global executar operações de limpeza antes do lançamento.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="cd7cb-109">Método Commit</span><span class="sxs-lookup"><span data-stu-id="cd7cb-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="cd7cb-110">Confirma a referência de assembly em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="cd7cb-111">Método CreateStream</span><span class="sxs-lookup"><span data-stu-id="cd7cb-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="cd7cb-112">Cria um fluxo com o nome especificado e o formato.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd7cb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd7cb-113">Requirements</span></span>  
 <span data-ttu-id="cd7cb-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd7cb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7cb-115">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cd7cb-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cd7cb-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7cb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd7cb-117">See also</span></span>

- [<span data-ttu-id="cd7cb-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="cd7cb-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="cd7cb-119">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="cd7cb-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="cd7cb-120">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="cd7cb-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
