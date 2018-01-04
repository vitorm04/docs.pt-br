---
title: "Método ICorDebugStepper::StepRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a>Método ICorDebugStepper::StepRange
Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e para retornar quando atingir código além do último dos intervalos especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bStepIn`  
 [in] Definido como `true` para entrar em uma função que é chamada no thread. Definido como `false` ao passar sobre a função.  
  
 `ranges`  
 [in] Uma matriz de estruturas COR_DEBUG_STEP_RANGE, cada uma delas Especifica um intervalo.  
  
 `cRangeCount`  
 [in] O tamanho do `ranges` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `StepRange` método funciona como o [ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) método, exceto que ela não for concluída até que o código fora do intervalo especificado for atingido.  
  
 Isso pode ser mais eficiente do que o passo a passo de uma instrução de cada vez. Os intervalos são especificados como uma lista de pares de deslocamento do início do quadro do seletor.  
  
 Os intervalos são relativas ao código do Microsoft intermediate language (MSIL) de um método. Chamar [: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) com `false` para tornar os intervalos em relação o código nativo de um método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
