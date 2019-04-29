---
title: Método ICorDebugChain::GetNext
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ecb4f8a5519fb819161ed917ad03d2537bd9551
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645234"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="72a48-102">Método ICorDebugChain::GetNext</span><span class="sxs-lookup"><span data-stu-id="72a48-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="72a48-103">Obtém a próxima cadeia de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="72a48-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72a48-104">Syntax</span></span>  
  
```  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72a48-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="72a48-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a próxima cadeia de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="72a48-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="72a48-107">Se essa cadeia é a última cadeia, `ppChain` é nulo.</span><span class="sxs-lookup"><span data-stu-id="72a48-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a48-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72a48-108">Requirements</span></span>  
 <span data-ttu-id="72a48-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a48-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a48-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72a48-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72a48-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a48-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a48-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a48-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
