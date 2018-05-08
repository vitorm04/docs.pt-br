---
title: Método ICorDebugStepper::Step
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2d282e27ec5068fa6fe7f58ba95458fdc219972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstepperstep-method"></a>Método ICorDebugStepper::Step
Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e, opcionalmente, para continuar a depuração único por meio das funções que são chamadas de dentro do thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bStepIn`  
 [in] Definido como `true` para entrar em uma função que é chamada no thread. Definido como `false` ao passar sobre a função.  
  
## <a name="remarks"></a>Comentários  
 A etapa é concluída quando o common language runtime executa a próxima instrução gerenciada no quadro deste seletor. Se `Step` é chamado em um seletor, que não está no código gerenciado, a etapa será concluída quando a próxima instrução do código gerenciado é executada pelo thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
