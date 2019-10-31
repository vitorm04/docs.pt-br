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
ms.openlocfilehash: 199f58456e64ccf7ef771d42d5c7d64b189cb670
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125494"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="569d5-102">Método ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="569d5-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="569d5-103">Fornece um enumerador para os tipos de interface para os quais o objeto atual foi convertido ou usado como.</span><span class="sxs-lookup"><span data-stu-id="569d5-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="569d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="569d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="569d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="569d5-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="569d5-106">no Um valor que indica se o método retorna apenas interfaces Windows Runtime (interfaces`IInspectable`) ou todas as interfaces COM armazenadas em cache pelo RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="569d5-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="569d5-107">fora Um ponteiro para o endereço de um enumerador ICorDebugTypeEnum que fornece acesso a objetos ICorDebugType que representam tipos de interface em cache filtrados de acordo com `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="569d5-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="569d5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="569d5-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="569d5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="569d5-109">Requirements</span></span>  
 <span data-ttu-id="569d5-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="569d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="569d5-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="569d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="569d5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="569d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="569d5-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="569d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569d5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="569d5-114">See also</span></span>

- [<span data-ttu-id="569d5-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="569d5-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="569d5-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="569d5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
