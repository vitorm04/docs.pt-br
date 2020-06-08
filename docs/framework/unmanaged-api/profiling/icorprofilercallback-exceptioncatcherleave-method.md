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
ms.openlocfilehash: cff2dd9fdb05ea4dd160dfa57df6f047beb57f69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500293"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="d9662-102">Método ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="d9662-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="d9662-103">Notifica o criador de perfil que o controle está sendo passado para fora do `catch` bloco apropriado.</span><span class="sxs-lookup"><span data-stu-id="d9662-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9662-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9662-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9662-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9662-105">Remarks</span></span>  
 <span data-ttu-id="d9662-106">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="d9662-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d9662-107">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="d9662-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d9662-108">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="d9662-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9662-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9662-109">Requirements</span></span>  
 <span data-ttu-id="d9662-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9662-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9662-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d9662-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9662-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9662-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9662-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9662-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9662-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9662-114">See also</span></span>

- [<span data-ttu-id="d9662-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d9662-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d9662-116">Método ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="d9662-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
