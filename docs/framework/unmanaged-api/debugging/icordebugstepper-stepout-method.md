---
title: "Método ICorDebugStepper::StepOut"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d6462f166e9c734dacc7ebee13cb82e3b12158b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstepout-method"></a>Método ICorDebugStepper::StepOut
Faz com que este ICorDebugStepper para percorrer por meio de seu recipiente thread e concluir quando o quadro atual retorna o controle para o quadro de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Comentários  
 Um `StepOut` operação será concluída após o retorno normalmente do quadro atual para o quadro de chamada.  
  
 Se `StepOut` é chamado quando em código não gerenciado, a etapa será concluída quando o quadro atual retorna para o código gerenciado que o chamou.  
  
 No .NET Framework versão 2.0, não use `StepOut` com o STOP_UNMANAGED o sinalizador será definido porque ele falhará. (Use [: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores para depuração.) Interoperabilidade depuradores devem sair para código nativo próprios.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
