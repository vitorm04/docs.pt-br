---
title: Método ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0a273c54559e8e297e09740ba9c770ce12d72d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760590"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>Método ICorDebugStepper::SetUnmappedStopMask
Define um valor que especifica o tipo de código não mapeado no qual a execução será interrompida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mask`  
 [in] Um valor de enumeração CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual o depurador interromperá a execução.  
  
 O valor padrão é STOP_OTHER_UNMAPPED. O valor STOP_UNMANAGED só é válido com a depuração de interoperabilidade.  
  
## <a name="remarks"></a>Comentários  
 Quando o depurador encontra uma just-in-time (compilação JIT) que não tem nenhum mapeamento correspondente para Microsoft intermediate language (MSIL), ele interromperá a execução se o sinalizador que especifica esse tipo de código não mapeado tiver sido definido; Caso contrário, depuração de modo transparente continua.  
  
 Se o depurador não usa um seletor para inserir um método, em seguida, ele não necessariamente passar por código não mapeado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
