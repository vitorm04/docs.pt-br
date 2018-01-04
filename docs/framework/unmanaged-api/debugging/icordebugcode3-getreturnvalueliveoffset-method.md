---
title: "Método ICorDebugCode3::GetReturnValueLiveOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d10d298a031e7146eaf6cf7988538e6f7020136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="b929b-102">Método ICorDebugCode3::GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="b929b-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="b929b-103">Para um deslocamento de IL especificado, obtém os deslocamentos nativo onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="b929b-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b929b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b929b-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b929b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b929b-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="b929b-106">O deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="b929b-106">The IL offset.</span></span> <span data-ttu-id="b929b-107">Ele deve ser um site de chamada de função ou a chamada de função falhará.</span><span class="sxs-lookup"><span data-stu-id="b929b-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="b929b-108">O número de bytes disponíveis para armazenar `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="b929b-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="b929b-109">Um ponteiro para o número de deslocamentos de fato retornadas.</span><span class="sxs-lookup"><span data-stu-id="b929b-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="b929b-110">Geralmente, seu valor é 1, mas uma única instrução IL pode mapear vários `CALL` instruções de assembly.</span><span class="sxs-lookup"><span data-stu-id="b929b-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="b929b-111">Uma matriz de deslocamentos nativo.</span><span class="sxs-lookup"><span data-stu-id="b929b-111">An array of native offsets.</span></span> <span data-ttu-id="b929b-112">Normalmente, `pOffsets` contém um desvio único, embora uma única instrução IL pode mapear para mapear vários para vários `CALL` instruções de assembly.</span><span class="sxs-lookup"><span data-stu-id="b929b-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b929b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b929b-113">Remarks</span></span>  
 <span data-ttu-id="b929b-114">Esse método é usado junto com o [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno de um método que retorna um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="b929b-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="b929b-115">Passar um deslocamento para um site de chamada de função para este método de IL retorna um ou mais deslocamentos nativo.</span><span class="sxs-lookup"><span data-stu-id="b929b-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="b929b-116">O depurador pode definir pontos de interrupção nesses deslocamentos nativo na função.</span><span class="sxs-lookup"><span data-stu-id="b929b-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="b929b-117">Quando o depurador atingirá um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para este método para o [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b929b-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="b929b-118">O depurador deve, em seguida, desmarque todos os pontos de interrupção que ele definiu.</span><span class="sxs-lookup"><span data-stu-id="b929b-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b929b-119">O `ICorDebugCode3::GetReturnValueLiveOffset` e [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) métodos permitem que você obtenha informações do valor de retorno para somente tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="b929b-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="b929b-120">Recuperando informações de valor de retorno dos tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>) não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="b929b-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="b929b-121">A função retorna o `HRESULT` valores mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b929b-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="b929b-122">Valor `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="b929b-122">`HRESULT` value</span></span>|<span data-ttu-id="b929b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b929b-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="b929b-124">Êxito.</span><span class="sxs-lookup"><span data-stu-id="b929b-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="b929b-125">No site de deslocamento de IL especificado não é uma instrução de chamada ou a função retornará `void`.</span><span class="sxs-lookup"><span data-stu-id="b929b-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="b929b-126">O deslocamento de IL fornecido é uma chamada correta, mas o tipo de retorno não tem suporte para obter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b929b-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="b929b-127">O `ICorDebugCode3::GetReturnValueLiveOffset` método está disponível apenas em baseados em x86 e sistemas AMD64.</span><span class="sxs-lookup"><span data-stu-id="b929b-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b929b-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b929b-128">Requirements</span></span>  
 <span data-ttu-id="b929b-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b929b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b929b-130">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b929b-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b929b-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b929b-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b929b-132">**Versões do .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b929b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b929b-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b929b-133">See Also</span></span>  
 [<span data-ttu-id="b929b-134">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="b929b-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [<span data-ttu-id="b929b-135">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="b929b-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
