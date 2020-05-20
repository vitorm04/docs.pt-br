---
title: Interface ISymUnmanagedReaderSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: 3f6cea68a4379f8769ccbdbc6911cc5c425d3369
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614871"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a>Interface ISymUnmanagedReaderSymbolSearchInfo
Fornece métodos que recebem informações de pesquisa de símbolo. Obtenha essa interface chamando `QueryInterface` em um objeto que implementa a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetSymbolSearchInfo](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|Obtém informações de pesquisa de símbolo.|  
|[Método GetSymbolSearchInfoCount](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|Obtém uma contagem de informações de pesquisa de símbolo.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interfaces de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-interfaces.md)
