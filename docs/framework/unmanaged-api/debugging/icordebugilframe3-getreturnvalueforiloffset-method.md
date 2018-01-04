---
title: "Método ICorDebugILFrame3::GetReturnValueForILOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="4b66a-102">Método ICorDebugILFrame3::GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="4b66a-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="4b66a-103">Obtém um objeto de "ICorDebugValue" que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="4b66a-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b66a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b66a-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b66a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b66a-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="4b66a-106">O deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="4b66a-106">The IL offset.</span></span> <span data-ttu-id="4b66a-107">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="4b66a-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="4b66a-108">Um ponteiro para o endereço de um objeto de interface de "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="4b66a-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b66a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b66a-109">Remarks</span></span>  
 <span data-ttu-id="4b66a-110">Esse método é usado junto com o [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método para obter o valor de retorno de um método.</span><span class="sxs-lookup"><span data-stu-id="4b66a-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="4b66a-111">Isso é especialmente útil no caso de métodos cujos valores de retorno são ignorados, como os seguir dois exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="4b66a-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="4b66a-112">O primeiro exemplo chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método, mas ignora o valor de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="4b66a-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="4b66a-113">O segundo exemplo ilustra um problema muito mais comuns na depuração.</span><span class="sxs-lookup"><span data-stu-id="4b66a-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="4b66a-114">Como um método é usado como um argumento em uma chamada de método, o valor de retorno é acessível somente quando o depurador percorre o método chamado.</span><span class="sxs-lookup"><span data-stu-id="4b66a-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="4b66a-115">Em muitos casos, especialmente quando o método chamado é definido em uma biblioteca externa, que não é possível.</span><span class="sxs-lookup"><span data-stu-id="4b66a-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="4b66a-116">Se você passar o [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método um deslocamento para um site de chamada de função de IL, retorna um ou mais deslocamentos nativo.</span><span class="sxs-lookup"><span data-stu-id="4b66a-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="4b66a-117">O depurador pode definir pontos de interrupção nesses deslocamentos nativo na função.</span><span class="sxs-lookup"><span data-stu-id="4b66a-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="4b66a-118">Quando o depurador atingirá um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para este método para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="4b66a-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="4b66a-119">O depurador deve, em seguida, desmarque todos os pontos de interrupção que ele definiu.</span><span class="sxs-lookup"><span data-stu-id="4b66a-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4b66a-120">O [método Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) e `ICorDebugILFrame3::GetReturnValueForILOffset` métodos permitem que você obtenha informações do valor de retorno para somente tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="4b66a-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="4b66a-121">Recuperando informações de valor de retorno dos tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>) não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="4b66a-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="4b66a-122">O deslocamento de IL especificado pelo `ILOffset` parâmetro deve estar em um site de chamada de função e o depurador deve ser interrompido em um ponto de interrupção definido no deslocamento nativo retornado pelo [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método para o mesmo deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="4b66a-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="4b66a-123">Se o depurador não está parado no local correto para o deslocamento de IL especificado, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="4b66a-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="4b66a-124">Se a chamada de função não retorna um valor, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="4b66a-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="4b66a-125">O `ICorDebugILFrame3::GetReturnValueForILOffset` método está disponível apenas em baseados em x86 e sistemas AMD64.</span><span class="sxs-lookup"><span data-stu-id="4b66a-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b66a-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b66a-126">Requirements</span></span>  
 <span data-ttu-id="4b66a-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b66a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b66a-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b66a-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b66a-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b66a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b66a-130">**Versões do .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b66a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b66a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b66a-131">See Also</span></span>  
 [<span data-ttu-id="4b66a-132">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="4b66a-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="4b66a-133">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="4b66a-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
