---
title: "Método ICorDebugEnum::GetCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b2be2e198007e15a0bae3ba0d3dd0cf1cf9983c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="c981f-102">Método ICorDebugEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="c981f-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="c981f-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c981f-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c981f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c981f-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c981f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c981f-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="c981f-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c981f-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c981f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c981f-107">Requirements</span></span>  
 <span data-ttu-id="c981f-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c981f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c981f-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c981f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c981f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c981f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c981f-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c981f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
