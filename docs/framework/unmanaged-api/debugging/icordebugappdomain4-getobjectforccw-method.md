---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405545"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="e3bff-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="e3bff-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="e3bff-103">Obtém um objeto gerenciado de um ponteiro CCW callable wrapper () COM.</span><span class="sxs-lookup"><span data-stu-id="e3bff-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3bff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3bff-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3bff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3bff-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="e3bff-106">[in] Um ponteiro CCW callable wrapper () COM.</span><span class="sxs-lookup"><span data-stu-id="e3bff-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="e3bff-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro CCW determinado.</span><span class="sxs-lookup"><span data-stu-id="e3bff-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3bff-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3bff-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3bff-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3bff-109">Requirements</span></span>  
 <span data-ttu-id="e3bff-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3bff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3bff-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3bff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3bff-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3bff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3bff-113">**Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3bff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bff-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3bff-114">See Also</span></span>  
 [<span data-ttu-id="e3bff-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="e3bff-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="e3bff-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e3bff-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
