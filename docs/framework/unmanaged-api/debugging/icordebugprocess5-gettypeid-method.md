---
title: "Método ICorDebugProcess5::GetTypeID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f76285fceaa32f7c8b62b5cdf2ae7b4e9ec00de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="8e552-102">Método ICorDebugProcess5::GetTypeID</span><span class="sxs-lookup"><span data-stu-id="8e552-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="8e552-103">Converte um endereço de objeto para um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identificador.</span><span class="sxs-lookup"><span data-stu-id="8e552-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e552-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e552-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e552-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e552-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="8e552-106">[in] O endereço do objeto.</span><span class="sxs-lookup"><span data-stu-id="8e552-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="8e552-107">Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) valor que identifica o objeto.</span><span class="sxs-lookup"><span data-stu-id="8e552-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e552-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e552-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e552-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e552-109">Requirements</span></span>  
 <span data-ttu-id="8e552-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e552-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e552-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e552-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e552-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e552-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e552-113">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e552-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e552-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e552-114">See Also</span></span>  
 [<span data-ttu-id="8e552-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="8e552-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="8e552-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8e552-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
