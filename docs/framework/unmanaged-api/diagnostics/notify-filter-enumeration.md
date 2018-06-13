---
title: Enumeração NOTIFY_FILTER
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98c3e1ed3da209cbded5d76d938d2420fce606be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431001"
---
# <a name="notifyfilter-enumeration"></a>Enumeração NOTIFY_FILTER
Identifica os retornos de chamada para funções do depurador. Para obter mais informações, consulte o [Inotifysource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) método deve ser invocado.|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) método deve ser invocado.|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) método deve ser invocado.|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|Indica que o [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) método deve ser invocado.|  
|`NOTIFY_FILTER_ALLSYNC`|Indica que todos os [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) métodos devem ser chamados.|  
|`NOTIFY_FILTER_ALL`|Ativa todas as notificações existentes e futuras.|  
|`NOTIFY_FILTER_NONE`|Indica que nenhum método de notificação deve ser chamado.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
