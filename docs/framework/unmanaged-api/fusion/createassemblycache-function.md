---
title: Função CreateAssemblyCache
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6327c9d7dee548957a569b587faefe3d6d9cb1b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497763"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="89e51-102">Função CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="89e51-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="89e51-103">Obtém um ponteiro para um novo [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instância que representa o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="89e51-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89e51-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89e51-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="89e51-106">[out] Retornado `IAssemblyCache` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="89e51-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="89e51-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="89e51-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="89e51-108">`dwReserved` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="89e51-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e51-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89e51-109">Requirements</span></span>  
 <span data-ttu-id="89e51-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e51-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="89e51-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89e51-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="89e51-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89e51-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e51-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89e51-114">See also</span></span>
- [<span data-ttu-id="89e51-115">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="89e51-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="89e51-116">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="89e51-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="89e51-117">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="89e51-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
