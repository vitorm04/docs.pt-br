---
title: "Enumeração CorSymAddrKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bb55d9c9f85ae8f8112f16dcf552295699826d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corsymaddrkind-enumeration"></a>Enumeração CorSymAddrKind
Indica o tipo de endereço de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`ADDR_NATIVE_REGISTER`|Indica um registro de CPU.|  
|`ADDR_NATIVE_REGREL`|Indica que o primeiro endereço é um registro e o segundo endereço é um deslocamento.|  
|`ADDR_NATIVE_OFFSET`|Indica um deslocamento de um endereço base.|  
|`ADDR_NATIVE_REGREG`|Indica que o primeiro endereço é a parte baixa de um registro, e o segundo endereço é a parte alta.|  
|`ADDR_NATIVE_REGSTK`|Indica que o primeiro endereço é a parte baixa de um registro, o segundo é a parte alta e a terceira é um deslocamento.|  
|`ADDR_NATIVE_STKREG`|Indica que o primeiro endereço é um registro, o segundo é um deslocamento e o terceiro é a parte alta do registro.|  
|`ADDR_BITFIELD`|Indica que o primeiro endereço é o início de um campo e o segundo endereço é o tamanho do campo.|  
|`ADDR_NATIVE_ISECTOFFSET`|Indica que o primeiro endereço é a seção e o segundo endereço é um deslocamento.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de armazenamento de símbolo de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
