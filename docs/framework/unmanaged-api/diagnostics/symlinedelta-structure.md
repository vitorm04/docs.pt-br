---
title: Estrutura SYMLINEDELTA
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159478"
---
# <a name="symlinedelta-structure"></a>Estrutura SYMLINEDELTA
Fornece informações para o manipulador de símbolo sobre os métodos que foram movidos em decorrência de edições.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`mdMethod`|Token de metadados do método.|  
|`delta`|O número de linhas que o método foi movido.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
