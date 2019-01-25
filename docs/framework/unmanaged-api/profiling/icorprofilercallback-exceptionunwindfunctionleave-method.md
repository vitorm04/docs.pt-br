---
title: Método ICorProfilerCallback::ExceptionUnwindFunctionLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e945cad9080d14fff0b0a95c4e4d5f13981b1b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582256"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="a3aaf-102">Método ICorProfilerCallback::ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="a3aaf-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="a3aaf-103">Notifica o criador de perfil que a fase de desenrolamento de tratamento de exceções terminou o desenrolamento de uma função.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3aaf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3aaf-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3aaf-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3aaf-105">Remarks</span></span>  
 <span data-ttu-id="a3aaf-106">Quando o `ExceptionUnwindFunctionLeave` método é chamado, a instância de função e seus dados de pilha são removidos da pilha.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="a3aaf-107">O criador de perfil não deve bloquear durante esta chamada porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="a3aaf-108">Se você tentar aqui os blocos do criador de perfil e uma coleta de lixo, o tempo de execução bloqueará até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="a3aaf-109">Além disso, durante esta chamada, o criador de perfil não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a3aaf-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3aaf-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3aaf-110">Requirements</span></span>  
 <span data-ttu-id="a3aaf-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3aaf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3aaf-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3aaf-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3aaf-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3aaf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3aaf-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3aaf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3aaf-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3aaf-115">See also</span></span>
- [<span data-ttu-id="a3aaf-116">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a3aaf-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a3aaf-117">Método ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="a3aaf-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
