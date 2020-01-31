---
title: Método ICorDebugThread3::CreateStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791409"
---
# <a name="icordebugthread3createstackwalk-method"></a>Método ICorDebugThread3::CreateStackWalk
Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppStackWalk`  
 fora Um ponteiro para o endereço do objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O objeto `ICorDebugStackWalk` foi criado com êxito.|  
|{1&gt;E_FAIL&lt;1}|O objeto `ICorDebugStackWalk` não foi criado.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Se o método `CreateStackWalk` for executado com sucesso, o contexto do objeto de `ICorDebugStackWalk` retornado será definido como o contexto atual do thread.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
