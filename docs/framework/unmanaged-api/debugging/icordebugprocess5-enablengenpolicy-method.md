---
title: Método ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792457"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>Método ICorDebugProcess5::EnableNGENPolicy
Define um valor que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ePolicy`  
 no Uma constante [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se a política for definida com êxito, o método retornará `S_OK`. Se `ePolicy` estiver fora do intervalo dos valores enumerados definidos por [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), o método retornará `E_INVALIDARG` e a chamada do método não terá efeito. Se a política do gerador de imagem nativa (NGen. exe) não puder ser atualizada, o método retornará `E_FAIL`.  
  
 O método `ICorDebugProcess5::EnableNGenPolicy` pode ser chamado a qualquer momento durante o tempo de vida do processo. A política está em vigor para todos os módulos que são carregados depois que a política é definida.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess5](icordebugprocess5-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
