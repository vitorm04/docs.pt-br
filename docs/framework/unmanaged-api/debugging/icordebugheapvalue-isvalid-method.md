---
title: "Método ICorDebugHeapValue::IsValid"
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
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f4f356c953feaf0e6597983f431222a469e90c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="65346-102">Método ICorDebugHeapValue::IsValid</span><span class="sxs-lookup"><span data-stu-id="65346-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="65346-103">Obtém um valor que indica se o objeto representado por esse ICorDebugHeapValue é válido.</span><span class="sxs-lookup"><span data-stu-id="65346-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="65346-104">Esse método foi preterido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="65346-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65346-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65346-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65346-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65346-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="65346-107">[out] Um ponteiro para um valor booliano que indica se esse valor no heap é válido.</span><span class="sxs-lookup"><span data-stu-id="65346-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65346-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="65346-108">Remarks</span></span>  
 <span data-ttu-id="65346-109">O valor será inválido se ele tem sido recuperado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="65346-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="65346-110">Esse método foi substituído.</span><span class="sxs-lookup"><span data-stu-id="65346-110">This method has been deprecated.</span></span> <span data-ttu-id="65346-111">No .NET Framework 2.0, todos os valores são válidos até [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) é chamado, no qual os valores são invalidados.</span><span class="sxs-lookup"><span data-stu-id="65346-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65346-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65346-112">Requirements</span></span>  
 <span data-ttu-id="65346-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65346-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65346-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65346-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65346-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65346-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65346-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65346-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
