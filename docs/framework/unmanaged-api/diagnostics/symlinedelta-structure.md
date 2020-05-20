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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609294"
---
# <a name="symlinedelta-structure"></a>Estrutura SYMLINEDELTA
Fornece informações para o manipulador de símbolos sobre métodos que foram movidos como resultado de edições.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`mdMethod`|O token de metadados do método.|  
|`delta`|O número de linhas que o método foi movido.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl  
  
## <a name="see-also"></a>Confira também

- [Estruturas de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-structures.md)
