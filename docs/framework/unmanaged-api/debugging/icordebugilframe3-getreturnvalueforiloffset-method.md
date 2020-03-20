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
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178808"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="abe9b-102">Método ICorDebugILFrame3::GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="abe9b-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="abe9b-103">Obtém um objeto "ICorDebugValue" que encapsula o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="abe9b-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abe9b-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe9b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="abe9b-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="abe9b-106">O deslocamento do IL.</span><span class="sxs-lookup"><span data-stu-id="abe9b-106">The IL offset.</span></span> <span data-ttu-id="abe9b-107">Consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="abe9b-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="abe9b-108">Um ponteiro para o endereço de um objeto de interface "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="abe9b-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abe9b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="abe9b-109">Remarks</span></span>  
 <span data-ttu-id="abe9b-110">Este método é usado juntamente com o método [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) para obter o valor de retorno de um método.</span><span class="sxs-lookup"><span data-stu-id="abe9b-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="abe9b-111">É particularmente útil no caso de métodos cujos valores de retorno são ignorados, como nos dois exemplos de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="abe9b-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="abe9b-112">O primeiro exemplo <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> chama o método, mas ignora o valor de retorno do método.</span><span class="sxs-lookup"><span data-stu-id="abe9b-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="abe9b-113">O segundo exemplo ilustra um problema muito mais comum na depuração.</span><span class="sxs-lookup"><span data-stu-id="abe9b-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="abe9b-114">Como um método é usado como argumento em uma chamada de método, seu valor de retorno só é acessível quando o depurador passa pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="abe9b-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="abe9b-115">Em muitos casos, particularmente quando o chamado método é definido em uma biblioteca externa, isso não é possível.</span><span class="sxs-lookup"><span data-stu-id="abe9b-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="abe9b-116">Se você passar pelo [método ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) um deslocamento il para um site de chamada de função, ele retorna um ou mais deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="abe9b-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="abe9b-117">O depurador pode, então, definir pontos de interrupção nesses deslocamentos nativos na função.</span><span class="sxs-lookup"><span data-stu-id="abe9b-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="abe9b-118">Quando o depurador atinge um dos pontos de interrupção, você pode então passar o mesmo deslocamento il que você passou para este método para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="abe9b-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="abe9b-119">O depurador deve então limpar todos os pontos de interrupção que ele definiu.</span><span class="sxs-lookup"><span data-stu-id="abe9b-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="abe9b-120">O Método e métodos [ICorDebugCode3:GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) e `ICorDebugILFrame3::GetReturnValueForILOffset` os métodos permitem obter informações de valor de retorno apenas para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="abe9b-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="abe9b-121">A recuperação de informações de valor de retorno de <xref:System.ValueType>tipos de valor (ou seja, todos os tipos que derivam ) não é suportada.</span><span class="sxs-lookup"><span data-stu-id="abe9b-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="abe9b-122">O deslocamento DE IL `ILOffset` especificado pelo parâmetro deve estar em um local de chamada de função, e a depuração deve ser interrompida em um ponto de ruptura definido no deslocamento nativo retornado pelo método [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) para o mesmo deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="abe9b-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="abe9b-123">Se a depuração não for interrompida no local correto para a compensação IL especificada, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="abe9b-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="abe9b-124">Se a chamada de função não retornar um valor, a API falhará.</span><span class="sxs-lookup"><span data-stu-id="abe9b-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="abe9b-125">O `ICorDebugILFrame3::GetReturnValueForILOffset` método está disponível apenas nos sistemas x86 e AMD64.</span><span class="sxs-lookup"><span data-stu-id="abe9b-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe9b-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abe9b-126">Requirements</span></span>  
 <span data-ttu-id="abe9b-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe9b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe9b-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abe9b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abe9b-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe9b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe9b-130">**.NET Framework Versions:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe9b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe9b-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="abe9b-131">See also</span></span>

- [<span data-ttu-id="abe9b-132">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="abe9b-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="abe9b-133">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="abe9b-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
