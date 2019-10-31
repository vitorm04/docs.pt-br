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
ms.openlocfilehash: 132734dfb6ba9d70836638ab67564fc215e9bc40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192121"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="a8cc7-102">Método ICorDebugChain::GetNext</span><span class="sxs-lookup"><span data-stu-id="a8cc7-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="a8cc7-103">Obtém a próxima cadeia de quadros para o thread.</span><span class="sxs-lookup"><span data-stu-id="a8cc7-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8cc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8cc7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8cc7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8cc7-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="a8cc7-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a próxima cadeia de quadros para o thread.</span><span class="sxs-lookup"><span data-stu-id="a8cc7-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="a8cc7-107">Se essa cadeia for a última cadeia, `ppChain` será NULL.</span><span class="sxs-lookup"><span data-stu-id="a8cc7-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8cc7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8cc7-108">Requirements</span></span>  
 <span data-ttu-id="a8cc7-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8cc7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8cc7-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8cc7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8cc7-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8cc7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8cc7-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8cc7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
