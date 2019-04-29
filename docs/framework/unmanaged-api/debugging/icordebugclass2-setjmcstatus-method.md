---
title: Método ICorDebugClass2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750612"
---
# <a name="icordebugclass2setjmcstatus-method"></a>Método ICorDebugClass2::SetJMCStatus
Para cada método da classe, define um valor que indica se o método é o código definido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIsJustMyCode`  
 [in] Definido como `true` para indicar que o método é definido pelo usuário de código; caso contrário, é definido como `false`.  
  
## <a name="remarks"></a>Comentários  
 Um seletor do just my code (JMC) vai ignorar o código definido pelo usuário. Código definido pelo usuário deve ser um subconjunto de código depurável.  
  
 `SetJMCStatus` Retorna um valor HRESULT de S_FALSE se ele falhar ao definir o valor de qualquer método, mesmo que define o valor para todos os outros métodos com êxito.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
