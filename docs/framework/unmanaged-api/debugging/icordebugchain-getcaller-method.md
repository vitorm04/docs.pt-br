---
title: Método ICorDebugChain::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: a6d26924773e6ad505975402ec3ace150d02cc3a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894609"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="3dd9b-102">Método ICorDebugChain::GetCaller</span><span class="sxs-lookup"><span data-stu-id="3dd9b-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="3dd9b-103">Obtém a cadeia que chamou essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dd9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dd9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3dd9b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="3dd9b-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="3dd9b-107">Se essa cadeia fosse chamada espontaneamente (como seria o caso, se essa cadeia ou o depurador inicializasse a pilha de chamadas `ppChain` ), será nulo.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd9b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dd9b-108">Remarks</span></span>  
 <span data-ttu-id="3dd9b-109">A cadeia de chamada pode estar em um thread diferente, se a chamada tiver sido empacotada entre threads.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd9b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dd9b-110">Requirements</span></span>  
 <span data-ttu-id="3dd9b-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd9b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd9b-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dd9b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd9b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd9b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd9b-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd9b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
