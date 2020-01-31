---
title: Método ICorDebugStepper::StepRange
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791717"
---
# <a name="icordebugsteppersteprange-method"></a>Método ICorDebugStepper::StepRange
Faz com que esse ICorDebugStepper faça uma única etapa por meio de seu thread que o contém e retorne quando ele atinge o código além do último intervalo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bStepIn`  
 no Defina como `true` para entrar em uma função que é chamada dentro do thread. Defina como `false` para percorrer a função.  
  
 `ranges`  
 no Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada uma delas especifica um intervalo.  
  
 `cRangeCount`  
 no O tamanho da matriz de `ranges`.  
  
## <a name="remarks"></a>Comentários  
 O método `StepRange` funciona como o método [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , exceto que ele não é concluído até que o código fora do intervalo especificado seja atingido.  
  
 Isso pode ser mais eficiente do que a depuração de uma instrução por vez. Os intervalos são especificados como uma lista de pares de deslocamento do início do quadro do stepper.  
  
 Os intervalos são relativos ao código da MSIL (Microsoft Intermediate Language) de um método. Chame [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos relativos ao código nativo de um método.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
