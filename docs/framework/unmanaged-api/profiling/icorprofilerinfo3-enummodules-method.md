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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093872"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="9dd57-102">Método ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="9dd57-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="9dd57-103">Retorna um enumerador que fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9dd57-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd57-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9dd57-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dd57-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9dd57-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9dd57-106">[out] Um ponteiro para um [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9dd57-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dd57-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9dd57-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd57-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9dd57-108">Requirements</span></span>  
 <span data-ttu-id="9dd57-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd57-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd57-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9dd57-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9dd57-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dd57-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9dd57-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9dd57-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9dd57-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dd57-113">See also</span></span>

- [<span data-ttu-id="9dd57-114">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="9dd57-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="9dd57-115">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="9dd57-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9dd57-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="9dd57-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9dd57-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9dd57-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
