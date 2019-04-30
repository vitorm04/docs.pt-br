---
title: Método ICorDebugStepper::StepOut
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987422"
---
# <a name="icordebugstepperstepout-method"></a>Método ICorDebugStepper::StepOut
Faz com que esse ICorDebugStepper a etapa única por meio de seu recipiente thread e para ser concluído quando o quadro atual retorna o controle para o quadro de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Comentários  
 Um `StepOut` operação será concluída após retornar normalmente de quadro atual para o quadro de chamada.  
  
 Se `StepOut` é chamado quando em código não gerenciado, a etapa será concluída quando o quadro atual retorna para o código gerenciado que o chamou.  
  
 No .NET Framework versão 2.0, não use `StepOut` com o STOP_UNMANAGED sinalizador definido porque ele falhará. (Use [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) definir sinalizadores de passo a passo.) Depuradores de interoperabilidade devem sair para código nativo em si.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
