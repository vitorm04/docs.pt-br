---
title: "Método ICorDebugVariableHome::GetRegister"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a>Método ICorDebugVariableHome::GetRegister
Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRegister`  
 [out] Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna os seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A variável está no registro indicado pelo `pRegister` argumento.|  
|`E_FAIL`|A variável não está em um registro ou um local relativo ao registro.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [Interface ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
