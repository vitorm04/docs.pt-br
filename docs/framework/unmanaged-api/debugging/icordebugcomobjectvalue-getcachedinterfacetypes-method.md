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
ms.openlocfilehash: 36e6313ae7b4c67a20bee6d2a76a4ed1da84acbe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749807"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="f6ce0-102">Método ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="f6ce0-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="f6ce0-103">Fornece um enumerador para os tipos de interface que o objeto atual foi convertido em ou usado como.</span><span class="sxs-lookup"><span data-stu-id="f6ce0-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ce0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6ce0-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6ce0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6ce0-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="f6ce0-106">[in] Um valor que indica se o método retorna apenas [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) ou todas as interfaces COM armazenados em cache pelo runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="f6ce0-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="f6ce0-107">[out] Um ponteiro para o endereço de um enumerador de ICorDebugTypeEnum que fornece acesso a objetos ICorDebugType que representam os tipos de interface em cache é filtrado acordo com a `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="f6ce0-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6ce0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6ce0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6ce0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6ce0-109">Requirements</span></span>  
 <span data-ttu-id="f6ce0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6ce0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6ce0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6ce0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6ce0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6ce0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6ce0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6ce0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ce0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6ce0-114">See also</span></span>

- [<span data-ttu-id="f6ce0-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="f6ce0-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="f6ce0-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f6ce0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
