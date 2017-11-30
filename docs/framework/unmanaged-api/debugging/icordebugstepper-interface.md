---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83d394669270eb26b33e084b20a621e18b5b14aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper Interface1
Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Faz com que essa `ICorDebugStepper` para cancelar o último comando de etapa recebido.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Obtém um valor que indica se este `ICorDebugStepper` está executando uma etapa.|  
|[Método SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Define um valor de CorDebugIntercept que especifica os tipos de código que são entrado em.|  
|[Método SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Define um valor que indica se chamadas para [: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passar valores de argumento em relação ao código nativo ou em código do Microsoft intermediate language (MSIL) do método que está sendo percorrido.|  
|[Método SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Define um valor de CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual a execução será interrompida.|  
|[Método Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Faz com que essa `ICorDebugStepper` para percorrer por meio de seu recipiente thread e, opcionalmente, para continuar a depuração único por meio das funções que são chamadas de dentro do thread.|  
|[Método StepOut](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Faz com que essa `ICorDebugStepper` para percorrer por meio de seu recipiente thread e concluído quando o quadro atual retorna o controle para o quadro de chamada.|  
|[Método StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Faz com que essa `ICorDebugStepper` para percorrer por meio de seu recipiente thread e para retornar quando atingir código além do último dos intervalos especificados.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugStepper` interface tem as seguintes finalidades:  
  
-   Ele atua como um identificador entre um comando de depuração que é emitido e a conclusão desse comando.  
  
-   Ele fornece uma interface central para encapsular todo o passo a passo que pode ser executada.  
  
-   Ele fornece uma maneira de cancelar prematuramente uma operação de revisão.  
  
 Pode haver mais de um seletor por thread. Por exemplo, um ponto de interrupção pode ser obtido ao passar sobre uma função, e o usuário deseja iniciar uma nova operação de revisão nessa função. Cabe o depurador para determinar como tratar essa situação. O depurador talvez queira cancelar a operação de revisão original ou aninhar as duas operações. O `ICorDebugStepper` interface dá suporte a ambas as opções.  
  
 Um seletor pode migrar entre threads se o common language runtime (CLR) faz uma chamada de thread cruzado, empacotada.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
