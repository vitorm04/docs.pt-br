---
title: Método ICorDebugCode::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178994"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="6c407-102">Método ICorDebugCode::GetCode</span><span class="sxs-lookup"><span data-stu-id="6c407-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="6c407-103">Obtém todo o código para a função especificada, formatado para desmontagem.</span><span class="sxs-lookup"><span data-stu-id="6c407-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="6c407-104">Este método foi preterido na versão 2.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c407-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6c407-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6c407-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c407-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c407-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c407-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c407-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="6c407-108">[em] O deslocamento do início da função.</span><span class="sxs-lookup"><span data-stu-id="6c407-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="6c407-109">[em] O deslocamento do fim da função.</span><span class="sxs-lookup"><span data-stu-id="6c407-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="6c407-110">[em] O tamanho `buffer` da matriz para a qual o código será devolvido.</span><span class="sxs-lookup"><span data-stu-id="6c407-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="6c407-111">[fora] A matriz na qual o código será devolvido.</span><span class="sxs-lookup"><span data-stu-id="6c407-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="6c407-112">[fora] O número de bytes retornou.</span><span class="sxs-lookup"><span data-stu-id="6c407-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c407-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c407-113">Remarks</span></span>  
 <span data-ttu-id="6c407-114">Se o código da função foi dividido em vários pedaços, eles são concatenados para aumentar o deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="6c407-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="6c407-115">Os limites da instrução não são verificados.</span><span class="sxs-lookup"><span data-stu-id="6c407-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c407-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c407-116">Requirements</span></span>  
 <span data-ttu-id="6c407-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c407-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c407-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c407-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c407-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c407-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c407-120">**.NET Framework Versões:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="6c407-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c407-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c407-121">See also</span></span>

- [<span data-ttu-id="6c407-122">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="6c407-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
