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
ms.openlocfilehash: e01f94e9574ebc032bc45490fd88ff92e9104aa3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994039"
---
# <a name="icordebugthreadenumeratechains-method"></a>Método ICorDebugThread::EnumerateChains
Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste objeto ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppChains`  
 [out] Um ponteiro para o endereço de um `ICorDebugChainEnum` objeto que permite a enumeração de todos os a pilha encadeia neste thread, começando na cadeia de ativo (ou seja, o mais recente).  
  
## <a name="remarks"></a>Comentários  
 A cadeia da pilha representa a pilha de chamadas física para o thread. As circunstâncias a seguir criar um limite de cadeia de pilha:  
  
- Uma transição para gerenciado ou não gerenciado para gerenciado.  
  
- A alternância de contexto.  
  
- Um sequestro de um thread de usuário do depurador.  
  
 No caso mais simples para um thread que está executando código puramente gerenciado em um único contexto, uma correspondência direta existirá entre os threads e cadeias de pilha.  
  
 Um depurador talvez queira reorganizar as pilhas de chamadas física de todos os threads em pilhas de chamadas lógicas. Isso envolveria a classificação de cadeias de todos os threads por suas relações de chamador/receptor e reagrupá-los.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
