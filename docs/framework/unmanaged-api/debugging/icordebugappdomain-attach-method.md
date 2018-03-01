---
title: "Método ICorDebugAppDomain::Attach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ba725cfe4aabab14de4b64297a038bf0b0ccec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="eab66-102">Método ICorDebugAppDomain::Attach</span><span class="sxs-lookup"><span data-stu-id="eab66-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="eab66-103">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eab66-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eab66-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="eab66-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="eab66-105">Remarks</span></span>  
 <span data-ttu-id="eab66-106">O depurador deve ser anexado ao domínio do aplicativo para receber eventos de e para habilitar a depuração do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eab66-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab66-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eab66-107">Requirements</span></span>  
 <span data-ttu-id="eab66-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab66-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab66-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eab66-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eab66-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eab66-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab66-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab66-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
