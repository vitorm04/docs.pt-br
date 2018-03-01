---
title: "Método ICorDebugStepper::Step"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f921725d6794f08530a537462208264ced1dc089
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
