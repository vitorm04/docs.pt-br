---
title: Estrutura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: 197c33511a474eb8291e4361ebb3c21fb3720cae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789419"
---
# <a name="cordebugehclause-structure"></a>Estrutura CorDebugEHClause
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Representa uma cláusula de manipulação de exceção (EH) para um determinado código de linguagem intermediária (IL).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`Flags`|Um campo de bits que descreve as informações de exceção na cláusula EH. Para obter mais informações, consulte a seção Comentários.|  
|`TryOffset`|O deslocamento, em bytes, do bloco `try` a partir do início do corpo do método.|  
|`TryLength`|O tamanho, em bytes, do bloco `try`.|  
|`HandlerOffset`|A localização do manipulador desse bloco `try`.|  
|`HandlerLength`|O tamanho, em bytes, do código do manipulador.|  
|`ClassToken`|O token de metadados para um manipulador de exceção com base em tipo.|  
|`FilterOffset`|O deslocamento, em bytes, do início do corpo do método para um manipulador de exceção com base em filtro.|  
  
## <a name="remarks"></a>Comentários  
 Uma matriz de valores de `CoreDebugEHClause` é retornada pelo método [GetEHClauses](icordebugilcode-getehclauses-method.md) .  
  
 As informações da cláusula EH são definidas pela especificação CLI. Para obter mais informações, consulte [Standard ECMA-355: Common Language Infrastructure (CLI), 6º edição](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 O campo `flags` pode conter os seguintes sinalizadores. Observe se eles não estão definidos em CorDebug.idl ou em CorDebug.h.  
  
|Sinalizador|Value|Descrição|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Uma cláusula de exceção digitada.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Uma cláusula do manipulador e do filtro de exceção.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|Uma cláusula `finally`.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Uma cláusula de falha (uma cláusula `finally` que é chamada somente quando uma exceção é lançada).|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetEHClauses](icordebugilcode-getehclauses-method.md)
- [Estruturas de depuração](debugging-structures.md)
