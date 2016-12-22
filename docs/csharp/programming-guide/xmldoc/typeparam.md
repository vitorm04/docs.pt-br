---
title: "&lt;typeparam&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "typeparam"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;typeparam&gt; (XML) C#"
  - "marca XML C# typeparam"
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;typeparam&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### Parâmetros  
 `name`  
 Nome do parâmetro de tipo.  Envolva o nome em aspas duplas \(" "\).  
  
 `description`  
 Uma descrição para o parâmetro de tipo.  
  
## Comentários  
 O `<typeparam>` marca deve ser usada no comentário para uma declaração de tipo ou método genérico para descrever um parâmetro de tipo.  Adicione uma marca para cada parâmetro do tipo do tipo genérico ou método.  
  
 Para obter mais informações, consulte [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 O texto para o `<typeparam>` marca será exibida no IntelliSense, o [Object Browser Window](http://msdn.microsoft.com/pt-br/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) código de relatório da web de comentário.  
  
 Compilar com  [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) a comentários de documentação do processo para um arquivo.  
  
## Exemplo  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)