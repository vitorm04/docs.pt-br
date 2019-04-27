---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 973442a969746671e4d85c5d7881f51c5dfba535
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922597"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="4c566-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="4c566-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="4c566-103">Obtém um objeto gerenciado de um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="4c566-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c566-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c566-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c566-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c566-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="4c566-106">[in] Um ponteiro CCW (callable wrapper) COM.</span><span class="sxs-lookup"><span data-stu-id="4c566-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="4c566-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o objeto gerenciado que corresponde ao determinado ponteiro CCW.</span><span class="sxs-lookup"><span data-stu-id="4c566-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c566-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c566-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c566-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c566-109">Requirements</span></span>  
 <span data-ttu-id="4c566-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c566-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c566-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c566-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c566-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c566-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c566-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c566-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c566-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c566-114">See also</span></span>

- [<span data-ttu-id="4c566-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="4c566-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="4c566-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4c566-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
