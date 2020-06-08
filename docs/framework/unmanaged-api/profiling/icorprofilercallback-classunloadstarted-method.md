---
title: Método ICorProfilerCallback::ClassUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500345"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="09f0e-102">Método ICorProfilerCallback::ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="09f0e-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="09f0e-103">Notifica o criador de perfil de que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="09f0e-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09f0e-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09f0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09f0e-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="09f0e-106">\[in] identifica a classe que está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="09f0e-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="09f0e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="09f0e-107">Remarks</span></span>  
 <span data-ttu-id="09f0e-108">O valor de `classId` não é válido para uma solicitação de informações após o `ClassUnloadStarted` retorno do método — essa é a última chance do criador de perfil obter informações sobre essa classe.</span><span class="sxs-lookup"><span data-stu-id="09f0e-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f0e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09f0e-109">Requirements</span></span>  
 <span data-ttu-id="09f0e-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09f0e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f0e-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="09f0e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09f0e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09f0e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09f0e-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09f0e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f0e-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="09f0e-114">See also</span></span>

- [<span data-ttu-id="09f0e-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="09f0e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="09f0e-116">Método ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="09f0e-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
