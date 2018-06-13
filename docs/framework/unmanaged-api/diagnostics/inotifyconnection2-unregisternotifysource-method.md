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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4b4f90f918c872f3227ac22f4cccadcbf3194a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425474"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>Método INotifyConnection2::UnregisterNotifySource
Remove um objeto de fonte de notificação especificado a conexão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `in_pNotifySource`  
 [in] Objeto de notificação a ser cancelado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Consulte também  
 [Interface INotifyConnection2](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [Interface INotifySource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [Método RegisterNotifySource](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
