---
title: Método ICorDebugChain::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894679"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="d5d5b-102">Método ICorDebugChain::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="d5d5b-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="d5d5b-103">Obtém o quadro ativo (ou seja, mais recente) na cadeia.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5d5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5d5b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5d5b-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d5d5b-106">fora Um ponteiro para o endereço de um objeto ICorDebugFrame que representa o quadro ativo (ou seja, mais recente) na cadeia.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5d5b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5d5b-107">Remarks</span></span>  
 <span data-ttu-id="d5d5b-108">Se nenhum quadro de pilha gerenciado estiver disponível `ppFrame` , será definido como nulo.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="d5d5b-109">Se o quadro ativo não estiver disponível, a chamada terá sucesso e `ppFrame` será NULL.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="d5d5b-110">Os quadros ativos não estarão disponíveis para cadeias iniciadas devido a CHAIN_ENTER_UNMANAGED e para algumas cadeias iniciadas devido a CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="d5d5b-111">Consulte a enumeração CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="d5d5b-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d5b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5d5b-112">Requirements</span></span>  
 <span data-ttu-id="d5d5b-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d5b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d5b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5d5b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5d5b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5d5b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5d5b-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
