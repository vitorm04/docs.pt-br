---
title: "Como inicializar objetos usando um inicializador de objeto (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "inicializadores de objeto [C#], como usar"
  - "objetos [C#], inicializando"
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como inicializar objetos usando um inicializador de objeto (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar inicializadores de objeto para inicializar objetos do tipo de uma maneira declarativa sem explicitamente chamar um construtor para o tipo.  
  
 Os exemplos a seguir mostram como usar inicializadores de objeto com objetos denominados.  Os processos de compilador objeto inicializadores primeiro acessando o construtor de instância padrão e depois processar as inicializações de membro.  Portanto, se o construtor padrão é declarado como `private` na classe, inicializadores de objeto que exigem acesso público irão falhar.  
  
 Você deve usar um inicializador de objeto se você estiver definindo um tipo anônimo.  Para obter mais informações, consulte [Como retornar subconjuntos de propriedades de elementos em uma consulta](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## Exemplo  
 O exemplo a seguir mostra como inicializar um novo tipo de `StudentName` usando inicializadores de objeto.  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como inicializar uma coleção de tipos de `StudentName` usando um inicializador de coleção.  Observe que um inicializador de coleção é uma série de inicializadores separados por vírgulas do objeto.  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## Compilando o código  
 Para executar estes código, copiar e colar a classe em um projeto de aplicativo de console visual C\# que foi criado em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)