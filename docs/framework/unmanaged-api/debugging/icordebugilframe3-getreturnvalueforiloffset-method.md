---
title: Método ICorDebugILFrame3::GetReturnValueForILOffset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5832ec095ea0e96327f6a9636193da9c0c8a5dd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988259"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="517d1-102">Método ICorDebugILFrame3::GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="517d1-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="517d1-103">Obtém um objeto "ICorDebugValue" que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="517d1-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="517d1-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="517d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="517d1-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="517d1-106">O deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="517d1-106">The IL offset.</span></span> <span data-ttu-id="517d1-107">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="517d1-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="517d1-108">Um ponteiro para o endereço de um objeto de interface "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="517d1-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="517d1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="517d1-109">Remarks</span></span>  
 <span data-ttu-id="517d1-110">Esse método é usado junto com o método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) para obter o valor de retorno de um método.</span><span class="sxs-lookup"><span data-stu-id="517d1-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="517d1-111">Ele é particularmente útil no caso de métodos cujos valores de retorno são ignorados, como nos dois exemplos de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="517d1-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="517d1-112">O primeiro exemplo chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método, mas ignora o valor de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="517d1-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="517d1-113">O segundo exemplo ilustra um problema muito mais comum na depuração.</span><span class="sxs-lookup"><span data-stu-id="517d1-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="517d1-114">Como um método é usado como um argumento em uma chamada de método, seu valor de retorno é acessível somente quando o depurador percorre o método chamado.</span><span class="sxs-lookup"><span data-stu-id="517d1-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="517d1-115">Em muitos casos, particularmente quando o método chamado é definido em uma biblioteca externa, isso não é possível.</span><span class="sxs-lookup"><span data-stu-id="517d1-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="517d1-116">Se você passar o método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) de um deslocamento IL para um site de chamada de função, ele retornará um ou mais deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="517d1-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="517d1-117">O depurador pode então definir pontos de interrupção nesses deslocamentos nativos na função.</span><span class="sxs-lookup"><span data-stu-id="517d1-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="517d1-118">Quando o depurador atinge um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para esse método para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="517d1-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="517d1-119">O depurador deve limpar todos os pontos de interrupção definidos por ele.</span><span class="sxs-lookup"><span data-stu-id="517d1-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="517d1-120">O [método ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) e `ICorDebugILFrame3::GetReturnValueForILOffset` os métodos permitem obter informações de valor de retorno somente para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="517d1-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="517d1-121">Não há suporte para a recuperação de informações de valor de retorno de tipos de valor ( <xref:System.ValueType>ou seja, todos os tipos que derivam de).</span><span class="sxs-lookup"><span data-stu-id="517d1-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="517d1-122">O deslocamento de Il especificado pelo `ILOffset` parâmetro deve estar em um site de chamada de função e o depurado deve ser interrompido em um ponto de interrupção definido no deslocamento nativo retornado pelo método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) para o mesmo deslocamento de Il.</span><span class="sxs-lookup"><span data-stu-id="517d1-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="517d1-123">Se o depurador não for interrompido no local correto para o deslocamento IL especificado, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="517d1-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="517d1-124">Se a chamada de função não retornar um valor, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="517d1-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="517d1-125">O `ICorDebugILFrame3::GetReturnValueForILOffset` método está disponível apenas em sistemas baseados em x86 e amd64.</span><span class="sxs-lookup"><span data-stu-id="517d1-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="517d1-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="517d1-126">Requirements</span></span>  
 <span data-ttu-id="517d1-127">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="517d1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="517d1-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="517d1-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="517d1-129">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="517d1-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="517d1-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="517d1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517d1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="517d1-131">See also</span></span>

- [<span data-ttu-id="517d1-132">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="517d1-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="517d1-133">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="517d1-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
