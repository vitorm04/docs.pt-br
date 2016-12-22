---
title: "Como definir propriedades abstract (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "propriedades abstratas [C#]"
  - "propriedades [C#], abstrata"
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como definir propriedades abstract (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O exemplo a seguir mostra como definir  [abstrata](../../../csharp/language-reference/keywords/abstract.md) propriedades.  Uma declaração de propriedade abstract não fornece uma implementação de acessadores de propriedade\-\-ele declara que a classe oferece suporte a propriedades, mas deixa a implementação do acessador para classes derivadas.  O exemplo a seguir demonstra como implementar as propriedades abstract herdadas de uma classe base.  
  
 Este exemplo consiste em três arquivos, cada um deles é compilada individualmente e seu assembly resultante é referenciado pela próxima compilação:  
  
-   abstractshape.CS: o `Shape` classe que contém um resumo `Area` propriedade.  
  
-   Shapes.CS: subclasses de `Shape` classe.  
  
-   shapetest.CS: um programa de teste para exibir as áreas de alguns `Shape`\-derivado objetos.  
  
 Para compilar o exemplo, use o seguinte comando:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Isso criará a shapetest.exe do arquivo executável.  
  
## Exemplo  
 Este arquivo declara o `Shape` classe que contém o `Area` propriedade do tipo `double`.  
  
 [!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modificadores na propriedade são colocados na própria declaração de propriedade.  Por exemplo:  
  
    ```  
    public abstract double Area  
    ```  
  
-   Ao declarar uma propriedade abstrata \(como `Area` neste exemplo\), você simplesmente indicam que os assessores da propriedade estão disponíveis, mas não de implementá\-las.  Neste exemplo, apenas um  [obter](../../../csharp/language-reference/keywords/get.md) acessador estiver disponível, portanto, a propriedade é somente leitura.  
  
## Exemplo  
 O código a seguir mostra três subclasses de `Shape` e como substituir o `Area` propriedade para fornecer sua própria implementação.  
  
 [!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## Exemplo  
 O código a seguir mostra um programa de teste que cria um número de `Shape`\-derivado objetos e imprime suas áreas.  
  
 [!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Como criar e usar assemblies usando a linha de comando](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)