---
title: Método ICorDebugThread::GetCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762485"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>Método ICorDebugThread::GetCurrentException
Obtém um ponteiro de interface para um objeto de ICorDebugValue que representa uma exceção que está sendo atualmente gerada pelo código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppExceptionObject`  
 [out] Um ponteiro para o endereço de um `ICorDebugValue` que representa a exceção que está sendo atualmente gerada pelo objeto de código gerenciado.  
  
## <a name="remarks"></a>Comentários  
 O objeto de exceção continuará a existir desde o momento em que a exceção é lançada até o final do `catch` bloco. Uma avaliação de função, que é executada pelos métodos ICorDebugEval, limpará horizontalmente o objeto de exceção na instalação e restaurá-lo após a conclusão.  
  
 Exceções podem ser aninhadas (por exemplo, se uma exceção é gerada em um filtro ou em uma avaliação de função), portanto, pode haver várias exceções pendentes em um único thread. `GetCurrentException` Retorna a exceção mais atual.  
  
 O objeto de exceção e o tipo podem mudar durante a vida útil da exceção. Por exemplo, depois que uma exceção do tipo x é gerada, o common language runtime (CLR) pode ficar sem memória e promovê-lo para uma exceção de falta de memória.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
