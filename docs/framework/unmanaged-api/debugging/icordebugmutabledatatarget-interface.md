---
title: Interface ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatarget-interface"></a>Interface ICorDebugMutableDataTarget
Estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para oferecer suporte a destinos de dados mutável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ContinueStatusChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Altera o status de continuação para o evento de depuração pendentes no thread especificado.|  
|[Método SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Define o contexto (valores do registro) de um thread.|  
|[Método WriteVirtual](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Grava a memória no espaço de endereço de processo de destino.|  
  
## <a name="remarks"></a>Comentários  
 Essa extensão para o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pode ser implementada pelas ferramentas de depuração que deseja modificar o processo de destino (por exemplo, para realizar a depuração invasivo ao vivo).  
  
 Todos esses métodos são opcionais no sentido de que nenhuma funcionalidade de depuração com base em inspeção principal é perdida por não implementa esta interface ou a falha de chamadas para esses métodos.  Qualquer falha `HRESULT` entre esses métodos serão propagadas como o `HRESULT` na chamada de método ICorDebug.  
  
 Observe que uma única chamada de método ICorDebug pode resultar em várias mutações e que não há nenhum mecanismo para garantir relacionados mutações são aplicadas de forma transacional (AON).  Isso significa que, se uma mutação falhar depois que outras pessoas (para a mesma chamada ICorDebug) tiveram êxito, o processo de destino poderão ser deixado em um estado inconsistente e depuração pode se tornar não confiável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
