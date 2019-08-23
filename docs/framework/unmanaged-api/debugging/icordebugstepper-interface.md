---
title: Interface ICorDebugStepper
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962693"
---
# <a name="icordebugstepper-interface"></a>Interface ICorDebugStepper
Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Faz com `ICorDebugStepper` que isso cancele o comando da última etapa recebido.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Obtém um valor que indica se este `ICorDebugStepper` está executando uma etapa no momento.|  
|[Método SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Define um valor CorDebugIntercept que especifica os tipos de código que são percorridos.|  
|[Método SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Define um valor que indica se as chamadas para [ICorDebugStepper:: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passam valores de argumentos relativos ao código nativo ou ao código MSIL (Microsoft Intermediate Language) do método que está sendo percorrido.|  
|[Método SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Define um valor CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual a execução será interrompida.|  
|[Método Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e, opcionalmente, para continuar percorrendo por meio de funções que são chamadas dentro do thread.|  
|[Método StepOut](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e para concluir quando o quadro atual retorna o controle para o quadro de chamada.|  
|[Método StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e retorna quando ele atinge o código após o último dos intervalos especificados.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugStepper` interface atende às seguintes finalidades:  
  
- Ele atua como um identificador entre um comando Step que é emitido e a conclusão desse comando.  
  
- Ele fornece uma interface central para encapsular toda a depuração que pode ser executada.  
  
- Ele fornece uma maneira de cancelar prematuramente uma operação de depuração.  
  
 Pode haver mais de um stepper por thread. Por exemplo, um ponto de interrupção pode ser atingido durante a depuração em uma função, e o usuário pode desejar iniciar uma nova operação de depuração dentro dessa função. Cabe ao depurador determinar como lidar com essa situação. O depurador pode querer cancelar a operação de depuração original ou aninhar as duas operações. A `ICorDebugStepper` interface dá suporte a ambas as opções.  
  
 Um stepper poderá migrar entre threads se o Common Language Runtime (CLR) fizer uma chamada de marshaling em vários threads.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
