---
title: Método ICorDebugCode3::GetReturnValueLiveOffset
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178947"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="f122f-102">Método ICorDebugCode3::GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="f122f-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="f122f-103">Para uma compensação IL especificada, obtém as compensações nativas onde um ponto de ruptura deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="f122f-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f122f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f122f-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f122f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f122f-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="f122f-106">O deslocamento do IL.</span><span class="sxs-lookup"><span data-stu-id="f122f-106">The IL offset.</span></span> <span data-ttu-id="f122f-107">Deve ser um local de chamada de função ou a chamada da função falhará.</span><span class="sxs-lookup"><span data-stu-id="f122f-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="f122f-108">O número de bytes `pOffsets`disponíveis para armazenar .</span><span class="sxs-lookup"><span data-stu-id="f122f-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="f122f-109">Um ponteiro para o número de deslocamentos realmente retornou.</span><span class="sxs-lookup"><span data-stu-id="f122f-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="f122f-110">Normalmente, seu valor é 1, mas uma `CALL` única instrução il pode mapear para várias instruções de montagem.</span><span class="sxs-lookup"><span data-stu-id="f122f-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="f122f-111">Uma série de deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="f122f-111">An array of native offsets.</span></span> <span data-ttu-id="f122f-112">Normalmente, `pOffsets` contém um único deslocamento, embora uma única instrução il possa mapear para vários mapas para várias `CALL` instruções de montagem.</span><span class="sxs-lookup"><span data-stu-id="f122f-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f122f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f122f-113">Remarks</span></span>  
 <span data-ttu-id="f122f-114">Este método é usado juntamente com o método [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno de um método que retorna um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="f122f-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="f122f-115">Passar um deslocamento de IL para um local de chamada de função para este método retorna um ou mais deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="f122f-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="f122f-116">O depurador pode, então, definir pontos de interrupção nesses deslocamentos nativos na função.</span><span class="sxs-lookup"><span data-stu-id="f122f-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="f122f-117">Quando o depurador atinge um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL que você passou para este método para o método [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="f122f-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="f122f-118">O depurador deve então limpar todos os pontos de interrupção que ele definiu.</span><span class="sxs-lookup"><span data-stu-id="f122f-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f122f-119">Os `ICorDebugCode3::GetReturnValueLiveOffset` métodos [ICorDebugILFrame3:GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) permitem que você obtenha informações de valor de retorno apenas para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="f122f-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="f122f-120">A recuperação de informações de valor de retorno de <xref:System.ValueType>tipos de valor (ou seja, todos os tipos que derivam ) não é suportada.</span><span class="sxs-lookup"><span data-stu-id="f122f-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="f122f-121">A função `HRESULT` retorna os valores mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f122f-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="f122f-122">`HRESULT` valor</span><span class="sxs-lookup"><span data-stu-id="f122f-122">`HRESULT` value</span></span>|<span data-ttu-id="f122f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f122f-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="f122f-124">Sucesso.</span><span class="sxs-lookup"><span data-stu-id="f122f-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="f122f-125">O site de deslocamento il dado não `void`é uma instrução de chamada, ou a função retorna .</span><span class="sxs-lookup"><span data-stu-id="f122f-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="f122f-126">O deslocamento de IL dado é uma chamada adequada, mas o tipo de retorno não é suportado para obter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="f122f-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="f122f-127">O `ICorDebugCode3::GetReturnValueLiveOffset` método está disponível apenas nos sistemas x86 e AMD64.</span><span class="sxs-lookup"><span data-stu-id="f122f-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f122f-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f122f-128">Requirements</span></span>  
 <span data-ttu-id="f122f-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f122f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f122f-130">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f122f-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f122f-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f122f-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f122f-132">**.NET Framework Versions:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f122f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f122f-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="f122f-133">See also</span></span>

- [<span data-ttu-id="f122f-134">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="f122f-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="f122f-135">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="f122f-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
