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
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760572"
---
# <a name="icordebugstepperstep-method"></a>Método ICorDebugStepper::Step
Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e, opcionalmente, para continuar a depuração de único por meio de funções que são chamadas de dentro do thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bStepIn`  
 [in] Definido como `true` para entrar em uma função que é chamada dentro do thread. Definido como `false` para ignorar a função.  
  
## <a name="remarks"></a>Comentários  
 A etapa é concluída quando o common language runtime executa a próxima instrução gerenciada no quadro deste seletor. Se `Step` é chamado em um seletor, que não está no código gerenciado, a etapa será concluída quando a próxima instrução de código gerenciado é executada pelo thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
