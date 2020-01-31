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
ms.openlocfilehash: 8a21f1c0018e99b94a1b9910b6f266bdca84b7fe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864551"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="85d0f-102">Método ICorProfilerFunctionEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="85d0f-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="85d0f-103">Obtém o número de funções que foram carregadas pelo aplicativo ou carregadas de modo forçado pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="85d0f-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85d0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85d0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85d0f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="85d0f-106">fora O número de funções que foram carregadas.</span><span class="sxs-lookup"><span data-stu-id="85d0f-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d0f-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="85d0f-107">Requirements</span></span>  
 <span data-ttu-id="85d0f-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d0f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d0f-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="85d0f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85d0f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85d0f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85d0f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d0f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d0f-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="85d0f-112">See also</span></span>

- [<span data-ttu-id="85d0f-113">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="85d0f-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="85d0f-114">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="85d0f-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
