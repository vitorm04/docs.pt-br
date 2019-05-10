---
title: Estrutura COR_PRF_EX_CLAUSE_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 148ca261e717b9a54192a13c317fe385b98f4ccd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651157"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="b63ae-102">Estrutura COR_PRF_EX_CLAUSE_INFO</span><span class="sxs-lookup"><span data-stu-id="b63ae-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="b63ae-103">Armazena informações sobre uma instância de cláusula de exceção específica e seu quadro associado.</span><span class="sxs-lookup"><span data-stu-id="b63ae-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b63ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b63ae-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b63ae-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b63ae-105">Members</span></span>  
  
|<span data-ttu-id="b63ae-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b63ae-106">Member</span></span>|<span data-ttu-id="b63ae-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b63ae-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="b63ae-108">Um valor igual a [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeração que especifica o tipo de cláusula de exceção o código que acabou de inserir ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b63ae-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="b63ae-109">O ponto de entrada nativo do manipulador de cláusula — por exemplo, o conteúdo do registro X86 EIP.</span><span class="sxs-lookup"><span data-stu-id="b63ae-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="b63ae-110">O ponteiro para o quadro de lógico para o manipulador de cláusula — por exemplo, o conteúdo do registro X86 EBP.</span><span class="sxs-lookup"><span data-stu-id="b63ae-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="b63ae-111">O ponteiro para a pilha de sombra.</span><span class="sxs-lookup"><span data-stu-id="b63ae-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="b63ae-112">Esse valor é o conteúdo do registro BSP e só se aplica a IA64.</span><span class="sxs-lookup"><span data-stu-id="b63ae-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b63ae-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b63ae-113">Remarks</span></span>  
 <span data-ttu-id="b63ae-114">Quando uma notificação de exceção é recebida, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) pode ser usado para obter as informações de endereço e o quadro nativas para a cláusula de exceção (`catch` / `finally`/filtro) que está prestes a ser executado ou foi executado.</span><span class="sxs-lookup"><span data-stu-id="b63ae-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="b63ae-115">Esses retornos de chamada do common language runtime (CLR) envolve a execução de uma cláusula de exceção:</span><span class="sxs-lookup"><span data-stu-id="b63ae-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="b63ae-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="b63ae-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="b63ae-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="b63ae-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="b63ae-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="b63ae-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="b63ae-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="b63ae-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="b63ae-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="b63ae-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="b63ae-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="b63ae-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="b63ae-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b63ae-122">Requirements</span></span>  
 <span data-ttu-id="b63ae-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b63ae-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b63ae-124">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b63ae-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b63ae-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b63ae-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b63ae-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b63ae-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63ae-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b63ae-127">See also</span></span>

- [<span data-ttu-id="b63ae-128">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b63ae-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
