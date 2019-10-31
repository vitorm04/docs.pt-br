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
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132303"
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
 A estrutura de `COR_TYPEID` é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo. Em seguida, ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item. Por exemplo, enumerando um objeto [ICorDebugHeapEnum](icordebugheapenum-interface.md) , você pode recuperar objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) individuais que representam objetos individuais no heap gerenciado. Em seguida, você pode passar o valor `COR_TYPEID` do campo `COR_HEAPOBJECT.type` para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) para recuperar um objeto ICorDebugType que fornece informações de tipo sobre o objeto.  
  
 Um objeto `COR_TYPEID` destina-se a ser opaco. Seus campos individuais não devem ser acessados ou manipulados. Seu uso exclusivo é como um identificador que é fornecido como um parâmetro de `out` em uma chamada de método e que, por sua vez, pode ser passado para outros métodos para fornecer informações adicionais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
