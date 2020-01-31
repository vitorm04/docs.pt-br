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
ms.openlocfilehash: 626ecddae8ba91d1830d98210208f9fbee36f073
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868580"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="e3eba-102">Método ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="e3eba-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="e3eba-103">Retorna um enumerador que fornece métodos para iterar em sequência por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3eba-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3eba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3eba-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3eba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3eba-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e3eba-106">fora Um ponteiro para uma interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e3eba-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3eba-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3eba-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3eba-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e3eba-108">Requirements</span></span>  
 <span data-ttu-id="e3eba-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3eba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3eba-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3eba-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3eba-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3eba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3eba-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3eba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3eba-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="e3eba-113">See also</span></span>

- [<span data-ttu-id="e3eba-114">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="e3eba-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="e3eba-115">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="e3eba-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e3eba-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e3eba-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e3eba-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e3eba-117">Profiling</span></span>](index.md)
