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
ms.openlocfilehash: 35fdcd4bc3c9dbf6408f501256ce0df0174f9374
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948727"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="c948c-102">Método ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="c948c-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="c948c-103">Converte um endereço de objeto em um objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="c948c-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c948c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c948c-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c948c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c948c-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c948c-106">[in] O endereço do objeto.</span><span class="sxs-lookup"><span data-stu-id="c948c-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c948c-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="c948c-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c948c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c948c-108">Remarks</span></span>  
 <span data-ttu-id="c948c-109">Se `addr` não aponta para um objeto gerenciado válido, o `GetObject` retorno do método `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="c948c-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c948c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c948c-110">Requirements</span></span>  
 <span data-ttu-id="c948c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c948c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c948c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c948c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c948c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c948c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c948c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c948c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c948c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c948c-115">See also</span></span>

- [<span data-ttu-id="c948c-116">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="c948c-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="c948c-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c948c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
