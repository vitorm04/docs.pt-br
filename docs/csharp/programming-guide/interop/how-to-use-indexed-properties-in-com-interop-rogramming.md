---
title: "Como usar propriedades indexadas na programa&#231;&#227;o para interoperabilidade COM (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "propriedades indexadas [C#]"
  - "Programação do Office [C#], propriedades indexadas"
  - "propriedades [C#], indexado"
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar propriedades indexadas na programa&#231;&#227;o para interoperabilidade COM (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

*Indexado propriedades* melhorar o modo no qual COM propriedades que possuem parâmetros são consumidas na programação de C\#.  Indexado propriedades funcionam com outros recursos introduzidos no Visual C\# 2010, tais como  [argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), um novo tipo \([dinâmico](../../../csharp/language-reference/keywords/dynamic.md)\), e  [informações de tipo incorporados](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md), para melhorar a programação de Microsoft Office.  
  
 Em versões anteriores do C\#, métodos são acessíveis como se propriedades do `get` método não tem parâmetros e o `set` método tem apenas um parâmetro de valor.  No entanto, nem todas as propriedades COM atendem a essas restrições.  Por exemplo, o Excel [intervalo](http://go.microsoft.com/fwlink/?LinkId=166053) a propriedade tem um `get` acessador requer um parâmetro para o nome do intervalo.  No passado, porque você não pôde acessar o `Range` propriedade diretamente, era necessário usar o `get_Range` método em vez disso, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Propriedades indexadas permitem que você escrever, em vez disso, o seguinte:  
  
 [!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  O exemplo anterior também usa o  [argumentos opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) recurso, introduzido no Visual C\# 2010, que permite que você omita `Type.Missing`.  
  
 Da mesma forma, para definir o valor da `Value` propriedade de um [intervalo](http://go.microsoft.com/fwlink/?LinkId=179211) de objeto no Visual C\# 2008 e anteriores, dois argumentos são necessários.  Uma fornece um argumento para um parâmetro opcional que especifica o tipo de valor de intervalo.  O outro fornece o valor para o `Value` propriedade.  Antes do Visual C\# 2010, C\# permitido apenas um argumento.  Portanto, em vez de usar um método do conjunto regular, você precisava usar o `set_Value` método ou propriedade diferente, [valor2](http://go.microsoft.com/fwlink/?LinkId=166050).  Os exemplos a seguir ilustram essas técnicas.  Ambos definir o valor da célula A1 para `Name`.  
  
 [!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Propriedades indexadas permitem que você escreva o seguinte código em vez disso.  
  
 [!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Você não pode criar propriedades indexadas de sua preferência.  O recurso suporta apenas o consumo de propriedades indexadas existentes.  
  
## Exemplo  
 O código a seguir mostra um exemplo completo.  Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C\#](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md).  
  
 [!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## Consulte também  
 [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C\#](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md)   
 [Passo a passo: Programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)