---
title: Método ICorDebugNativeFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096747"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="01ad2-102">Método ICorDebugNativeFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="01ad2-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="01ad2-103">Define o ponteiro de instrução para o local de deslocamento especificado no código nativo.</span><span class="sxs-lookup"><span data-stu-id="01ad2-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ad2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01ad2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ad2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01ad2-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="01ad2-106">no O local de deslocamento no código nativo.</span><span class="sxs-lookup"><span data-stu-id="01ad2-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ad2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="01ad2-107">Remarks</span></span>  
 <span data-ttu-id="01ad2-108">As chamadas para `SetIP` invalidam imediatamente todos os quadros e cadeias para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="01ad2-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="01ad2-109">Se o depurador precisar de informações de quadro após uma chamada para `SetIP`, ele deverá executar um novo rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="01ad2-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="01ad2-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) tentará manter o quadro de pilha em um estado válido.</span><span class="sxs-lookup"><span data-stu-id="01ad2-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="01ad2-111">No entanto, mesmo que o quadro esteja em um estado válido, no que diz respeito ao tempo de execução, ainda pode haver problemas, como variáveis locais não inicializadas e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="01ad2-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="01ad2-112">O chamador é responsável por garantir a coerência do programa em execução.</span><span class="sxs-lookup"><span data-stu-id="01ad2-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="01ad2-113">Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido para fora de um `catch` ou de um bloco de `finally`.</span><span class="sxs-lookup"><span data-stu-id="01ad2-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="01ad2-114">Se `SetIP` for chamado para fazer essa movimentação em uma plataforma de 64 bits, ele retornará um HRESULT indicando falha.</span><span class="sxs-lookup"><span data-stu-id="01ad2-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ad2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01ad2-115">Requirements</span></span>  
 <span data-ttu-id="01ad2-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ad2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ad2-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01ad2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01ad2-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01ad2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01ad2-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ad2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ad2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01ad2-120">See also</span></span>
