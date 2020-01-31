---
title: Enumeração VariableLocationType
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790306"
---
# <a name="variablelocationtype-enumeration"></a>Enumeração VariableLocationType
Indica o tipo de local nativo de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`VLT_REGISTER`|A variável está em um registro.|  
|`VLT_REGISTER_RELATIVE`|A variável está em um local de memória relativa ao registro.|  
|`VLT_INVALID`|A variável não é armazenada em um local de memória de registro ou de registro relativo.|  
  
## <a name="remarks"></a>Comentários  
 Um membro da enumeração `VariableLocationType` é retornado pelo método [ICorDebugVariableHome:: Getlocationtype](icordebugvariablehome-getlocationtype-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Declarando enumerações](debugging-enumerations.md)
