---
title: Método ICorProfilerCallback::ExceptionSearchCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 8f5997dddf78dd75d482bc45d2ee730b20d9ab16
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866462"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="1cc50-102">Método ICorProfilerCallback::ExceptionSearchCatcherFound</span><span class="sxs-lookup"><span data-stu-id="1cc50-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="1cc50-103">Notifica o criador de perfil de que a fase de pesquisa do tratamento de exceções localizou um manipulador para a exceção que foi lançada.</span><span class="sxs-lookup"><span data-stu-id="1cc50-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cc50-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cc50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cc50-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="1cc50-106">\[em] a ID da função que contém o manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="1cc50-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cc50-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1cc50-107">Requirements</span></span>  
 <span data-ttu-id="1cc50-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc50-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc50-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1cc50-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cc50-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cc50-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cc50-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc50-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc50-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="1cc50-112">See also</span></span>

- [<span data-ttu-id="1cc50-113">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1cc50-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
