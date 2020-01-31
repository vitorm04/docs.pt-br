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
ms.openlocfilehash: f720b06581ac60c8bd68dc5e85f15843fd9425f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788902"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="cd0b8-102">Método ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="cd0b8-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="cd0b8-103">Fornece um enumerador para os tipos de interface para os quais o objeto atual foi convertido ou usado como.</span><span class="sxs-lookup"><span data-stu-id="cd0b8-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd0b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd0b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd0b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd0b8-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="cd0b8-106">no Um valor que indica se o método retorna apenas interfaces Windows Runtime (interfaces`IInspectable`) ou todas as interfaces COM armazenadas em cache pelo RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="cd0b8-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="cd0b8-107">fora Um ponteiro para o endereço de um enumerador ICorDebugTypeEnum que fornece acesso a objetos ICorDebugType que representam tipos de interface em cache filtrados de acordo com `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="cd0b8-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd0b8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd0b8-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd0b8-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cd0b8-109">Requirements</span></span>  
 <span data-ttu-id="cd0b8-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd0b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd0b8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd0b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd0b8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd0b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd0b8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd0b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0b8-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="cd0b8-114">See also</span></span>

- [<span data-ttu-id="cd0b8-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="cd0b8-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="cd0b8-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cd0b8-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
