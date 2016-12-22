---
title: "O tipo &lt;typename&gt; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40041"
  - "vbc40041"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40041"
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &lt;typename&gt; n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.  
  
 Para um aplicativo ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele deve usar somente tipos compatíveis com CLS.  
  
 Os seguintes tipos de dados [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não são compatíveis com CLS:  
  
-   [Tipo de dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Identificação do erro:**  BC40041  
  
### Para corrigir este erro  
  
-   Se seu aplicativo precisar ser compatível com CLS, altere o tipo de dados desse elemento para o tipo mais próximo compatível com CLS.  Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar o intervalo de valores acima 2.147.483.647.  Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se não precisar seu aplicativo ser compatível com CLS, você não precisará alterar nada.  Entretanto, você deve conhecer sua incompatibilidade.  
  
## Consulte também  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)