---
title: Método ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777131"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="9823c-102">Método ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="9823c-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="9823c-103">Notifica o depurador de que um módulo Common Language Runtime (CLR) foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9823c-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9823c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9823c-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9823c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9823c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9823c-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="9823c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="9823c-107">no Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="9823c-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9823c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9823c-108">Remarks</span></span>  
 <span data-ttu-id="9823c-109">O retorno de chamada `LoadModule` fornece um tempo apropriado para examinar os metadados do módulo, definir sinalizadores de compilador JIT (just-in-time) ou habilitar ou desabilitar retornos de chamada de carregamento de classe para o módulo.</span><span class="sxs-lookup"><span data-stu-id="9823c-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9823c-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9823c-110">Requirements</span></span>  
 <span data-ttu-id="9823c-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9823c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9823c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9823c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9823c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9823c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9823c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9823c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9823c-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="9823c-115">See also</span></span>

- [<span data-ttu-id="9823c-116">Método UnloadModule</span><span class="sxs-lookup"><span data-stu-id="9823c-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="9823c-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="9823c-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
