---
title: Estrutura COR_TYPEID
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273992"
---
# <a name="cor_typeid-structure"></a>Estrutura COR_TYPEID
Contém um identificador de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`token1`|O primeiro token.|  
|`token2`|O segundo token.|  
  
## <a name="remarks"></a>Comentários  
 A `COR_TYPEID` estrutura é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo. Em seguida, ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item. Por exemplo, enumerando um objeto [ICorDebugHeapEnum](icordebugheapenum-interface.md) , você pode recuperar objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) individuais que representam objetos individuais no heap gerenciado. Em seguida, você pode `COR_TYPEID` passar o valor `COR_HEAPOBJECT.type` do campo para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) para recuperar um objeto ICorDebugType que fornece informações de tipo sobre o objeto.  
  
 Um `COR_TYPEID` objeto deve ser opaco. Seus campos individuais não devem ser acessados ou manipulados. Seu uso exclusivo é como um identificador que é fornecido como um `out` parâmetro em uma chamada de método e que, por sua vez, pode ser passado para outros métodos para fornecer informações adicionais.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
