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
ms.openlocfilehash: 9d02a68e80e34be906e9fe09f3457a0f2214c6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405061"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="c4530-102">Método ICorDebugChain::GetReason</span><span class="sxs-lookup"><span data-stu-id="c4530-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="c4530-103">Obtém o motivo para genesis dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="c4530-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4530-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4530-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4530-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4530-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="c4530-106">[out] Um ponteiro para um valor (uma combinação bit a bit) da enumeração CorDebugChainReason que indica o motivo para genesis dessa cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="c4530-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4530-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4530-107">Requirements</span></span>  
 <span data-ttu-id="c4530-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4530-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4530-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4530-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4530-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4530-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4530-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4530-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
