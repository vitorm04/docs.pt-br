---
title: Interface ICorDebugCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893464"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="855d5-102">Interface ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="855d5-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="855d5-103">Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.</span><span class="sxs-lookup"><span data-stu-id="855d5-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="855d5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="855d5-104">Methods</span></span>  
  
|<span data-ttu-id="855d5-105">Método</span><span class="sxs-lookup"><span data-stu-id="855d5-105">Method</span></span>|<span data-ttu-id="855d5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="855d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="855d5-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="855d5-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="855d5-108">Cria um ponto de interrupção no deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="855d5-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="855d5-109">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="855d5-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="855d5-110">Obtém o endereço virtual relativo (RVA) do segmento de código que isso `ICorDebugCode` representa.</span><span class="sxs-lookup"><span data-stu-id="855d5-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="855d5-111">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="855d5-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="855d5-112">Obtém todo o código para a função especificada, formatado para desmontagem.</span><span class="sxs-lookup"><span data-stu-id="855d5-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="855d5-113">Esse método foi preterido; Use [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="855d5-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="855d5-114">Método GetEnCRemapSequencePoints</span><span class="sxs-lookup"><span data-stu-id="855d5-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="855d5-115">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="855d5-115">Not implemented.</span></span>|  
|[<span data-ttu-id="855d5-116">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="855d5-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="855d5-117">Obtém o "ICorDebugFunction" associado a isso `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="855d5-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="855d5-118">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="855d5-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="855d5-119">Obtém uma matriz de instâncias "COR_DEBUG_IL_TO_NATIVE_MAP" que representam mapeamentos de deslocamentos MSIL para deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="855d5-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="855d5-120">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="855d5-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="855d5-121">Obtém o tamanho, em bytes, do código binário representado por isso `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="855d5-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="855d5-122">Método GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="855d5-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="855d5-123">Obtém o número baseado em um que identifica a versão do código que `ICorDebugCode` representa.</span><span class="sxs-lookup"><span data-stu-id="855d5-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="855d5-124">Método IsIL</span><span class="sxs-lookup"><span data-stu-id="855d5-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="855d5-125">Obtém um valor que indica se isso `ICorDebugCode` é compilado em MSIL.</span><span class="sxs-lookup"><span data-stu-id="855d5-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="855d5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="855d5-126">Remarks</span></span>  
 <span data-ttu-id="855d5-127">`ICorDebugCode`pode representar o MSIL ou código nativo.</span><span class="sxs-lookup"><span data-stu-id="855d5-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="855d5-128">Um objeto "ICorDebugFunction" que representa o código MSIL pode ter zero ou um `ICorDebugCode` objetos associados a ele.</span><span class="sxs-lookup"><span data-stu-id="855d5-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="855d5-129">Um objeto "ICorDebugFunction" que representa o código nativo pode ter qualquer número `ICorDebugCode` de objetos associados a ele.</span><span class="sxs-lookup"><span data-stu-id="855d5-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="855d5-130">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="855d5-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="855d5-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="855d5-131">Requirements</span></span>  
 <span data-ttu-id="855d5-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="855d5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855d5-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="855d5-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="855d5-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="855d5-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="855d5-135">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855d5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855d5-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="855d5-136">See also</span></span>

- [<span data-ttu-id="855d5-137">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="855d5-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="855d5-138">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="855d5-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
