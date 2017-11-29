---
title: "Método ICorDebugManagedCallback2::MDANotification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.MDANotification
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aeddab575f6667dbd27ab3474ae9c6e00dd05750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>Método ICorDebugManagedCallback2::MDANotification
Fornece notificação de que a execução de código encontrou um Assistente de depuração gerenciado (MDA) no aplicativo que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pController`  
 [in] Um ponteiro para uma interface ICorDebugController que expõe o processo ou um domínio de aplicativo no qual ocorreu o MDA.  
  
 Um depurador não deve fazer suposições sobre se o controlador é um processo ou um domínio de aplicativo, embora ele sempre pode consultar a interface para tomar uma decisão.  
  
 `pThread`  
 [in] Um ponteiro para uma interface ICorDebugThread que expõe o thread gerenciado em que ocorreu o evento de depuração.  
  
 Se o MDA ocorreu em uma não gerenciado de thread, o valor de `pThread` será nulo.  
  
 Você deve obter a ID do thread de sistema operacional (SO) do objeto MDA em si.  
  
 `pMDA`  
 [in] Um ponteiro para um [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface que expõe as informações de MDA.  
  
## <a name="remarks"></a>Comentários  
 Um MDA é um aviso de heurística e não exigir ação explícita do depurador, exceto chamada [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para retomar a execução do aplicativo que está sendo depurado.  
  
 O common language runtime (CLR) pode determinar qual MDAs são acionados e os dados que estão em qualquer determinado MDA a qualquer momento. Portanto, os depuradores não deverá criar qualquer funcionalidade que exigem padrões específicos de MDA.  
  
 MDAs podem ser enfileirados e acionados logo após o MDA é encontrado. Isso pode acontecer se o tempo de execução precisa esperar até que ele atinja um ponto de segurança para acionar o MDA, em vez de disparar o MDA quando ele encontra. Isso também significa que o tempo de execução pode disparar um número de MDAs em um único conjunto de retornos de chamada na fila (semelhantes a uma operação de evento "anexar").  
  
 Um depurador deve liberar a referência a um `ICorDebugMDA` instância imediatamente depois do retorno do `MDANotification` retorno de chamada, para permitir que o CLR reciclar a memória consumida por um MDA. Liberar a instância pode melhorar o desempenho se muitos MDAs são acionados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
