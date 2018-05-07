---
title: Método ICorDebugThread::EnumerateChains
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caeb60c33580f7171a6959c3046cf7312868851b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadenumeratechains-method"></a>Método ICorDebugThread::EnumerateChains
Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha no objeto ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppChains`  
 [out] Um ponteiro para o endereço de uma `ICorDebugChainEnum` objeto que permite a enumeração de todos os a pilha encadeia neste thread, começando na cadeia de ativo (ou seja, o mais recente).  
  
## <a name="remarks"></a>Comentários  
 A cadeia da pilha representa a pilha de chamadas físico para o thread. As circunstâncias a seguir criar um limite de cadeia de pilha:  
  
-   Uma transição gerenciado para gerenciado ou não gerenciado para gerenciado.  
  
-   Uma alternância de contexto.  
  
-   Um sequestro de um thread de usuário do depurador.  
  
 No caso mais simples para um thread que está executando o código totalmente gerenciado em um único contexto, exista uma correspondência entre threads e cadeias de pilha.  
  
 Um depurador talvez queira reorganizar as pilhas de chamadas física de todos os threads em pilhas de chamadas lógicas. Isso envolve a classificação de cadeias de todos os threads por suas relações de chamador/receptor e reagrupá-los.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
