---
title: Interface ISymUnmanagedWriter2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614676"
---
# <a name="isymunmanagedwriter2-interface"></a>Interface ISymUnmanagedWriter2
Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos léxicos e variáveis. Essa interface estende a interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DefineConstant2](isymunmanagedwriter2-defineconstant2-method.md)|Define um nome para um valor constante.|  
|[Método DefineGlobalVariable2](isymunmanagedwriter2-defineglobalvariable2-method.md)|Define uma única variável global.|  
|[Método DefineLocalVariable2](isymunmanagedwriter2-definelocalvariable2-method.md)|Define uma única variável no escopo léxico atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interfaces de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-interfaces.md)
- [Interface ISymUnmanagedWriter](isymunmanagedwriter-interface.md)
- [Interface ISymUnmanagedWriter3](isymunmanagedwriter3-interface.md)
