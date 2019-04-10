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
ms.openlocfilehash: 9053505f7356f4618993ead911f730909f53f383
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227139"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="cfd61-102">Método ICorProfilerModuleEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="cfd61-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="cfd61-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="cfd61-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfd61-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfd61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfd61-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="cfd61-106">[out] Um ponteiro para o ponteiro de interface que aponta para a cópia deste [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="cfd61-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="cfd61-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="cfd61-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="cfd61-108">No entanto, a posição do cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="cfd61-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd61-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfd61-109">Requirements</span></span>  
 <span data-ttu-id="cfd61-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd61-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd61-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfd61-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfd61-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfd61-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cfd61-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cfd61-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cfd61-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfd61-114">See also</span></span>

- [<span data-ttu-id="cfd61-115">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="cfd61-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="cfd61-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="cfd61-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
