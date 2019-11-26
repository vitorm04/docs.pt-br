---
title: Método INotifyConnection2::UnregisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: cf399d0c7dec7528f02988ddfe6ca5c0b1f0c4c3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440992"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>Método INotifyConnection2::UnregisterNotifySource
Removes a specified notification source object from the connection.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `in_pNotifySource`  
 [in] Notification object to be unregistered.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Consulte também

- [Interface INotifyConnection2](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [Interface INotifySource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Método RegisterNotifySource](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
