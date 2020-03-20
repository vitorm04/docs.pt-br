---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179045"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="85617-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="85617-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="85617-103">Obtém um objeto gerenciado a partir de um ponteiro de invólucro callable (CCW) COM.</span><span class="sxs-lookup"><span data-stu-id="85617-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85617-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85617-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85617-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="85617-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="85617-106">[em] Um ponteiro de invólucro callable COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="85617-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="85617-107">[fora] Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro CCW dado.</span><span class="sxs-lookup"><span data-stu-id="85617-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85617-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="85617-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85617-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85617-109">Requirements</span></span>  
 <span data-ttu-id="85617-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85617-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85617-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85617-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85617-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85617-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85617-113">**.NET Framework Versions:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85617-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85617-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="85617-114">See also</span></span>

- [<span data-ttu-id="85617-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="85617-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="85617-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85617-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
