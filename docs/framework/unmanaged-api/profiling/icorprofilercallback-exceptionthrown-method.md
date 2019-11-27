---
title: Método ICorProfilerCallback::ExceptionThrown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 4ecbe0ef3c3021c5633b9380da2eb31cf22aa4b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445333"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="27940-102">Método ICorProfilerCallback::ExceptionThrown</span><span class="sxs-lookup"><span data-stu-id="27940-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="27940-103">Notifica o criador de perfil de que uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="27940-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27940-104">Essa função será chamada somente se a exceção atingir código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="27940-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27940-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27940-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27940-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27940-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="27940-107">no A ID do objeto que causou a exceção a ser gerada.</span><span class="sxs-lookup"><span data-stu-id="27940-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27940-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="27940-108">Remarks</span></span>  
 <span data-ttu-id="27940-109">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="27940-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="27940-110">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="27940-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="27940-111">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="27940-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27940-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="27940-112">Requirements</span></span>  
 <span data-ttu-id="27940-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27940-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27940-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="27940-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27940-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27940-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27940-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27940-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27940-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27940-117">See also</span></span>

- [<span data-ttu-id="27940-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="27940-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
