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
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188702"
---
# <a name="icordebugdatatarget-interface"></a>Interface ICorDebugDataTarget
Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Fornece informações sobre a plataforma, incluindo a arquitetura do processador e sistema operacional, que está executando o processo de destino.|  
|[Método ReadVirtual](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Obtém um bloco de memória contígua, iniciando no endereço especificado e retorna-o no buffer fornecido.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Solicita o contexto do thread atual para o thread especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugDataTarget` e seus métodos têm as seguintes características:  
  
-   Os serviços de depuração chamar métodos nessa interface para acessar a memória e outros dados no processo de destino.  
  
-   O cliente do depurador deve implementar essa interface conforme apropriado para o destino específico (por exemplo, um processo dinâmico ou um despejo de memória).  
  
-   O `ICorDebugDataTarget` métodos podem ser chamados somente de dentro de métodos implementados em outros `ICorDebug*` interfaces. Isso garante que o cliente de depurador tem controle sobre qual thread é invocado e quando.  
  
-   O `ICorDebugDataTarget` implementação deve sempre retornar informações atualizadas sobre o destino.  
  
 O processo de destino deve ser interrompido e não é alterado de qualquer forma durante `ICorDebug*` interfaces (e, portanto, `ICorDebugDataTarget` métodos) estão sendo chamados. Se o destino é um processo dinâmico e as alterações de estado, o [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método precisa ser chamado novamente para fornecer uma instância de ICorDebugProcess de substituição.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
