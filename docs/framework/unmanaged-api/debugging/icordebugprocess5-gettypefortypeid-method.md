---
title: "Método ICorDebugProcess5::GetTypeForTypeID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeForTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08c4b72b5b37d9e3a2a2e19bad9e79449906b495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>Método ICorDebugProcess5::GetTypeForTypeID
Converte um identificador de tipo para um valor de ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 [in] O identificador de tipo.  
  
 `ppType`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugType.  
  
## <a name="remarks"></a>Comentários  
 Em alguns casos, os métodos que retornam um identificador de tipo podem retornar um valor nulo `COR_TYPEID` valor. Se esse valor é passado como o `id` argumento, o `GetTypeForTypeID` método falhará e retornará `E_FAIL`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
