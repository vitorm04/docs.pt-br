---
title: Enumeração CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: 99fc89d1aee6c9f0fbffc193e12ce563e820f268
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789276"
---
# <a name="cordebugrecordformat-enumeration"></a>Enumeração CorDebugRecordFormat
Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|Os dados serão um registro de exceção do Windows de 32 bits.|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|Os dados serão um registro de exceção do Windows de 64 bits.|  
  
## <a name="remarks"></a>Comentários  
 Um membro da enumeração `CorDebugRecordFormat` é passado para o método [DecodeEvent](icordebugprocess6-decodeevent-method.md) para indicar o formato da matriz de bytes em seu argumento `pRecord`.  
  
> [!NOTE]
> Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Declarando enumerações](debugging-enumerations.md)
