---
title: "Método ICorDebugClass2::SetJMCStatus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da9f61bd9a652b4c8e340ddecdee4b48bbdb086e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a>Método ICorDebugClass2::SetJMCStatus
Para cada método da classe, define um valor que indica se o método é código definido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bIsJustMyCode`  
 [in] Definido como `true` para indicar que o método é definido pelo usuário código; caso contrário, é definido como `false`.  
  
## <a name="remarks"></a>Comentários  
 Um seletor de (JMC) apenas meu código vai ignorar código definido pelo usuário. Código definido pelo usuário deve ser um subconjunto de código depurável.  
  
 `SetJMCStatus`Retorna um valor HRESULT S_FALSE se ele falhar ao definir o valor de qualquer método, mesmo que ele define o valor para todos os outros métodos com êxito.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
