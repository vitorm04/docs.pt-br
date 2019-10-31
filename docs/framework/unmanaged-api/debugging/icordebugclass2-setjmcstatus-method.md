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
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125698"
---
# <a name="icordebugclass2setjmcstatus-method"></a>Método ICorDebugClass2::SetJMCStatus
Para cada método da classe, define um valor que indica se o método é um código definido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIsJustMyCode`  
 no Defina como `true` para indicar que o método é um código definido pelo usuário; caso contrário, defina como `false`.  
  
## <a name="remarks"></a>Comentários  
 Um stepper JMC (Just-the-code) ignorará o código não definido pelo usuário. O código definido pelo usuário deve ser um subconjunto de código depurável.  
  
 `SetJMCStatus` retornará um valor HRESULT de S_FALSE se ele falhar ao definir o valor de qualquer método, mesmo que ele defina o valor para todos os outros métodos com êxito.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
