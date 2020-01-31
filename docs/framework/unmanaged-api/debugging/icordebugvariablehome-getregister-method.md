---
title: 'Método ICorDebugVariableHome:: getregister'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790983"
---
# <a name="icordebugvariablehomegetregister-method"></a>Método ICorDebugVariableHome:: getregister
Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRegister`  
 fora Um valor de enumeração CorDebugRegister que indica o registro para uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna os seguintes valores:  
  
|Value|Descrição|  
|-----------|-----------------|  
|`S_OK`|A variável está no registro indicado pelo argumento `pRegister`.|  
|`E_FAIL`|A variável não está em um local de registro ou relativo ao registro.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Enumeração VariableLocationType](variablelocationtype-enumeration.md)
- [Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
