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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178596"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="f0d0d-102">Método ICorDebugProcess5::GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="f0d0d-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="f0d0d-103">Fornece informações sobre os campos que pertencem a um tipo.</span><span class="sxs-lookup"><span data-stu-id="f0d0d-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0d0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0d0d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0d0d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f0d0d-106">[em] O identificador do tipo cujas informações de campo são recuperadas.</span><span class="sxs-lookup"><span data-stu-id="f0d0d-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="f0d0d-107">[em] O número de [objetos COR_FIELD](cor-field-structure.md) cujas informações de campo devem ser recuperadas.</span><span class="sxs-lookup"><span data-stu-id="f0d0d-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="f0d0d-108">[fora] Uma série de [objetos COR_FIELD](cor-field-structure.md) que fornecem informações sobre os campos que pertencem ao tipo.</span><span class="sxs-lookup"><span data-stu-id="f0d0d-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="f0d0d-109">[fora] Um ponteiro para o número `fields`de [objetos COR_FIELD](cor-field-structure.md) incluídos em .</span><span class="sxs-lookup"><span data-stu-id="f0d0d-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0d0d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0d0d-110">Remarks</span></span>  
 <span data-ttu-id="f0d0d-111">O `celt` parâmetro, que especifica o número de campos cujas `fields`informações de campo o `COR_TYPE_LAYOUT::numFields` método usa para preencher, deve corresponder ao valor do campo.</span><span class="sxs-lookup"><span data-stu-id="f0d0d-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d0d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0d0d-112">Requirements</span></span>  
 <span data-ttu-id="f0d0d-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d0d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d0d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0d0d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0d0d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0d0d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0d0d-116">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d0d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d0d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0d0d-117">See also</span></span>

- [<span data-ttu-id="f0d0d-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="f0d0d-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="f0d0d-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f0d0d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
