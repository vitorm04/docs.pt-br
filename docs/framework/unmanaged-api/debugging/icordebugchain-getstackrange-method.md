---
title: Método ICorDebugChain::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123859"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="ddea7-102">Método ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="ddea7-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="ddea7-103">Obtém o intervalo de endereços do segmento da pilha para esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="ddea7-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddea7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddea7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddea7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ddea7-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="ddea7-106">fora Um ponteiro para um valor `CORDB_ADDRESS` que é o endereço inicial do segmento de pilha.</span><span class="sxs-lookup"><span data-stu-id="ddea7-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="ddea7-107">fora Um ponteiro para um valor `CORDB_ADDRESS` que é o endereço final do segmento da pilha.</span><span class="sxs-lookup"><span data-stu-id="ddea7-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddea7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ddea7-108">Remarks</span></span>  
 <span data-ttu-id="ddea7-109">O intervalo numérico é significativo apenas para comparação de locais de quadros de pilha.</span><span class="sxs-lookup"><span data-stu-id="ddea7-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="ddea7-110">Você não pode fazer suposições sobre o que realmente está armazenado na pilha.</span><span class="sxs-lookup"><span data-stu-id="ddea7-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddea7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ddea7-111">Requirements</span></span>  
 <span data-ttu-id="ddea7-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddea7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddea7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddea7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddea7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddea7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddea7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddea7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
