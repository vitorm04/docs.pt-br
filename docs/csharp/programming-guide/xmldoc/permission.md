---
title: "&lt;permission&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;permission&gt; (XML) C#"
  - "marca XML C# permission"
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;permission&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### Parâmetros  
 cref \= " `member`"  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.  O compilador verifica se o elemento de código fornecido existe e se traduz `member` para o nome do elemento canônico na saída XML. *membro* deve aparecer entre aspas duplas \(""\).  
  
 Para obter informações sobre como criar uma referência de cref para um tipo genérico, consulte [\<see\>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Uma descrição do acesso ao membro.  
  
## Comentários  
 O \<permission\> marca permite o acesso de um membro do documento.  O <xref:System.Security.PermissionSet> classe permite que você especificar o acesso a um membro.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)