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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402490"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="b2dda-102">Método ICorDebugAppDomain::Attach</span><span class="sxs-lookup"><span data-stu-id="b2dda-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="b2dda-103">Anexa o depurador ao domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2dda-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2dda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2dda-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2dda-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2dda-105">Remarks</span></span>  
 <span data-ttu-id="b2dda-106">O depurador deve ser anexado ao domínio do aplicativo para receber eventos de e para habilitar a depuração do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2dda-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2dda-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2dda-107">Requirements</span></span>  
 <span data-ttu-id="b2dda-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2dda-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2dda-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2dda-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2dda-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2dda-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2dda-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2dda-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
