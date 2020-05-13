---
title: Método ICorDebugILFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 325b2a009e77d87e95bdb02803dd3c4675c26ddc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213420"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="789da-102">Método ICorDebugILFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="789da-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="789da-103">Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="789da-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="789da-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="789da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="789da-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="789da-106">O local de deslocamento no código MSIL.</span><span class="sxs-lookup"><span data-stu-id="789da-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="789da-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="789da-107">Remarks</span></span>  
 <span data-ttu-id="789da-108">As chamadas para `SetIP` invalidar imediatamente todos os quadros e cadeias para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="789da-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="789da-109">Se o depurador precisar de informações de quadro após uma chamada para `SetIP` , ele deverá executar um novo rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="789da-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="789da-110">[ICorDebug](icordebug-interface.md) tentará manter o quadro de pilha em um estado válido.</span><span class="sxs-lookup"><span data-stu-id="789da-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="789da-111">No entanto, mesmo que o quadro esteja em um estado válido, ainda pode haver problemas como variáveis locais não inicializadas.</span><span class="sxs-lookup"><span data-stu-id="789da-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="789da-112">O chamador é responsável por garantir a coerência do programa em execução.</span><span class="sxs-lookup"><span data-stu-id="789da-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="789da-113">Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido para fora de um `catch` `finally` bloco ou.</span><span class="sxs-lookup"><span data-stu-id="789da-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="789da-114">Se `SetIP` for chamado para fazer uma movimentação desse tipo em uma plataforma de 64 bits, ele retornará um HRESULT indicando falha.</span><span class="sxs-lookup"><span data-stu-id="789da-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="789da-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="789da-115">Requirements</span></span>  
 <span data-ttu-id="789da-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="789da-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="789da-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="789da-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="789da-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="789da-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="789da-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="789da-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
