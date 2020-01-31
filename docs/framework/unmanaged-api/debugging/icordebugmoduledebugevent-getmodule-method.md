---
title: 'Método ICorDebugModuleDebugEvent:: GetModule'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792905"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>Método ICorDebugModuleDebugEvent:: GetModule
Obtém o módulo mesclado que acabou de ser carregado ou descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppModule`  
 fora Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que acabou de ser carregado ou descarregado.  
  
## <a name="remarks"></a>Comentários  
 Você pode chamar o método [GetEventKind](icordebugdebugevent-geteventkind-method.md) para determinar se o módulo foi carregado ou descarregado.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
