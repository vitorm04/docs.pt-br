---
title: "Método ICorDebugAppDomain4::GetObjectForCCW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abce5563e8cd7eb0c599e835d0217157cf073485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="37d8b-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="37d8b-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="37d8b-103">Obtém um objeto gerenciado de um ponteiro CCW callable wrapper () COM.</span><span class="sxs-lookup"><span data-stu-id="37d8b-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37d8b-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37d8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37d8b-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="37d8b-106">[in] Um ponteiro CCW callable wrapper () COM.</span><span class="sxs-lookup"><span data-stu-id="37d8b-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="37d8b-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro CCW determinado.</span><span class="sxs-lookup"><span data-stu-id="37d8b-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37d8b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="37d8b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d8b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37d8b-109">Requirements</span></span>  
 <span data-ttu-id="37d8b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d8b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37d8b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37d8b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37d8b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37d8b-113">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37d8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d8b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37d8b-114">See Also</span></span>  
 [<span data-ttu-id="37d8b-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="37d8b-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="37d8b-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="37d8b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
