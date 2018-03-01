---
title: "Enumeração NOTIFY_FILTER"
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
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ef72cb965bec8f424f5df35d4f66715fa11a5e46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="34d2f-102">Enumeração NOTIFY_FILTER</span><span class="sxs-lookup"><span data-stu-id="34d2f-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="34d2f-103">Identifica os retornos de chamada para funções do depurador.</span><span class="sxs-lookup"><span data-stu-id="34d2f-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="34d2f-104">Para obter mais informações, consulte o [Inotifysource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="34d2f-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d2f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34d2f-105">Syntax</span></span>  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="34d2f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="34d2f-106">Members</span></span>  
  
|<span data-ttu-id="34d2f-107">Membro</span><span class="sxs-lookup"><span data-stu-id="34d2f-107">Member</span></span>|<span data-ttu-id="34d2f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="34d2f-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="34d2f-109">Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="34d2f-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="34d2f-110">Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="34d2f-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="34d2f-111">Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="34d2f-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="34d2f-112">Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="34d2f-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="34d2f-113">Indica que todos os [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) métodos devem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="34d2f-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="34d2f-114">Ativa todas as notificações existentes e futuras.</span><span class="sxs-lookup"><span data-stu-id="34d2f-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="34d2f-115">Indica que nenhum método de notificação deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="34d2f-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34d2f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34d2f-116">Requirements</span></span>  
 <span data-ttu-id="34d2f-117">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="34d2f-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d2f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34d2f-118">See Also</span></span>  
 [<span data-ttu-id="34d2f-119">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="34d2f-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
