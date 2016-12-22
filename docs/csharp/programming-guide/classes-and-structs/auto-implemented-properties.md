---
title: "Propriedades autoimplementadas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "propriedades autoimplementadas [C#]"
  - "propriedades [C#], autoimplementadas"
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Propriedades autoimplementadas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No c\# 3.0 e posterior, as propriedades implementadas automaticamente fazem declaração de propriedade mais concisa quando nenhuma lógica adicional é necessária nos acessadores de propriedade.  Elas também permitem que o código do cliente criar objetos.  Quando você declara uma propriedade, conforme mostrado no exemplo a seguir, o compilador cria um campo de backup particular e anônimo que só pode ser acessado por meio da propriedade `get` e `set` acessadores.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe simples que tem algumas propriedades implementadas automaticamente:  
  
 [!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 No c\# 6 e versões posteriores, você pode inicializar as propriedades implementadas automaticamente da mesma forma que os campos:  
  
```c#  
public string FirstName { get; set; } = "Jane";  
```  
  
 A classe é mostrada no exemplo anterior é mutável.  Código do cliente pode alterar os valores em objetos depois que eles são criados.  Em classes complexas que contêm o comportamento significativo \(métodos\), bem como dados, geralmente é necessário ter propriedades públicas.  No entanto, para pequenas classes ou estruturas que basta encapsulam um conjunto de valores \(dados\) e têm pouca ou nenhuma comportamentos, aumente os objetos imutáveis, declarando o acessador set como [particular](../../../csharp/language-reference/keywords/private.md) \(imutáveis aos consumidores\) ou com a declaração de apenas um acessador get \(imutáveis em todos os lugares, exceto o construtor\).  Para obter mais informações, consulte [Como implementar uma classe leve com propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Atributos são permitidos nas propriedades implementadas automaticamente, mas, obviamente, não nos campos de backup uma vez que esses não são acessíveis a partir de seu código\-fonte.  Se você precisar usar um atributo no campo de uma propriedade existente, crie uma propriedade regular.  
  
## Consulte também  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)