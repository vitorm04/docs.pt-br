---
title: "Enumeração LogSwitchCallReason"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LogSwitchCallReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: LogSwitchCallReason
helpviewer_keywords: LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dcd91001dfd823416b08ba49ba4ed12a2c4d058
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="f7d7d-102">Enumeração LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="f7d7d-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="f7d7d-103">Indica a operação que foi realizada em uma alternação entre depuração/rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f7d7d-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7d7d-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="f7d7d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f7d7d-105">Members</span></span>  
  
|<span data-ttu-id="f7d7d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f7d7d-106">Member</span></span>|<span data-ttu-id="f7d7d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7d7d-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="f7d7d-108">Uma opção de depuração/rastreamento foi criada.</span><span class="sxs-lookup"><span data-stu-id="f7d7d-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="f7d7d-109">Uma opção de depuração/rastreamento foi modificada.</span><span class="sxs-lookup"><span data-stu-id="f7d7d-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="f7d7d-110">Uma opção de depuração/rastreamento foi excluída.</span><span class="sxs-lookup"><span data-stu-id="f7d7d-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7d7d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7d7d-111">Requirements</span></span>  
 <span data-ttu-id="f7d7d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d7d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7d7d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7d7d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7d7d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d7d-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d7d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7d7d-116">See Also</span></span>  
 [<span data-ttu-id="f7d7d-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="f7d7d-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
