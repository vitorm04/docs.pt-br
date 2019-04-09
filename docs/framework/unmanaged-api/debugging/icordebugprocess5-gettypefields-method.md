---
title: Método ICorDebugProcess5::GetTypeFields
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107946"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="24617-102">Método ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="24617-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="24617-103">Fornece informações sobre os campos que pertencem a um tipo.</span><span class="sxs-lookup"><span data-stu-id="24617-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24617-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24617-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24617-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24617-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="24617-106">[in] O identificador do tipo cujas informações de campo são recuperadas.</span><span class="sxs-lookup"><span data-stu-id="24617-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="24617-107">[in] O número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos cujas informações de campo deve ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="24617-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="24617-108">[out] Uma matriz de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos que fornecem informações sobre os campos que pertencem ao tipo.</span><span class="sxs-lookup"><span data-stu-id="24617-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="24617-109">[out] Um ponteiro para o número de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objetos incluídos no `fields`.</span><span class="sxs-lookup"><span data-stu-id="24617-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24617-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="24617-110">Remarks</span></span>  
 <span data-ttu-id="24617-111">O `celt` parâmetro, que especifica o número de campos cujas informações de campo, o método usa para popular `fields`, deve corresponder ao valor da `COR_TYPE_LAYOUT::numFields` campo.</span><span class="sxs-lookup"><span data-stu-id="24617-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24617-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24617-112">Requirements</span></span>  
 <span data-ttu-id="24617-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24617-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24617-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24617-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24617-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24617-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="24617-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="24617-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24617-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24617-117">See also</span></span>

- [<span data-ttu-id="24617-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="24617-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="24617-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="24617-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
