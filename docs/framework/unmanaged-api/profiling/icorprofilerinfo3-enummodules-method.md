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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be5d05c34272b9fa5755b4d0e22fa9094707c5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703550"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="f11d0-102">Método ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="f11d0-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="f11d0-103">Retorna um enumerador que fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f11d0-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f11d0-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f11d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f11d0-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f11d0-106">[out] Um ponteiro para um [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f11d0-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f11d0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f11d0-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11d0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f11d0-108">Requirements</span></span>  
 <span data-ttu-id="f11d0-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f11d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11d0-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f11d0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f11d0-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f11d0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f11d0-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11d0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f11d0-113">See also</span></span>

- [<span data-ttu-id="f11d0-114">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="f11d0-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f11d0-115">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="f11d0-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f11d0-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f11d0-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f11d0-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f11d0-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
