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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbafe39fffd28a9bfccaa275c9009bc03549cda6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429421"
---
# <a name="isymunmanagedwriter2-interface"></a>Interface ISymUnmanagedWriter2
Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis. Essa interface estende o [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DefineConstant2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|Define um nome para um valor constante.|  
|[Método DefineGlobalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|Define uma única variável global.|  
|[Método DefineLocalVariable2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|Define uma única variável no escopo léxico atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Interface ISymUnmanagedWriter3](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
