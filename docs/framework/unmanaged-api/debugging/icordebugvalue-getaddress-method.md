---
title: Método ICorDebugValue::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c0fa19841580c7cfe8902577c3f756712a35893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420648"
---
# <a name="icordebugvaluegetaddress-method"></a>Método ICorDebugValue::GetAddress
Obtém o endereço do objeto "ICorDebugValue", que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [out] Ponteiro para uma `CORDB_ADDRESS` objeto que especifica o endereço do objeto de valor.  
  
## <a name="remarks"></a>Comentários  
 Se o valor estiver disponível, será retornado 0 (zero). Isso pode acontecer se o valor for pelo menos parcialmente nos registros ou armazenados em um identificador de coletor de lixo (`GCHandle`).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
