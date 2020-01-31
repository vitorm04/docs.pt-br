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
ms.openlocfilehash: dc03365b72a5f3613402faf1aed44b5683e9892c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777831"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="60a01-102">Método ICorDebugCode3::GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="60a01-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="60a01-103">Para um deslocamento de IL especificado, obtém os deslocamentos nativos onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="60a01-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60a01-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a01-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60a01-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="60a01-106">O deslocamento de IL.</span><span class="sxs-lookup"><span data-stu-id="60a01-106">The IL offset.</span></span> <span data-ttu-id="60a01-107">Ele deve ser um site de chamada de função ou a chamada de função falhará.</span><span class="sxs-lookup"><span data-stu-id="60a01-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="60a01-108">O número de bytes disponíveis para armazenar `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="60a01-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="60a01-109">Um ponteiro para o número de deslocamentos realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="60a01-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="60a01-110">Normalmente, seu valor é 1, mas uma única instrução IL pode ser mapeada para várias instruções de assembly `CALL`.</span><span class="sxs-lookup"><span data-stu-id="60a01-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="60a01-111">Uma matriz de deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="60a01-111">An array of native offsets.</span></span> <span data-ttu-id="60a01-112">Normalmente, `pOffsets` contém um único deslocamento, embora uma única instrução IL possa ser mapeada para vários mapas para várias instruções de assembly `CALL`.</span><span class="sxs-lookup"><span data-stu-id="60a01-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a01-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="60a01-113">Remarks</span></span>  
 <span data-ttu-id="60a01-114">Esse método é usado junto com o método [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno de um método que retorna um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="60a01-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="60a01-115">Passar um deslocamento de IL para um site de chamada de função para esse método retorna um ou mais deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="60a01-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="60a01-116">O depurador pode então definir pontos de interrupção nesses deslocamentos nativos na função.</span><span class="sxs-lookup"><span data-stu-id="60a01-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="60a01-117">Quando o depurador atinge um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para esse método para o método [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="60a01-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="60a01-118">O depurador deve limpar todos os pontos de interrupção definidos por ele.</span><span class="sxs-lookup"><span data-stu-id="60a01-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="60a01-119">Os métodos `ICorDebugCode3::GetReturnValueLiveOffset` e [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) permitem que você obtenha informações de valor de retorno somente para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="60a01-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="60a01-120">Não há suporte para a recuperação de informações de valor de retorno de tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>).</span><span class="sxs-lookup"><span data-stu-id="60a01-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="60a01-121">A função retorna os valores de `HRESULT` mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="60a01-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="60a01-122">Valor `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="60a01-122">`HRESULT` value</span></span>|<span data-ttu-id="60a01-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="60a01-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="60a01-124">Êxito.</span><span class="sxs-lookup"><span data-stu-id="60a01-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="60a01-125">O site de deslocamento de IL fornecido não é uma instrução de chamada ou a função retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="60a01-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="60a01-126">O deslocamento IL fornecido é uma chamada adequada, mas não há suporte para o tipo de retorno para obter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="60a01-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="60a01-127">O método `ICorDebugCode3::GetReturnValueLiveOffset` só está disponível em sistemas baseados em x86 e AMD64.</span><span class="sxs-lookup"><span data-stu-id="60a01-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a01-128">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="60a01-128">Requirements</span></span>  
 <span data-ttu-id="60a01-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a01-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a01-130">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60a01-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60a01-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60a01-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a01-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a01-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a01-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="60a01-133">See also</span></span>

- [<span data-ttu-id="60a01-134">Método GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="60a01-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="60a01-135">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="60a01-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
