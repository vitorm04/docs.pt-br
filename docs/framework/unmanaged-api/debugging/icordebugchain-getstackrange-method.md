---
title: "Método ICorDebugChain::GetStackRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37a9be7924a6d9c1f1d78bd10f9642fff22036bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="2d912-102">Método ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="2d912-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="2d912-103">Obtém o intervalo de endereços do segmento de pilha para essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="2d912-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d912-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d912-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d912-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d912-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="2d912-106">[out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço inicial do segmento de pilha.</span><span class="sxs-lookup"><span data-stu-id="2d912-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="2d912-107">[out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço final do segmento de pilha.</span><span class="sxs-lookup"><span data-stu-id="2d912-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d912-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d912-108">Remarks</span></span>  
 <span data-ttu-id="2d912-109">O intervalo numérico é significativo apenas para comparação de locais de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="2d912-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="2d912-110">Você não pode fazer suposições sobre o que realmente está armazenado na pilha.</span><span class="sxs-lookup"><span data-stu-id="2d912-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d912-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d912-111">Requirements</span></span>  
 <span data-ttu-id="2d912-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d912-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d912-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d912-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d912-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d912-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d912-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d912-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
