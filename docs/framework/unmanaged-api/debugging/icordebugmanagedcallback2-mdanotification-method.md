---
title: Método ICorDebugManagedCallback2::MDANotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90c805a5f1f1da990564034fc292562d5f933d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608083"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>Método ICorDebugManagedCallback2::MDANotification
Fornece notificação de que a execução de código encontrou um Assistente para depuração gerenciada (MDA) no aplicativo que está sendo depurado.  
  
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
 [in] Um ponteiro para um domínio de aplicativo no qual ocorreu o MDA ou de interface ICorDebugController que expõe o processo.  
  
 Um depurador não deve fazer suposições sobre se o controlador é um processo ou um domínio de aplicativo, embora ele sempre pode consultar a interface para a determinação.  
  
 `pThread`  
 [in] Um ponteiro para uma interface ICorDebugThread que expõe o thread gerenciado no qual ocorreu o evento de depuração.  
  
 Se o MDA ocorreu em uma não gerenciado de thread, o valor de `pThread` será nulo.  
  
 Você deve obter a ID do thread de sistema operacional (SO) do objeto MDA em si.  
  
 `pMDA`  
 [in] Um ponteiro para um [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface que expõe as informações de MDA.  
  
## <a name="remarks"></a>Comentários  
 Um MDA é um aviso de heurística e não requer nenhuma ação explícita do depurador, exceto para chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para retomar a execução do aplicativo que está sendo depurado.  
  
 O common language runtime (CLR) pode determinar qual MDAs são acionados e quais dados estão em qualquer determinado MDA a qualquer momento. Portanto, os depuradores não deverá criar qualquer funcionalidade que exigem os padrões MDA específicos.  
  
 Os MDAs podem ser enfileirados e acionados logo depois que o MDA é encontrado. Isso pode acontecer se o tempo de execução precisa esperar até que ela atinja um ponto seguro para acionar o MDA, em vez de disparar o MDA quando ele encontra. Isso também significa que o tempo de execução pode disparar um número de MDAs em um único conjunto de retornos de chamada na fila (semelhantes a uma operação de evento "anexar").  
  
 Um depurador deve liberar a referência a um `ICorDebugMDA` instância imediatamente depois de retornar do `MDANotification` retorno de chamada, para permitir que o CLR reciclar a memória consumida por um MDA. Liberação da instância pode melhorar o desempenho se MDAs muitos estão disparando.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
