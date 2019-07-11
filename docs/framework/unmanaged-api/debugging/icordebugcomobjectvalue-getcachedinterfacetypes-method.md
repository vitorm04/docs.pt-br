---
title: Método ICorDebugComObjectValue::GetCachedInterfaceTypes
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7325e84d8fe4df9a31543426c6376d0941306fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748459"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="13dc0-102">Método ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="13dc0-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="13dc0-103">Fornece um enumerador para os tipos de interface que o objeto atual foi convertido em ou usado como.</span><span class="sxs-lookup"><span data-stu-id="13dc0-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13dc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13dc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13dc0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13dc0-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="13dc0-106">[in] Um valor que indica se o método retorna apenas interfaces do tempo de execução do Windows (`IInspectable` interfaces) ou todas as interfaces COM armazenados em cache pelo runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="13dc0-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="13dc0-107">[out] Um ponteiro para o endereço de um enumerador de ICorDebugTypeEnum que fornece acesso a objetos ICorDebugType que representam os tipos de interface em cache é filtrado acordo com a `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="13dc0-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13dc0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="13dc0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13dc0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13dc0-109">Requirements</span></span>  
 <span data-ttu-id="13dc0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13dc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13dc0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13dc0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13dc0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13dc0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13dc0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13dc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13dc0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13dc0-114">See also</span></span>

- [<span data-ttu-id="13dc0-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="13dc0-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="13dc0-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="13dc0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
