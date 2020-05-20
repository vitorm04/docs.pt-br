---
title: Interface ISymUnmanagedVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610165"
---
# <a name="isymunmanagedvariable-interface"></a>Interface ISymUnmanagedVariable
Representa uma variável, como um parâmetro, uma variável local ou um campo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAddressField1](isymunmanagedvariable-getaddressfield1-method.md)|Obtém o primeiro campo de endereço para essa variável. Seu significado depende do tipo de endereço.|  
|[Método GetAddressField2](isymunmanagedvariable-getaddressfield2-method.md)|Obtém o segundo campo de endereço para essa variável. Seu significado depende do tipo de endereço.|  
|[Método GetAddressField3](isymunmanagedvariable-getaddressfield3-method.md)|Obtém o terceiro campo de endereço para essa variável. Seu significado depende do tipo de endereço.|  
|[Método GetAddressKind](isymunmanagedvariable-getaddresskind-method.md)|Obtém o tipo de endereço dessa variável.|  
|[Método GetAttributes](isymunmanagedvariable-getattributes-method.md)|Obtém os sinalizadores de atributo para essa variável.|  
|[Método GetEndOffset](isymunmanagedvariable-getendoffset-method.md)|Obtém o deslocamento final dessa variável dentro de seu pai.|  
|[Método GetName](isymunmanagedvariable-getname-method.md)|Obtém o nome dessa variável.|  
|[Método GetSignature](isymunmanagedvariable-getsignature-method.md)|Obtém a assinatura dessa variável.|  
|[Método GetStartOffset](isymunmanagedvariable-getstartoffset-method.md)|Obtém o deslocamento inicial dessa variável dentro de seu pai.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interfaces de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-interfaces.md)
