---
title: "Método ICorDebugProcess5::GetTypeFields"
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
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1eb167517a33788a0d7e30663675b294d29ba3cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="b15b5-102">Método ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="b15b5-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="b15b5-103">Fornece informações sobre os campos que pertencem a um tipo.</span><span class="sxs-lookup"><span data-stu-id="b15b5-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b15b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b15b5-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b15b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b15b5-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b15b5-106">[in] O identificador do tipo cujas informações de campo são recuperadas.</span><span class="sxs-lookup"><span data-stu-id="b15b5-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="b15b5-107">[in] O número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos cujas informações de campo deve ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="b15b5-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="b15b5-108">[out] Uma matriz de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos que fornecem informações sobre os campos que pertencem ao tipo.</span><span class="sxs-lookup"><span data-stu-id="b15b5-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="b15b5-109">[out] Um ponteiro para o número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos incluídos no `fields`.</span><span class="sxs-lookup"><span data-stu-id="b15b5-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b15b5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b15b5-110">Remarks</span></span>  
 <span data-ttu-id="b15b5-111">O `celt` parâmetro, que especifica o número de campos cujas informações de campo que usa o método para preencher `fields`, deve corresponder ao valor da `COR_TYPE_LAYOUT::numFields` campo.</span><span class="sxs-lookup"><span data-stu-id="b15b5-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b15b5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b15b5-112">Requirements</span></span>  
 <span data-ttu-id="b15b5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b15b5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b15b5-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b15b5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b15b5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b15b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b15b5-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b15b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15b5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b15b5-117">See Also</span></span>  
 [<span data-ttu-id="b15b5-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="b15b5-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="b15b5-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b15b5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
