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
ms.openlocfilehash: a57e73495ac22a25a5f13c06d4c75dee7dde41e0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894628"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="5bc5c-102">Método ICorDebugChain::GetPrevious</span><span class="sxs-lookup"><span data-stu-id="5bc5c-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="5bc5c-103">Obtém a cadeia de quadros anterior para o thread.</span><span class="sxs-lookup"><span data-stu-id="5bc5c-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bc5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc5c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bc5c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="5bc5c-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de quadros anterior para esse thread.</span><span class="sxs-lookup"><span data-stu-id="5bc5c-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="5bc5c-107">Se essa cadeia for a primeira cadeia, `ppChain` será NULL.</span><span class="sxs-lookup"><span data-stu-id="5bc5c-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc5c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bc5c-108">Requirements</span></span>  
 <span data-ttu-id="5bc5c-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc5c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc5c-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bc5c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bc5c-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc5c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc5c-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc5c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
