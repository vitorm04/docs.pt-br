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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645364"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="c83db-102">Método ICorDebugChain::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="c83db-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="c83db-103">Obtém o ativo (ou seja, mais recente) quadro da cadeia.</span><span class="sxs-lookup"><span data-stu-id="c83db-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c83db-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c83db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c83db-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c83db-106">[out] Um ponteiro para o endereço de um objeto ICorDebugFrame que representa o ativo (ou seja, mais recente) quadro da cadeia.</span><span class="sxs-lookup"><span data-stu-id="c83db-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c83db-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c83db-107">Remarks</span></span>  
 <span data-ttu-id="c83db-108">Se nenhum quadro de pilha gerenciada estiver disponível, `ppFrame` é definido como null.</span><span class="sxs-lookup"><span data-stu-id="c83db-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="c83db-109">Se o quadro ativo não estiver disponível, a chamada será bem-sucedida e `ppFrame` será nulo.</span><span class="sxs-lookup"><span data-stu-id="c83db-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="c83db-110">Quadros ativa não estará disponíveis para cadeias de iniciada devido ao CHAIN_ENTER_UNMANAGED e para algumas cadeias iniciadas devido ao CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="c83db-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="c83db-111">Consulte a enumeração CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="c83db-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83db-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c83db-112">Requirements</span></span>  
 <span data-ttu-id="c83db-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c83db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c83db-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c83db-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c83db-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c83db-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c83db-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c83db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
