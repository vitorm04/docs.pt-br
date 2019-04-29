---
title: Método ICorDebugAppDomain::Attach
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a290ca162e5ab71b4184d166bcd00f1d0217cb94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785171"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="9557b-102">Método ICorDebugAppDomain::Attach</span><span class="sxs-lookup"><span data-stu-id="9557b-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="9557b-103">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9557b-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9557b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9557b-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9557b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9557b-105">Remarks</span></span>  
 <span data-ttu-id="9557b-106">O depurador deve ser anexado ao domínio do aplicativo para receber eventos e habilitar a depuração do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9557b-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9557b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9557b-107">Requirements</span></span>  
 <span data-ttu-id="9557b-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9557b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9557b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9557b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9557b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9557b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9557b-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9557b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
