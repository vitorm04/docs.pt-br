---
title: Método ICorProfilerFunctionEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 5ccd90e92e83d7f9f6f19a082fb84dc1f1c35f4c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447813"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="6222c-102">Método ICorProfilerFunctionEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="6222c-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="6222c-103">Obtém o número de funções que foram carregadas pelo aplicativo ou carregadas de modo forçado pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="6222c-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6222c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6222c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6222c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6222c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6222c-106">fora O número de funções que foram carregadas.</span><span class="sxs-lookup"><span data-stu-id="6222c-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6222c-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6222c-107">Requirements</span></span>  
 <span data-ttu-id="6222c-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6222c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6222c-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6222c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6222c-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6222c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6222c-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6222c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6222c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6222c-112">See also</span></span>

- [<span data-ttu-id="6222c-113">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="6222c-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="6222c-114">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6222c-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
