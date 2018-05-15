---
title: Enumeração LogSwitchCallReason
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fe5710f1be0bfa4e651668e2469c3551ad79261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="be1f0-102">Enumeração LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="be1f0-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="be1f0-103">Indica a operação que foi realizada em uma alternação entre depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="be1f0-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be1f0-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="be1f0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="be1f0-105">Members</span></span>  
  
|<span data-ttu-id="be1f0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="be1f0-106">Member</span></span>|<span data-ttu-id="be1f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="be1f0-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="be1f0-108">Uma opção de depuração/rastreamento foi criada.</span><span class="sxs-lookup"><span data-stu-id="be1f0-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="be1f0-109">Uma opção de depuração/rastreamento foi modificada.</span><span class="sxs-lookup"><span data-stu-id="be1f0-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="be1f0-110">Uma opção de depuração/rastreamento foi excluída.</span><span class="sxs-lookup"><span data-stu-id="be1f0-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be1f0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be1f0-111">Requirements</span></span>  
 <span data-ttu-id="be1f0-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be1f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be1f0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be1f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be1f0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be1f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be1f0-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be1f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1f0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be1f0-116">See Also</span></span>  
 [<span data-ttu-id="be1f0-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="be1f0-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
