---
title: Método ICorDebugChain::GetReason
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48650a370f7d15724e20850e9d3b47dc8215f960
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498348"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="29c84-102">Método ICorDebugChain::GetReason</span><span class="sxs-lookup"><span data-stu-id="29c84-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="29c84-103">Obtém o motivo para a gênese dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="29c84-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29c84-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29c84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29c84-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="29c84-106">[out] Um ponteiro para um valor (uma combinação bit a bit) da enumeração CorDebugChainReason que indica o motivo para a gênese dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="29c84-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c84-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29c84-107">Requirements</span></span>  
 <span data-ttu-id="29c84-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c84-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c84-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29c84-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29c84-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29c84-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c84-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c84-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
