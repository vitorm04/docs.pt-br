---
title: Interface ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930830"
---
# <a name="icordebugdatatarget-interface"></a>Interface ICorDebugDataTarget
Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.|  
|[Método ReadVirtual](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Obtém um bloco de memória contígua a partir do endereço especificado e a retorna no buffer fornecido.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Solicita o contexto de thread atual para o thread especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugDataTarget`e seus métodos têm as seguintes características:  
  
- Os serviços de depuração chamam os métodos nessa interface para acessar a memória e outros dados no processo de destino.  
  
- O cliente do depurador deve implementar essa interface conforme apropriado para o destino específico (por exemplo, um processo ao vivo ou um despejo de memória).  
  
- Os `ICorDebugDataTarget` métodos podem ser invocados somente de dentro de métodos implementados em outras `ICorDebug*` interfaces. Isso garante que o cliente do depurador tenha controle sobre qual thread ele é invocado e quando.  
  
- A `ICorDebugDataTarget` implementação sempre deve retornar informações atualizadas sobre o destino.  
  
 O processo de destino deve ser interrompido e não alterado de nenhuma forma `ICorDebug*` enquanto as interfaces ( `ICorDebugDataTarget` e, portanto, os métodos) estão sendo chamadas. Se o destino for um processo ao vivo e seu estado for alterado, o método [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) precisará ser chamado novamente para fornecer uma instância de ICorDebugProcess substituta.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
