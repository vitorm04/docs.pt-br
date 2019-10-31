---
title: Método ICorDebugManagedCallback::UnloadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: e2550320494b9ba43947c3176788042f5c2e6ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130625"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="7aa35-102">Método ICorDebugManagedCallback::UnloadClass</span><span class="sxs-lookup"><span data-stu-id="7aa35-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="7aa35-103">Notifica o depurador de que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="7aa35-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa35-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aa35-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aa35-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7aa35-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7aa35-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="7aa35-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="7aa35-107">no Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="7aa35-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aa35-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7aa35-108">Remarks</span></span>  
 <span data-ttu-id="7aa35-109">A classe não deve ser referenciada após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="7aa35-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aa35-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7aa35-110">Requirements</span></span>  
 <span data-ttu-id="7aa35-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aa35-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aa35-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7aa35-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aa35-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aa35-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aa35-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aa35-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa35-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7aa35-115">See also</span></span>

- [<span data-ttu-id="7aa35-116">Método LoadClass</span><span class="sxs-lookup"><span data-stu-id="7aa35-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="7aa35-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="7aa35-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
