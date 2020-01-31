---
title: Método ICorDebugStepper::SetRangeIL
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791745"
---
# <a name="icordebugsteppersetrangeil-method"></a>Método ICorDebugStepper::SetRangeIL
Define um valor que especifica se as chamadas para [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) passam valores de argumentos que são relativos ao código nativo ou em relação ao código MSIL (Microsoft Intermediate Language) do método que está sendo percorrido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIL`  
 no Defina como `true` para especificar que os intervalos são relativos ao código MSIL. Defina como `false` para especificar que os intervalos são relativos ao código nativo. O valor padrão é `true`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
