---
title: Método ICorProfilerCallback::ExceptionSearchFilterLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: 607143d7848534329a55a9caebdb6b9175b2749c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866410"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="be06e-102">Método ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="be06e-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="be06e-103">Notifica o criador de perfil de que um filtro de usuário acabou de executar a execução.</span><span class="sxs-lookup"><span data-stu-id="be06e-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be06e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be06e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="be06e-105">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="be06e-105">Requirements</span></span>  
 <span data-ttu-id="be06e-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be06e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be06e-107">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="be06e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be06e-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be06e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be06e-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be06e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be06e-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="be06e-110">See also</span></span>

- [<span data-ttu-id="be06e-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="be06e-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="be06e-112">Método ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="be06e-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
