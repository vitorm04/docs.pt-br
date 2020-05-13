---
title: Método ICorDebugStepper::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: faddf30248b58c68037635480d8977f22ad077d0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379016"
---
# <a name="icordebugstepperisactive-method"></a>Método ICorDebugStepper::IsActive
Obtém um valor que indica se este ICorDebugStepper está executando uma etapa no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbActive`  
 fora Retorna `true` se stepper está executando uma etapa no momento; caso contrário, retorna `false` .  
  
## <a name="remarks"></a>Comentários  
 Qualquer ação de etapa permanece ativa até que o depurador receba uma chamada [ICorDebugManagedCallback:: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , que desativa automaticamente o stepper. Um stepper também pode ser desativado prematuramente chamando [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) antes que a condição de retorno de chamada seja atingida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
