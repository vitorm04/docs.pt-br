---
title: "Método ICorDebugILFrame2::RemapFunction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4def20bc51d1b01b1c05b81a89fc3c983b4d1219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="b79c5-102">Método ICorDebugILFrame2::RemapFunction</span><span class="sxs-lookup"><span data-stu-id="b79c5-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="b79c5-103">Remapeia uma função editada, especificando o novo deslocamento de linguagem intermediária (MSIL) Microsoft</span><span class="sxs-lookup"><span data-stu-id="b79c5-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b79c5-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b79c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b79c5-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="b79c5-106">[in] Novo MSIL deslocamento do quadro de pilhas em que o ponteiro de instrução deve ser colocado.</span><span class="sxs-lookup"><span data-stu-id="b79c5-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="b79c5-107">Esse valor deve ser um ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="b79c5-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="b79c5-108">É responsabilidade do chamador para garantir a validade do valor.</span><span class="sxs-lookup"><span data-stu-id="b79c5-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="b79c5-109">Por exemplo, o deslocamento do MSIL não é válido se ele está fora dos limites da função.</span><span class="sxs-lookup"><span data-stu-id="b79c5-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b79c5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b79c5-110">Remarks</span></span>  
 <span data-ttu-id="b79c5-111">Quando a função do quadro foi editada, o depurador pode chamar o `RemapFunction` método alternar a versão mais recente da função do quadro para que ele pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="b79c5-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="b79c5-112">A execução de código será iniciado em um deslocamento específico do MSIL.</span><span class="sxs-lookup"><span data-stu-id="b79c5-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b79c5-113">Chamando `RemapFunction`, como chamar [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), imediatamente invalidará todas as interfaces de depuração que estão relacionadas à geração de um rastreamento de pilha do thread.</span><span class="sxs-lookup"><span data-stu-id="b79c5-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="b79c5-114">Essas interfaces incluem [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame e ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="b79c5-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="b79c5-115">O `RemapFunction` método pode ser chamado somente no contexto do quadro atual e somente em um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="b79c5-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="b79c5-116">Após o recebimento de uma [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) retorno de chamada que não tenha sido continuado.</span><span class="sxs-lookup"><span data-stu-id="b79c5-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="b79c5-117">Enquanto a execução de código é interrompida por uma [: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) eventos para este quadro.</span><span class="sxs-lookup"><span data-stu-id="b79c5-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79c5-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b79c5-118">Requirements</span></span>  
 <span data-ttu-id="b79c5-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b79c5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b79c5-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b79c5-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b79c5-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b79c5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b79c5-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b79c5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
