---
title: "&lt;see&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<see>"
  - "see"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;see&gt; (XML) C#"
  - "cref [C#], Marca &lt;see&gt;"
  - "referências cruzadas [C#]"
  - "ver marca XML C#"
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;see&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<see cref="member"/>  
```  
  
#### Parâmetros  
 cref” \= “ `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código existe e`member` passa para o nome de elemento no XML.*Membro* de localidade dentro de aspas duplas \(” "\).  
  
## Comentários  
 \<A marca consulte\> permite que você especifique um link de dentro do texto.  Use [\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md) para indicar que o texto deve ser colocado considerar também seciona.  Use [o atributo cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) para criar hiperlinks internos páginas de documentação para elementos de código.  
  
 Compile com [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.  
  
 O exemplo a seguir mostra \<uma marca considerar\> em uma seção de resumo.  
  
 [!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)