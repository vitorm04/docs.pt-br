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
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763731"
---
# <a name="icordebugstepper-interface"></a>Interface ICorDebugStepper
Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Faz com que essa `ICorDebugStepper` para cancelar o último comando etapa recebido.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Obtém um valor que indica se este `ICorDebugStepper` está executando uma etapa.|  
|[Método SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Define um valor de CorDebugIntercept que especifica os tipos de código são entrados.|  
|[Método SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Define um valor que indica se chamadas para [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar valores de argumento em relação ao código nativo ou ao código do Microsoft intermediate language (MSIL) do método que está sendo percorrido.|  
|[Método SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Define um valor de CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual a execução será interrompida.|  
|[Método Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Faz com que essa `ICorDebugStepper` a etapa única por meio de seu recipiente thread e, opcionalmente, para continuar a depuração de único por meio de funções que são chamadas de dentro do thread.|  
|[Método StepOut](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Faz com que essa `ICorDebugStepper` único-percorra seu recipiente thread e concluído quando o quadro atual retorna o controle para o quadro de chamada.|  
|[Método StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Faz com que essa `ICorDebugStepper` a etapa única por meio de seu recipiente thread e para retornar quando ele atinge o código além do último dos intervalos especificados.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugStepper` interface tem as seguintes finalidades:  
  
- Ele atua como um identificador entre um comando de depuração é emitido e a conclusão desse comando.  
  
- Ele fornece uma interface central para encapsular todo o passo a passo que pode ser executada.  
  
- Ele fornece uma maneira de cancelar prematuramente uma operação de passo a passo.  
  
 Pode haver mais de um seletor por thread. Por exemplo, um ponto de interrupção pode ser obtido ao passar sobre uma função, e o usuário deseja iniciar uma nova operação de deslocamento dentro dessa função. É responsabilidade do depurador para determinar como lidar com essa situação. O depurador poderá cancelar a operação de passo a passo original ou aninhar as duas operações. O `ICorDebugStepper` interface dá suporte a ambas as opções.  
  
 Um seletor pode migrar entre threads, se o common language runtime (CLR) faz uma chamada de thread cruzado, com marshaling.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
