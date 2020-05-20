---
title: Interface ISymUnmanagedScope2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610854"
---
# <a name="isymunmanagedscope2-interface"></a>Interface ISymUnmanagedScope2
Representa um escopo léxico dentro de um método. Essa interface estende a interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) com métodos que obtêm informações sobre constantes definidas no escopo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetConstantCount](isymunmanagedscope2-getconstantcount-method.md)|Obtém uma contagem das constantes definidas neste escopo.|  
|[Método GetConstants](isymunmanagedscope2-getconstants-method.md)|Obtém as constantes locais definidas neste escopo.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interfaces de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-interfaces.md)
- [Interface ISymUnmanagedScope](isymunmanagedscope-interface.md)
