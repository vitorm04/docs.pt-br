---
title: "Gen&#233;ricos em tempo de execu&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], em tempo de execução"
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Gen&#233;ricos em tempo de execu&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando um tipo genérico ou método é compilado em Microsoft intermediate language \(MSIL\), ele contém metadados que o identifica como tendo os parâmetros de tipo.  Como o MSIL para um tipo genérico é usado difere dependendo se o parâmetro de tipo fornecido é um valor de tipo ou tipo de referência.  
  
 Quando um tipo genérico é construído pela primeira vez com um tipo de valor como um parâmetro, o runtime cria um tipo genérico especializado com o parâmetro fornecido ou parâmetros substituídos nos locais apropriados na MSIL.  Tipos genéricos especializados são criados uma vez para cada tipo de valor exclusivo que é usado como um parâmetro.  
  
 Por exemplo, suponha que seu código de programa declarado uma pilha que é construída de inteiros:  
  
 [!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 Neste ponto, o tempo de execução gera uma versão especializada da <xref:System.Collections.Generic.Stack%601> classe que tem o inteiro substituirá seu parâmetro apropriadamente.  Agora, sempre que o seu código de programa utiliza uma pilha de inteiros, as reutilizações de tempo de execução geradas especializadas <xref:System.Collections.Generic.Stack%601> classe.  No exemplo a seguir, duas instâncias de uma pilha de inteiros são criadas e eles compartilham uma única instância de `Stack<int>` código:  
  
 [!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 No entanto, suponha que isto outro <xref:System.Collections.Generic.Stack%601> de classe com um tipo de valor diferente, como um `long` ou uma estrutura definida pelo usuário como seu parâmetro é criada em outro ponto no seu código.  Como resultado, o tempo de execução gera outra versão do tipo genérico e substitui um `long` nos locais apropriados na MSIL.  Conversões são mais necessárias porque cada classe genérica especializado nativamente contém o tipo de valor.  
  
 Os genéricos funcionam de modo um pouco diferente para tipos de referência.  Na primeira vez que um tipo genérico é construído com qualquer tipo de referência, o runtime cria um tipo genérico especializado com referências de objeto que substituirá os parâmetros da MSIL.  Em seguida, sempre que um tipo construído é instanciado com um tipo de referência como seu parâmetro, independentemente do tipo é, o tempo de execução reutiliza a criado anteriormente versão especializada do tipo genérico.  Isso é possível porque todas as referências são do mesmo tamanho.  
  
 Por exemplo, suponha que você tenha dois tipos de referência, um `Customer` classe e um `Order` de classe e suponha também que você criou uma pilha de `Customer` tipos:  
  
 [!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 Neste ponto, o tempo de execução gera uma versão especializada da <xref:System.Collections.Generic.Stack%601> classe que armazena as referências de objeto que serão preenchidas posteriormente em vez de armazenar dados.  Suponha que a próxima linha de código cria uma pilha de outro tipo de referência, que é chamada de `Order`:  
  
 [!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 Ao contrário com tipos de valor, outro especializado versão do <xref:System.Collections.Generic.Stack%601> classe não foi criado para o `Order` tipo.  Em vez disso, uma instância da versão especializada da <xref:System.Collections.Generic.Stack%601> classe é criada e o `orders` variável é definida para fazer referência a ela.  Suponha que você encontrou, em seguida, uma linha de código para criar uma pilha de um `Customer` tipo:  
  
 [!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Como ocorre com a utilização anterior a <xref:System.Collections.Generic.Stack%601> classe criada usando o `Order` outra instância do especializado, digite <xref:System.Collections.Generic.Stack%601> classe é criada.  Os ponteiros que estão contidos estão definidos para fazer referência a uma área da memória o tamanho de um `Customer` tipo.  Como o número de tipos de referência pode variar muito de um programa para o programa, o C\# implementação de genéricos reduz bastante a quantidade de código, reduzindo a um número de classes especializadas criado pelo compilador para classes genéricas de tipos de referência.  
  
 Além disso, quando uma classe genérica C\# é instanciada usando um parâmetro de tipo de valor tipo ou referência, reflexão pode consultar em tempo de execução e seu tipo real e o seu parâmetro de tipo podem ser determinadas.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)