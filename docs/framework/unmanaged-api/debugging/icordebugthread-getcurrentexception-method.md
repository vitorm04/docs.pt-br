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
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379766"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>Método ICorDebugThread::GetCurrentException
Obtém um ponteiro de interface para um objeto ICorDebugValue que representa uma exceção que está sendo lançada atualmente pelo código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppExceptionObject`  
 fora Um ponteiro para o endereço de um `ICorDebugValue` objeto que representa a exceção que está sendo lançada atualmente pelo código gerenciado.  
  
## <a name="remarks"></a>Comentários  
 O objeto de exceção existirá a partir do momento em que a exceção é lançada até o final do `catch` bloco. Uma avaliação de função, que é executada pelos métodos ICorDebugEval, limpará o objeto de exceção na instalação e o restaurará na conclusão.  
  
 Exceções podem ser aninhadas (por exemplo, se uma exceção for lançada em um filtro ou em uma avaliação de função), portanto pode haver várias exceções pendentes em um único thread. `GetCurrentException`Retorna a exceção mais recente.  
  
 O tipo e o objeto de exceção podem ser alterados durante a vida útil da exceção. Por exemplo, após uma exceção do tipo x ser lançada, o Common Language Runtime (CLR) pode ficar sem memória e promovê-lo para uma exceção de memória insuficiente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
