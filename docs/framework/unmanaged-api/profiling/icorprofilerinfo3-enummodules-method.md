---
title: Método ICorProfilerInfo3::EnumModules
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 0bb2ba56ed93af7861e53d683a0a777107578a6b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449743"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="c1bd7-102">Método ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="c1bd7-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="c1bd7-103">Retorna um enumerador que fornece métodos para iterar em sequência por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1bd7-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1bd7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1bd7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1bd7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1bd7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c1bd7-106">fora Um ponteiro para uma interface [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c1bd7-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1bd7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1bd7-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1bd7-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c1bd7-108">Requirements</span></span>  
 <span data-ttu-id="c1bd7-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1bd7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1bd7-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c1bd7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1bd7-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1bd7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1bd7-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1bd7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1bd7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1bd7-113">See also</span></span>

- [<span data-ttu-id="c1bd7-114">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="c1bd7-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c1bd7-115">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c1bd7-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c1bd7-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c1bd7-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c1bd7-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c1bd7-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
