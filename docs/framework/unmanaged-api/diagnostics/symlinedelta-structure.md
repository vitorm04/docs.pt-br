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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438004"
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`mdMethod`|O token de metadados do método.|  
|`delta`|O número de linhas que o método foi movido.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
