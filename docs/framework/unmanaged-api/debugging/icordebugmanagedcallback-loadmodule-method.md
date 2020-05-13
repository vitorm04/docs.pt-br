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
ms.openlocfilehash: cd4a16bc8b48f147ed03555b51eee5f42a445bc6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212692"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="e469e-102">Método ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="e469e-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="e469e-103">Notifica o depurador de que um módulo Common Language Runtime (CLR) foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e469e-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e469e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e469e-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e469e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e469e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e469e-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="e469e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="e469e-107">no Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="e469e-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e469e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e469e-108">Remarks</span></span>  
 <span data-ttu-id="e469e-109">O `LoadModule` retorno de chamada fornece um tempo apropriado para examinar os metadados do módulo, definir sinalizadores de compilador JIT (just-in-time) ou habilitar ou desabilitar retornos de chamada de carregamento de classe para o módulo.</span><span class="sxs-lookup"><span data-stu-id="e469e-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e469e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e469e-110">Requirements</span></span>  
 <span data-ttu-id="e469e-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e469e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e469e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e469e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e469e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e469e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e469e-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e469e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e469e-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e469e-115">See also</span></span>

- [<span data-ttu-id="e469e-116">Método UnloadModule</span><span class="sxs-lookup"><span data-stu-id="e469e-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="e469e-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e469e-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
