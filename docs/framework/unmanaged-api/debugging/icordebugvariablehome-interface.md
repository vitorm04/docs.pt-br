---
title: Interface ICorDebugVariableHome
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorDebugVariableHome
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome
helpviewer_keywords: ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea8f4033a6b0878288c49d6f6d964eb40675162d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehome-interface"></a>Interface ICorDebugVariableHome
Representa um argumento de uma função ou variável local.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetArgumentIndex](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|Obtém o índice de um argumento de função.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|Obtém a instância de "ICorDebugCode" que contém essa `ICorDebugVariableHome` objeto.|  
|[Método GetLiveRange](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|Obtém o intervalo nativo através da qual esta variável está ativo.|  
|[Método GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|Obtém o tipo de local nativo da variável.|  
|[Método GetOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|Obtém o deslocamento do registro base para uma variável.|  
|[Método GetRegister](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|Obtém o registro que contém uma variável com um tipo de local de `VLT_REGISTER`e o registro de base para uma variável com um tipo de local de `VLT_REGISTER_RELATIVE`.|  
|[Método GetSlotIndex](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|Obtém o índice de slot gerenciado de uma variável local.|  
  
## <a name="example"></a>Exemplo  
 O fragmento de código a seguir usa o [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objeto chamado `pCode4`.  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Interface ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
