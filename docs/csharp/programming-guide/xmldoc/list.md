---
title: "&lt;list&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "list"
  - "<list>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;item&gt; (XML) C#"
  - "Marca &lt;list&gt; (XML) C#"
  - "Marca &lt;listheader&gt; (XML) C#"
  - "marca XML C# item"
  - "marca XML C# list"
  - "marca XML C# listheader"
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;list&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### Parâmetros  
 `term`  
 Um termo para definir, que será definido em `description`.  
  
 `description`  
 Tanto um item em um marcador ou lista numerada ou a definição de um `term`.  
  
## Comentários  
 O \<listheader\> bloco é usado para definir a linha de cabeçalho de uma tabela ou uma definição de lista.  Ao definir uma tabela, você só precisa fornecer uma entrada para o termo no título.  
  
 Cada item da lista é especificado com \<item\> bloco.  Ao criar uma lista de definições, você precisará especificar ambos `term` e `description`.  No entanto, para uma tabela, uma lista com marcadores ou uma lista numerada, você só precisa fornecer uma entrada para `description`.  
  
 Uma lista ou tabela pode ter tantas \<item\>. blocos conforme necessário.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)