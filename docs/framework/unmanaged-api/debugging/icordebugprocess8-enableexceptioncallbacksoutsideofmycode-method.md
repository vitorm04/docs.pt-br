---
title: Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f08f24e16b34d911793b5c8d4a28168f7677b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418962"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="48b1a-102">Método ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="48b1a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="48b1a-103">[Com suporte no [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="48b1a-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="48b1a-104">Habilita ou desabilita determinados tipos de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) retornos de chamada de exceção.</span><span class="sxs-lookup"><span data-stu-id="48b1a-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b1a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48b1a-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48b1a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48b1a-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="48b1a-107">[in]</span><span class="sxs-lookup"><span data-stu-id="48b1a-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48b1a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="48b1a-108">Remarks</span></span>  
 <span data-ttu-id="48b1a-109">Se o valor de `enableExceptionsOutsideOfJMC` é `false`:</span><span class="sxs-lookup"><span data-stu-id="48b1a-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="48b1a-110">Uma exceção DEBUG_EXCEPTION_FIRST_CHANCE não resultará em um retorno de chamada para o depurador.</span><span class="sxs-lookup"><span data-stu-id="48b1a-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="48b1a-111">Uma exceção DEBUG_EXCEPTION_CATCH_HANDLER_FOUND não resultará em um retorno de chamada para o depurador se nunca ignora a exceção no código de usuário (ou seja, o caminho de uma origem de exceção para um manipulador de exceção não possui métodos marcados como /justmycode ou JMC).</span><span class="sxs-lookup"><span data-stu-id="48b1a-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="48b1a-112">O valor padrão de `enableExceptionsOutsideOfJMC` é `true`.</span><span class="sxs-lookup"><span data-stu-id="48b1a-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b1a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48b1a-113">Requirements</span></span>  
 <span data-ttu-id="48b1a-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b1a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b1a-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48b1a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48b1a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48b1a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48b1a-117">**Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b1a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b1a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48b1a-118">See Also</span></span>  
 [<span data-ttu-id="48b1a-119">Interface ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="48b1a-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="48b1a-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="48b1a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
