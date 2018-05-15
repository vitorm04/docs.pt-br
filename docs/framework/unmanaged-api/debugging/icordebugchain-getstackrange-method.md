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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="e97cf-102">Método ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="e97cf-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="e97cf-103">Obtém o intervalo de endereços do segmento de pilha para essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="e97cf-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e97cf-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e97cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e97cf-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="e97cf-106">[out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço inicial do segmento de pilha.</span><span class="sxs-lookup"><span data-stu-id="e97cf-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="e97cf-107">[out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço final do segmento de pilha.</span><span class="sxs-lookup"><span data-stu-id="e97cf-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e97cf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e97cf-108">Remarks</span></span>  
 <span data-ttu-id="e97cf-109">O intervalo numérico é significativo apenas para comparação de locais de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="e97cf-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="e97cf-110">Você não pode fazer suposições sobre o que realmente está armazenado na pilha.</span><span class="sxs-lookup"><span data-stu-id="e97cf-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e97cf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e97cf-111">Requirements</span></span>  
 <span data-ttu-id="e97cf-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e97cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97cf-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e97cf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e97cf-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e97cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e97cf-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e97cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
