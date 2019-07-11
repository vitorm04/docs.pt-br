---
title: Método ICorDebugProcess5::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ec3dc37984228565b4a3fcc560d3857a1c1e46d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767337"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="efbff-102">Método ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="efbff-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="efbff-103">Converte um endereço de objeto em um objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="efbff-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efbff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efbff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efbff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efbff-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="efbff-106">[in] O endereço do objeto.</span><span class="sxs-lookup"><span data-stu-id="efbff-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="efbff-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="efbff-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efbff-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="efbff-108">Remarks</span></span>  
 <span data-ttu-id="efbff-109">Se `addr` não aponta para um objeto gerenciado válido, o `GetObject` retorno do método `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="efbff-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efbff-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efbff-110">Requirements</span></span>  
 <span data-ttu-id="efbff-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efbff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efbff-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efbff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efbff-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efbff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efbff-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efbff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efbff-115">See also</span></span>

- [<span data-ttu-id="efbff-116">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="efbff-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="efbff-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="efbff-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
