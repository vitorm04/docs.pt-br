---
title: Método ICorProfilerCallback::JITInlining
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500007"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="c4573-102">Método ICorProfilerCallback::JITInlining</span><span class="sxs-lookup"><span data-stu-id="c4573-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="c4573-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) está prestes a inserir uma função em linha com outra função.</span><span class="sxs-lookup"><span data-stu-id="c4573-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4573-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4573-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4573-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4573-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="c4573-106">no A ID da função na qual a `calleeId` função será inserida.</span><span class="sxs-lookup"><span data-stu-id="c4573-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="c4573-107">no A ID da função a ser inserida.</span><span class="sxs-lookup"><span data-stu-id="c4573-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="c4573-108">[fora] `true` para permitir que a inserção ocorra; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="c4573-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4573-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4573-109">Remarks</span></span>  
 <span data-ttu-id="c4573-110">O criador de perfil pode definir `pfShouldInline` como `false` para impedir que a `calleeId` função seja inserida na `callerId` função.</span><span class="sxs-lookup"><span data-stu-id="c4573-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="c4573-111">Além disso, o criador de perfil pode desabilitar a inserção embutida globalmente usando o valor COR_PRF_DISABLE_INLINING da enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c4573-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="c4573-112">Funções inseridas embutidas não geram eventos para entrar ou sair.</span><span class="sxs-lookup"><span data-stu-id="c4573-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="c4573-113">Portanto, o criador de perfil deve definir `pfShouldInline` como para `false` produzir um chamadas preciso.</span><span class="sxs-lookup"><span data-stu-id="c4573-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="c4573-114">`pfShouldInline`A configuração para `false` afetará o desempenho, pois a inserção embutida normalmente aumenta a velocidade e reduz o número de eventos de compilação JIT separados para o método inserido.</span><span class="sxs-lookup"><span data-stu-id="c4573-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4573-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4573-115">Requirements</span></span>  
 <span data-ttu-id="c4573-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4573-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4573-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4573-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4573-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4573-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4573-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4573-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4573-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4573-120">See also</span></span>

- [<span data-ttu-id="c4573-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c4573-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
