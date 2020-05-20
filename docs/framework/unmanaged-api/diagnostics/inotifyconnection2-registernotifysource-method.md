---
title: Método INotifyConnection2::RegisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442066"
---
# <a name="inotifyconnection2registernotifysource-method"></a>Método INotifyConnection2::RegisterNotifySource
Instala uma fonte de notificação especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `in_pNotifySource`  
 no Especifica o objeto a ser usado como a fonte de notificação.  
  
 `out_ppNotifySink`  
 fora Recebe o objeto a ser usado como o coletor de notificação.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Confira também

- [Interface INotifyConnection2](inotifyconnection2-interface.md)
- [Interface INotifySource2](inotifysource2-interface.md)
- [Interface INotifySink2](inotifysink2-interface.md)
- [Método UnregisterNotifySource](inotifyconnection2-unregisternotifysource-method.md)
