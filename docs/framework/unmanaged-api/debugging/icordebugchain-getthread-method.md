---
title: Método ICorDebugChain::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ab2b584b4a3e9bef17110f3084dc93efb2e5167
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989359"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="9a505-102">Método ICorDebugChain::GetThread</span><span class="sxs-lookup"><span data-stu-id="9a505-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="9a505-103">Obtém o thread físico que essa cadeia de chamada é parte do.</span><span class="sxs-lookup"><span data-stu-id="9a505-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a505-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a505-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a505-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a505-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="9a505-106">[out] Um ponteiro para um objeto de ICorDebugThread que representa o segmento físico essa cadeia de chamada faz parte.</span><span class="sxs-lookup"><span data-stu-id="9a505-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a505-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a505-107">Requirements</span></span>  
 <span data-ttu-id="9a505-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a505-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a505-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a505-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a505-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a505-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a505-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a505-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
