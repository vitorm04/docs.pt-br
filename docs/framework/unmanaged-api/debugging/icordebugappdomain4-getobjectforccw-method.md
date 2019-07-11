---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ab4905c55a1395e9ae5cba8343e6b832622005d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737634"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="a07c1-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="a07c1-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="a07c1-103">Obtém um objeto gerenciado de um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="a07c1-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a07c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a07c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a07c1-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="a07c1-106">[in] Um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="a07c1-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="a07c1-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o objeto gerenciado que corresponde ao determinado ponteiro CCW.</span><span class="sxs-lookup"><span data-stu-id="a07c1-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a07c1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a07c1-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a07c1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a07c1-109">Requirements</span></span>  
 <span data-ttu-id="a07c1-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a07c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a07c1-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a07c1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a07c1-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a07c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a07c1-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a07c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07c1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a07c1-114">See also</span></span>

- [<span data-ttu-id="a07c1-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="a07c1-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="a07c1-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a07c1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
