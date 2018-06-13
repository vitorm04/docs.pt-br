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
ms.openlocfilehash: 291c8129a790c235ee6e7f163c49c4e1e726cce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402706"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="7c17d-102">Método ICorDebugChain::GetThread</span><span class="sxs-lookup"><span data-stu-id="7c17d-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="7c17d-103">Obtém o segmento físico que essa cadeia de chamada é parte do.</span><span class="sxs-lookup"><span data-stu-id="7c17d-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c17d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c17d-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c17d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c17d-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="7c17d-106">[out] Um ponteiro para um objeto ICorDebugThread que representa o segmento físico essa cadeia de chamada é parte do.</span><span class="sxs-lookup"><span data-stu-id="7c17d-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c17d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c17d-107">Requirements</span></span>  
 <span data-ttu-id="7c17d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c17d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c17d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c17d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c17d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c17d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c17d-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c17d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
