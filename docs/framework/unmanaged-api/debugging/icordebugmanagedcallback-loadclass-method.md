---
title: Método ICorDebugManagedCallback::LoadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: cc5a2e1de79d6ba04ff3bf2bf86e0cb7ce9a5c0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788384"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>Método ICorDebugManagedCallback::LoadClass
Notifica o depurador de que uma classe foi carregada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a classe foi carregada.  
  
 `c`  
 no Um ponteiro para um objeto ICorDebugClass que representa a classe.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada ocorrerá somente se o carregamento da classe tiver sido habilitado para o módulo que contém a classe. O carregamento de classe é sempre habilitado para módulos dinâmicos.  
  
 O retorno de chamada `LoadClass` fornece um tempo apropriado para associar pontos de interrupção a classes recém-criadas em módulos dinâmicos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método UnloadClass](icordebugmanagedcallback-unloadclass-method.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
