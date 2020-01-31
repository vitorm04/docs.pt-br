---
title: Método ICorDebugProcess2::ClearUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: e2aaf902afd71a4a81f7d64ef3fec046aacc91fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792526"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>Método ICorDebugProcess2::ClearUnmanagedBreakpoint
Remove um ponto de interrupção definido anteriormente no endereço fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 no Um valor `CORDB_ADDRESS` que especifica o endereço no qual o ponto de interrupção foi definido.  
  
## <a name="remarks"></a>Comentários  
 O ponto de interrupção especificado teria sido definido anteriormente por uma chamada anterior para [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 O método `ClearUnmanagedBreakpoint` pode ser chamado enquanto o processo que está sendo depurado está em execução.  
  
 O método `ClearUnmanagedBreakpoint` retornará um código de falha se o depurador estiver anexado no modo somente gerenciado ou se não existir nenhum ponto de interrupção no endereço especificado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
