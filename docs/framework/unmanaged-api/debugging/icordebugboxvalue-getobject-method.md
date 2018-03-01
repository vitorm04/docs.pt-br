---
title: "Método ICorDebugBoxValue::GetObject"
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
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e71da40af57d00e4651c094ddad9c86fc6fe636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="31876-102">Método ICorDebugBoxValue::GetObject</span><span class="sxs-lookup"><span data-stu-id="31876-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="31876-103">Obtém o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="31876-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31876-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31876-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31876-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31876-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="31876-106">[out] Um ponteiro para o endereço de um objeto ICorDebugObjectValue que representa o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="31876-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31876-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31876-107">Requirements</span></span>  
 <span data-ttu-id="31876-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31876-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31876-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31876-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31876-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31876-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31876-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31876-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
