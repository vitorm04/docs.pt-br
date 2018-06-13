---
title: Interface ISymUnmanagedReader2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dfc67ecf1eeb9ea5a19c98a8c378e73021da6c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426822"
---
# <a name="isymunmanagedreader2-interface"></a>Interface ISymUnmanagedReader2
Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo. Essa interface estende o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetMethodByVersionPreRemap](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Obter um método de leitor de símbolo, considerando um token de método e um número de versão de edit-and-continue.|  
|[Método GetMethodsInDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Obtém cada método que tem informações de linha do documento fornecido.|  
|[Método GetSymAttributePreRemap](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Obtém um atributo personalizado com base no seu nome.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
