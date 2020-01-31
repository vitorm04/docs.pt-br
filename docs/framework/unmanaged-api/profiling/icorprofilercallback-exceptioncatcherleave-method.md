---
title: Método ICorProfilerCallback::ExceptionCatcherLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: 6b7aa7c60b5e861787d7a115d90a00d67cc48db0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866527"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="c5ee0-102">Método ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="c5ee0-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="c5ee0-103">Notifica o criador de perfil que o controle está sendo passado do bloco de `catch` apropriado.</span><span class="sxs-lookup"><span data-stu-id="c5ee0-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ee0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5ee0-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5ee0-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5ee0-105">Remarks</span></span>  
 <span data-ttu-id="c5ee0-106">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="c5ee0-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c5ee0-107">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="c5ee0-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c5ee0-108">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="c5ee0-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ee0-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c5ee0-109">Requirements</span></span>  
 <span data-ttu-id="c5ee0-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5ee0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5ee0-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c5ee0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5ee0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5ee0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5ee0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ee0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ee0-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="c5ee0-114">See also</span></span>

- [<span data-ttu-id="c5ee0-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c5ee0-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c5ee0-116">Método ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="c5ee0-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
