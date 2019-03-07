---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 985d98059c0c763f560d5e0f06133c45e75fa51a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490418"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="b2264-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="b2264-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="b2264-103">Obtém um objeto gerenciado de um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="b2264-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2264-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2264-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2264-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2264-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="b2264-106">[in] Um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="b2264-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="b2264-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o objeto gerenciado que corresponde ao determinado ponteiro CCW.</span><span class="sxs-lookup"><span data-stu-id="b2264-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2264-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2264-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2264-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2264-109">Requirements</span></span>  
 <span data-ttu-id="b2264-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2264-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2264-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2264-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2264-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2264-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2264-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2264-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2264-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2264-114">See also</span></span>
- [<span data-ttu-id="b2264-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="b2264-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="b2264-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b2264-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
