---
title: "Método ICorDebugThread::EnumerateChains"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
