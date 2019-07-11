---
title: Enumeração CorSymAddrKind
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba24f5394ef8fb31d8bfa4e74ac59e7bd4af86d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769870"
---
# <a name="corsymaddrkind-enumeration"></a>Enumeração CorSymAddrKind
Indica o tipo de endereço de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Indica um Microsoft intermediate language (MSIL) local variável ou parâmetro de índice.|  
|`ADDR_NATIVE_RVA`|Indica um endereço virtual relativo em um módulo.|  
|`ADDR_NATIVE_REGISTER`|Indica um registro da CPU.|  
|`ADDR_NATIVE_REGREL`|Indica que o primeiro endereço é um registro e o segundo endereço é um deslocamento.|  
|`ADDR_NATIVE_OFFSET`|Indica um deslocamento de um endereço básico.|  
|`ADDR_NATIVE_REGREG`|Indica que o primeiro endereço é a parte baixa de um registro e o segundo endereço é a parte alta.|  
|`ADDR_NATIVE_REGSTK`|Indica que o primeiro endereço é a parte baixa de um registro, o segundo é a parte alta e o terceiro é um deslocamento.|  
|`ADDR_NATIVE_STKREG`|Indica que o primeiro endereço é um registro, o segundo é um deslocamento e o terceiro é a parte alta de registro.|  
|`ADDR_BITFIELD`|Indica que o primeiro endereço é o início de um campo e o segundo endereço é o tamanho do campo.|  
|`ADDR_NATIVE_ISECTOFFSET`|Indica que o primeiro endereço é a seção e o segundo endereço é um deslocamento.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Enumerações do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
