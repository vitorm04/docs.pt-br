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
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395839"
---
# <a name="icordebugvaluegetaddress-method"></a>Método ICorDebugValue::GetAddress
Obtém o endereço desse objeto "ICorDebugValue", que está no processo de ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAddress`  
 fora Ponteiro para um `CORDB_ADDRESS` objeto que especifica o endereço desse objeto de valor.  
  
## <a name="remarks"></a>Comentários  
 Se o valor não estiver disponível, será retornado 0 (zero). Isso pode acontecer se o valor for pelo menos parcialmente em registros ou armazenado em um identificador de coletor de lixo ( `GCHandle` ).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também
