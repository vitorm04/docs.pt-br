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
ms.openlocfilehash: 55036fcdbd186f91c0e94fb05f3023cf614751f7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894247"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="6b225-102">Método ICorDebugChain::IsManaged</span><span class="sxs-lookup"><span data-stu-id="6b225-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="6b225-103">Obtém um valor que indica se esta cadeia está executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6b225-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b225-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b225-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b225-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b225-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="6b225-106">fora `true` se essa cadeia estiver executando código gerenciado; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="6b225-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b225-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b225-107">Requirements</span></span>  
 <span data-ttu-id="6b225-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b225-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b225-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b225-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b225-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b225-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b225-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b225-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
