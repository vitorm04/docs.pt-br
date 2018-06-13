---
title: Método ICorProfilerModuleEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9249e6f5ee7b15d55f5518263b0ac2e31b64e993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454454"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="2a82b-102">Método ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="2a82b-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="2a82b-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2a82b-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a82b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a82b-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a82b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a82b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2a82b-106">[out] Um ponteiro para o ponteiro de interface que aponta para a cópia desse [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2a82b-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="2a82b-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="2a82b-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="2a82b-108">No entanto, posição de cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="2a82b-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a82b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a82b-109">Requirements</span></span>  
 <span data-ttu-id="2a82b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a82b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a82b-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a82b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a82b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a82b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a82b-113">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a82b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a82b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a82b-114">See Also</span></span>  
 [<span data-ttu-id="2a82b-115">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="2a82b-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="2a82b-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2a82b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
