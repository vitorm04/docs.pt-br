---
title: Método ICorDebugProcess5::GetTypeID
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f58e4213959ca1cd6e65bc809a9ad964bebc31ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494786"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="9c03e-102">Método ICorDebugProcess5::GetTypeID</span><span class="sxs-lookup"><span data-stu-id="9c03e-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="9c03e-103">Converte um endereço de objeto para um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identificador.</span><span class="sxs-lookup"><span data-stu-id="9c03e-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c03e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c03e-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c03e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c03e-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="9c03e-106">[in] O endereço do objeto.</span><span class="sxs-lookup"><span data-stu-id="9c03e-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="9c03e-107">Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) valor que identifica o objeto.</span><span class="sxs-lookup"><span data-stu-id="9c03e-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c03e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c03e-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c03e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c03e-109">Requirements</span></span>  
 <span data-ttu-id="9c03e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c03e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c03e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c03e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c03e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c03e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c03e-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c03e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c03e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c03e-114">See also</span></span>
- [<span data-ttu-id="9c03e-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="9c03e-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="9c03e-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9c03e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
