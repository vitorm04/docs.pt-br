---
title: Método ICorDebugManagedCallback::LoadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: 80836cbbf82a97ccd6dc7251e5cbe934e0cbe66f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777270"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="d80ff-102">Método ICorDebugManagedCallback::LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="d80ff-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="d80ff-103">Notifica o depurador de que um assembly Common Language Runtime (CLR) foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d80ff-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d80ff-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d80ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d80ff-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d80ff-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual o assembly foi carregado.</span><span class="sxs-lookup"><span data-stu-id="d80ff-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="d80ff-107">no Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="d80ff-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d80ff-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d80ff-108">Requirements</span></span>  
 <span data-ttu-id="d80ff-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80ff-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d80ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d80ff-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d80ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d80ff-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80ff-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="d80ff-113">See also</span></span>

- [<span data-ttu-id="d80ff-114">Método UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="d80ff-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="d80ff-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d80ff-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
