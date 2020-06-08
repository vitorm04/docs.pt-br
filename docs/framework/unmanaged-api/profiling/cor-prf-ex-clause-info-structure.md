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
ms.openlocfilehash: 5c764031f709eefe61022d0662f37bc5d3f3e281
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500995"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="266d8-102">Estrutura COR_PRF_EX_CLAUSE_INFO</span><span class="sxs-lookup"><span data-stu-id="266d8-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="266d8-103">Armazena informações sobre uma instância de cláusula de exceção específica e seu quadro associado.</span><span class="sxs-lookup"><span data-stu-id="266d8-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="266d8-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="266d8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="266d8-105">Members</span></span>  
  
|<span data-ttu-id="266d8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="266d8-106">Member</span></span>|<span data-ttu-id="266d8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="266d8-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="266d8-108">Um valor da enumeração de [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) que especifica o tipo de cláusula de exceção que o código acabou de inserir ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="266d8-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="266d8-109">O ponto de entrada nativo do manipulador de cláusula — por exemplo, o conteúdo do registro de EIP x86.</span><span class="sxs-lookup"><span data-stu-id="266d8-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="266d8-110">O ponteiro para o quadro lógico para o manipulador de cláusula — por exemplo, o conteúdo do Registro EBP x86.</span><span class="sxs-lookup"><span data-stu-id="266d8-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="266d8-111">O ponteiro para a pilha de sombra.</span><span class="sxs-lookup"><span data-stu-id="266d8-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="266d8-112">Esse valor é o conteúdo do registro BSP e se aplica somente a IA64.</span><span class="sxs-lookup"><span data-stu-id="266d8-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="266d8-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="266d8-113">Remarks</span></span>  
 <span data-ttu-id="266d8-114">Quando uma notificação de exceção é recebida, [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) pode ser usado para obter as informações de endereço nativo e quadro da cláusula de exceção ( `catch` / `finally` /Filter) que está prestes a ser executada ou que acabou de ser executada.</span><span class="sxs-lookup"><span data-stu-id="266d8-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="266d8-115">A execução de uma cláusula de exceção envolve esses retornos de chamada do Common Language Runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="266d8-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="266d8-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="266d8-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="266d8-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="266d8-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="266d8-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="266d8-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="266d8-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="266d8-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="266d8-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="266d8-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="266d8-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="266d8-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="266d8-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="266d8-122">Requirements</span></span>  
 <span data-ttu-id="266d8-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="266d8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="266d8-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="266d8-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="266d8-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="266d8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="266d8-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="266d8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266d8-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="266d8-127">See also</span></span>

- [<span data-ttu-id="266d8-128">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="266d8-128">Profiling Structures</span></span>](profiling-structures.md)
