---
title: Método ICorDebugManagedCallback3::CustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 078f90387a475559067d402610ec264f4076ae01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793260"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>Método ICorDebugManagedCallback3::CustomNotification
Indica que uma notificação de depurador personalizada foi gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pThread`  
 no Um ponteiro para o thread que gerou a notificação.  
  
 `pAppDomain`  
 no Um ponteiro para o domínio do aplicativo que contém o thread que gerou a notificação.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Uma chamada subsequente para o método [ICorDebugThread4:: GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) recupera o objeto de thread que foi passado para o método <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>. O tipo do objeto de thread deve ter sido habilitado anteriormente chamando o método [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) . O depurador pode ler parâmetros específicos de tipo dos campos do objeto de thread e pode armazenar respostas em campos.  
  
 A interface [ICorDebug](icordebug-interface.md) impõe nenhuma política sobre os tipos de notificações ou seu conteúdo, e a semântica das notificações é estritamente um contrato entre os depuradores, os aplicativos e a .NET Framework.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
