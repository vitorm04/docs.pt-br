---
title: Método ICorDebugEnum::GetCount
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4af328c537fbc3b64eb1a2ac3df3a4e4224789e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466616"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="8825a-102">Método ICorDebugEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="8825a-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="8825a-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="8825a-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8825a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8825a-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8825a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8825a-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="8825a-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="8825a-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8825a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8825a-107">Requirements</span></span>  
 <span data-ttu-id="8825a-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8825a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8825a-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8825a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8825a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8825a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8825a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8825a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
