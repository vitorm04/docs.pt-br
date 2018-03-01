---
title: "Método ICorDebugGenericValue::SetValue"
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
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11cb4ab6d32f3dbada25fe42f062fdc2c1fabd17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="910a0-102">Método ICorDebugGenericValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="910a0-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="910a0-103">Copia um novo valor de buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="910a0-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="910a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="910a0-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="910a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="910a0-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="910a0-106">[in] Um ponteiro para o buffer da qual copiar o valor.</span><span class="sxs-lookup"><span data-stu-id="910a0-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="910a0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="910a0-107">Remarks</span></span>  
 <span data-ttu-id="910a0-108">Para tipos de referência, o valor é a referência, não o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="910a0-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="910a0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="910a0-109">Requirements</span></span>  
 <span data-ttu-id="910a0-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="910a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="910a0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="910a0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="910a0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="910a0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="910a0-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="910a0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
