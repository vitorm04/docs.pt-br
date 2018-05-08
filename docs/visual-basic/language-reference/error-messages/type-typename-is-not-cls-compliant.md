---
title: Tipo &lt;typename&gt; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 9911b4fe7b88996f17cb5e9eec7d4a5f2c254b76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Tipo &lt;typename&gt; não é compatível com CLS
Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.  
  
 Para um aplicativo ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
-   [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID do erro:** BC40041  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se seu aplicativo precisa para ser compatível com CLS, altere o tipo de dados desse elemento para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se seu aplicativo não precisa ser compatível com CLS, você não precisa alterar nada. Você deve conhecer sua incompatibilidade, no entanto.