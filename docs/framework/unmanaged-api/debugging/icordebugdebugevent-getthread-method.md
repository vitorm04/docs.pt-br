---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976372"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="7fd2c-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="7fd2c-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="7fd2c-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="7fd2c-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fd2c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fd2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fd2c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fd2c-105">Parameters</span></span>  
 <span data-ttu-id="7fd2c-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="7fd2c-106">ppThread</span></span>  
 <span data-ttu-id="7fd2c-107">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="7fd2c-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fd2c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fd2c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fd2c-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7fd2c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fd2c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fd2c-110">Requirements</span></span>  
 <span data-ttu-id="7fd2c-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd2c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd2c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fd2c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fd2c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fd2c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fd2c-114">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd2c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd2c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fd2c-115">See also</span></span>

- [<span data-ttu-id="7fd2c-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="7fd2c-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="7fd2c-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7fd2c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
