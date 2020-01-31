---
title: Função FunctionIDMapper2
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866912"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="91098-102">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="91098-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="91098-103">Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md)ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="91098-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="91098-104">`FunctionIDMapper2` também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="91098-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91098-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91098-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91098-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91098-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="91098-107">\[em] o identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="91098-107">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="91098-108">\[em] um ponteiro para dados que são usados para eliminar a ambiguidade entre tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="91098-108">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="91098-109">\[out] um ponteiro para um valor que o criador de perfil define para `true` se quiser receber `FunctionEnter3`retornos de chamada, `FunctionLeave3`e `FunctionTailcall3`, ou `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`e `FunctionTailcall3WithInfo`; caso contrário, ele definirá esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="91098-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="91098-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91098-110">Return Value</span></span>  
 <span data-ttu-id="91098-111">O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativo.</span><span class="sxs-lookup"><span data-stu-id="91098-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="91098-112">O valor de retorno não pode ser nulo, a menos que `false` seja retornado em `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="91098-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="91098-113">Caso contrário, um valor de retorno nulo produz resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="91098-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91098-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="91098-114">Remarks</span></span>  
 <span data-ttu-id="91098-115">Esse método estende a função [FunctionIDMapper](functionidmapper-function.md) com um parâmetro adicional que é usado para passar dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="91098-115">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="91098-116">Os dados do cliente são usados para fazer a ambiguidade entre tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="91098-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91098-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="91098-117">Requirements</span></span>  
 <span data-ttu-id="91098-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91098-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91098-119">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="91098-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="91098-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91098-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91098-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91098-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91098-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="91098-122">See also</span></span>

- [<span data-ttu-id="91098-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="91098-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="91098-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="91098-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="91098-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="91098-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="91098-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="91098-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="91098-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="91098-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="91098-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91098-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="91098-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91098-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="91098-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="91098-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="91098-131">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="91098-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
