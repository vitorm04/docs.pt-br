---
title: Método ICorDebugChain::IsManaged
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 481f6d08e11a5f315c64b3d58df4ab291fa42e78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123842"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="6553a-102">Método ICorDebugChain::IsManaged</span><span class="sxs-lookup"><span data-stu-id="6553a-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="6553a-103">Obtém um valor que indica se esta cadeia está executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6553a-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6553a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6553a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6553a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6553a-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="6553a-106">[fora] `true` se essa cadeia estiver executando código gerenciado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6553a-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6553a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6553a-107">Requirements</span></span>  
 <span data-ttu-id="6553a-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6553a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6553a-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6553a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6553a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6553a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6553a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6553a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
