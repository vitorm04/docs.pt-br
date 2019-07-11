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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760527"
---
# <a name="icordebugsteppersteprange-method"></a>Método ICorDebugStepper::StepRange
Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e para retornar quando ele atinge o código além do último dos intervalos especificados.  
  
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
 [in] Definido como `true` para entrar em uma função que é chamada dentro do thread. Definido como `false` para ignorar a função.  
  
 `ranges`  
 [in] Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada um deles especifica um intervalo.  
  
 `cRangeCount`  
 [in] O tamanho do `ranges` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `StepRange` método funciona como o [ICorDebugStepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) método, exceto que ela não for concluída até que o código fora do intervalo especificado for atingido.  
  
 Isso pode ser mais eficiente do que o passo a passo de uma instrução por vez. Intervalos são especificados como uma lista de pares de deslocamento do início do quadro do seletor.  
  
 Os intervalos são em relação ao código do Microsoft intermediate language (MSIL) de um método. Chame [ICorDebugStepper:: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos em relação ao código nativo de um método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
