---
title: "Método ICorDebugManagedCallback::LoadClass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3518a20567cdac8ed6587aa3dc06408ae6bf7b06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>Método ICorDebugManagedCallback::LoadClass
Notifica o depurador que uma classe foi carregada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a classe foi carregada.  
  
 `c`  
 [in] Um ponteiro para um objeto ICorDebugClass que representa a classe.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada ocorre apenas se o carregamento de classe tiver sido habilitado para o módulo que contém a classe. Carregamento de classe está sempre habilitado para módulos dinâmicos.  
  
 O `LoadClass` retorno de chamada oferece um momento apropriado para associar os pontos de interrupção para as classes recém-gerado em módulos dinâmicos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
