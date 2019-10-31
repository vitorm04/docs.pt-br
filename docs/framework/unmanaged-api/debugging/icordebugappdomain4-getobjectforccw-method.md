---
title: Método ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 8b046eb5926bb9aa4738e8fff8e61b0b7c23a3aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088823"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="09978-102">Método ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="09978-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="09978-103">Obtém um objeto gerenciado de um ponteiro de COM Callable Wrapper (CCW).</span><span class="sxs-lookup"><span data-stu-id="09978-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09978-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09978-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09978-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09978-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="09978-106">no Um ponteiro de COM Callable Wrapper (CCW).</span><span class="sxs-lookup"><span data-stu-id="09978-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="09978-107">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o objeto gerenciado que corresponde ao ponteiro do CCW fornecido.</span><span class="sxs-lookup"><span data-stu-id="09978-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09978-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="09978-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09978-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09978-109">Requirements</span></span>  
 <span data-ttu-id="09978-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09978-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09978-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09978-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09978-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09978-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09978-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09978-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09978-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09978-114">See also</span></span>

- [<span data-ttu-id="09978-115">Interface ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="09978-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="09978-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="09978-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
