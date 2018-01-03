---
title: "Método ICorDebugChain::IsManaged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e9937222c215d22ef4ef572873385f279e7ba86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="38474-102">Método ICorDebugChain::IsManaged</span><span class="sxs-lookup"><span data-stu-id="38474-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="38474-103">Obtém um valor que indica se esta cadeia está em execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="38474-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38474-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38474-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38474-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38474-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="38474-106">[out] `true` se esta cadeia está executando código gerenciado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="38474-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38474-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38474-107">Requirements</span></span>  
 <span data-ttu-id="38474-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38474-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38474-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38474-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38474-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38474-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38474-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38474-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
