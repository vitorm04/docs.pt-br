---
title: Método ICorDebug::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 2d3f8360a1fb1164fd4e26f85246251409bee376
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788955"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="42fb5-102">Método ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="42fb5-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="42fb5-103">Encerra o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="42fb5-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42fb5-104">`Terminate` não deve ser chamado até que um retorno de chamada [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) tenha sido recebido para todos os processos sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="42fb5-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42fb5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42fb5-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="42fb5-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="42fb5-106">Remarks</span></span>  
 <span data-ttu-id="42fb5-107">`Terminate` deve ser chamado quando o objeto de `ICorDebug` não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="42fb5-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42fb5-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="42fb5-108">Requirements</span></span>  
 <span data-ttu-id="42fb5-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42fb5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42fb5-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42fb5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42fb5-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42fb5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42fb5-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42fb5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fb5-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="42fb5-113">See also</span></span>

- [<span data-ttu-id="42fb5-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="42fb5-114">ICorDebug Interface</span></span>](icordebug-interface.md)
