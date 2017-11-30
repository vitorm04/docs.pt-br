---
title: "Método ICorDebugComObjectValue::GetCachedInterfaceTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2150e75b5b9f09424f08c29345d5d139c1673afa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="a02e1-102">Método ICorDebugComObjectValue::GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="a02e1-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="a02e1-103">Fornece um enumerador para os tipos de interface que o objeto atual foi convertido em ou usado como.</span><span class="sxs-lookup"><span data-stu-id="a02e1-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a02e1-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a02e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a02e1-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="a02e1-106">[in] Um valor que indica se o método retorna apenas [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) ou todas as interfaces COM armazenada em cache pelo runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="a02e1-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="a02e1-107">[out] Um ponteiro para o endereço de um enumerador de ICorDebugTypeEnum que fornece acesso a objetos ICorDebugType que representam tipos de interface em cache filtrados de acordo com `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="a02e1-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a02e1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a02e1-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02e1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a02e1-109">Requirements</span></span>  
 <span data-ttu-id="a02e1-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02e1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02e1-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a02e1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a02e1-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a02e1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a02e1-113">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02e1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a02e1-114">See Also</span></span>  
 [<span data-ttu-id="a02e1-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="a02e1-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="a02e1-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a02e1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
