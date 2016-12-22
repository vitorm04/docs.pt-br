---
title: "Restringindo a acessibilidade aos acessadores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "acessadores [C#]"
  - "acessibilidade do acessador assimétrico [C#]"
  - "indexadores [C#], somente leitura"
  - "propriedades [C#], somente leitura"
  - "indexadores somente leitura [C#]"
  - "propriedades somente leitura [C#]"
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Restringindo a acessibilidade aos acessadores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O  [obter](../../../csharp/language-reference/keywords/get.md) e  [set](../../../csharp/language-reference/keywords/set.md) são chamados de partes de uma propriedade ou indexador  *acessadores*.  Por padrão esses acessadores possuem a mesma visibilidade, ou nível de acesso que da propriedade ou indexador às quais eles pertencem.  Para obter mais informações, consulte  [níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).  No entanto, às vezes é útil restringir o acesso a um desses acessadores.  Normalmente, isso envolve a restringir a acessibilidade da `set` acessador, e manter o `get` acessador acessível publicamente.  Por exemplo:  
  
 [!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 Neste exemplo, uma propriedade chamada `Name` define um `get` e `set` acessador.  O `get` acessador recebe o nível de acessibilidade da propriedade propriamente dito, `public` nesse caso, enquanto o `set` acessador explicitamente é restrito, aplicando o  [protegido](../../../csharp/language-reference/keywords/protected.md) modificador de acesso para o acessador propriamente dito.  
  
## Restrições sobre os modificadores de acesso nos assessores  
 Usando os modificadores de assessor em propriedades ou indexadores está sujeita às seguintes condições:  
  
-   Não é possível usar modificadores de assessor em uma interface ou um explícito  [interface](../../../csharp/language-reference/keywords/interface.md) implementação de um membro.  
  
-   Você pode usar modificadores de assessor somente se a propriedade ou indexador tem dois `set` e `get` acessadores.  Nesse caso, o modificador é permitido em um só os dois acessadores.  
  
-   Se a propriedade ou indexador tiver um  [Substituir](../../../csharp/language-reference/keywords/override.md) modificador, o modificador de acesso deve coincidir com o acessador do acessador substituído, se houver.  
  
-   O nível de acessibilidade no acessador deve ser mais restritivo que o nível de acessibilidade na propriedade ou indexador propriamente dito.  
  
## Modificadores de acesso em substituindo acessadores  
 Quando você substituir uma propriedade ou indexador, os acessadores substituídos devem ser acessíveis para o código de substituição.  Além disso, o nível de acessibilidade de tanto o propriedade\/indexador e dos acessadores devem corresponder o propriedade\/indexador em correspondente substituído e os acessadores.  Por exemplo:  
  
 [!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## Implementar Interfaces  
 Quando você usa um acessador para implementar uma interface, o acessador não pode ter um modificador de acesso.  No entanto, se você implementa a interface usando um acessador, como `get`, o acessador outro pode ter um modificador de acesso, como no exemplo a seguir:  
  
 [!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## Domínio de acessibilidade do acessador  
 Se você usar um modificador de acesso no acessador, o  [o domínio de acessibilidade](../../../csharp/language-reference/keywords/accessibility-domain.md) do acessador é determinada por esse modificador.  
  
 Se você não tiver usado um modificador de acesso em o acessador, domínio de acessibilidade do acessador é determinado pelo nível de acessibilidade da propriedade ou indexador.  
  
## Exemplo  
 O exemplo a seguir contém três classes, `BaseClass`, `DerivedClass`, e `MainClass`.  Há duas propriedades sobre o `BaseClass`, `Name` e `Id` em ambas as classes.  O exemplo demonstra como a propriedade `Id` na `DerivedClass` podem ser ocultados pela propriedade `Id` na `BaseClass` quando você usa um modificador de acesso restrito, como  [protegido](../../../csharp/language-reference/keywords/protected.md) ou  [particular](../../../csharp/language-reference/keywords/private.md).  Portanto, quando você atribuir valores para essa propriedade, a propriedade sobre a `BaseClass` classe é chamada em vez disso.  Substituindo o modificador de acesso por  [pública](../../../csharp/language-reference/keywords/public.md) fará com que a propriedade acessíveis.  
  
 O exemplo também demonstra que um modificador de acesso restritivas, como `private` ou `protected`diante a `set` assessor da `Name` propriedade na `DerivedClass` impede o acesso para o acessador e gera um erro quando você atribui a ele.  
  
 [!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## Comentários  
 Observe que, se você substituir a declaração `new private string Id` por `new public string Id`, você obtém a saída:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)