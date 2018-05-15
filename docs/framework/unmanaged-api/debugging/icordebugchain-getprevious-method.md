---
title: Método ICorDebugChain::GetPrevious
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c0545440ed63ba914229249080ec9f6be8eb2b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="76cbd-102">Método ICorDebugChain::GetPrevious</span><span class="sxs-lookup"><span data-stu-id="76cbd-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="76cbd-103">Obtém a cadeia anterior de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="76cbd-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76cbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76cbd-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76cbd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76cbd-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="76cbd-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia anterior de quadros para este segmento.</span><span class="sxs-lookup"><span data-stu-id="76cbd-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="76cbd-107">Se essa cadeia é a primeira cadeia, `ppChain` é nulo.</span><span class="sxs-lookup"><span data-stu-id="76cbd-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76cbd-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76cbd-108">Requirements</span></span>  
 <span data-ttu-id="76cbd-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76cbd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76cbd-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76cbd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76cbd-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76cbd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76cbd-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76cbd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
