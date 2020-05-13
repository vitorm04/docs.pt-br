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
ms.openlocfilehash: b040d9454a5a3a0d550bb645953c783357419f73
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379488"
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
 no Defina como entrar `true` em uma função que é chamada dentro do thread. Defina como `false` para percorrer a função.  
  
 `ranges`  
 no Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada uma delas especifica um intervalo.  
  
 `cRangeCount`  
 no O tamanho da `ranges` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `StepRange` método funciona como o método [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , exceto que ele não é concluído até que o código fora do intervalo especificado seja atingido.  
  
 Isso pode ser mais eficiente do que a depuração de uma instrução por vez. Os intervalos são especificados como uma lista de pares de deslocamento do início do quadro do stepper.  
  
 Os intervalos são relativos ao código da MSIL (Microsoft Intermediate Language) de um método. Chame [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos relativos ao código nativo de um método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
