---
title: "Classes gen&#233;ricas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, classes genéricas"
  - "genéricos [C#], classes"
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classes gen&#233;ricas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Classes genéricas encapsulam as operações que não são específicas para um tipo de dados específico.  O uso mais comum para classes genéricas é com coleções como listas vinculadas, tabelas de hash, pilhas, filas, árvores e assim por diante.  Operações como, por exemplo, adicionando e removendo itens da coleção são executadas basicamente da mesma maneira independentemente do tipo de dados armazenados.  
  
 Para a maioria dos cenários que exigem as coleções de classes, a abordagem recomendada é usar os fornecidos na.Biblioteca de classes.  Para obter mais informações sobre como usar essas classes, consulte [Genéricos na biblioteca de classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Normalmente, você deve criar classes genéricas começando com uma classe concreta existente e, em seguida, alterando os tipos em parâmetros de tipo um por vez até atingir o equilíbrio ideal de generalização e usabilidade.  Ao criar suas próprias classes genéricas, considerações importantes incluem o seguinte:  
  
-   Quais tipos de generalizar em parâmetros de tipo.  
  
     Como uma regra, quanto mais você pode parametrizar tipos, o mais flexíveis e reutilizáveis se torna seu código.  No entanto, há muita generalização pode criar código que é difícil para outros desenvolvedores ler ou compreender.  
  
-   Que restrições, se houver, para aplicar os parâmetros de tipo \(consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)\).  
  
     Uma boa regra é aplicar restrições máxima possíveis que permitirá ainda que lidam com os tipos que você deve tratar.  Por exemplo, se você souber que sua classe genérica é destinado ao uso somente com os tipos de referência, aplica a restrição de classe.  Que impedirá o uso não intencional de sua classe com os tipos de valor e permitirá que você use o `as` operador em `T`e verifique se há valores nulos.  
  
-   Se fator comportamento genérico em subclasses e classes base.  
  
     Porque classes genéricas podem servir como classes base, as mesmas considerações de design se aplicam aqui como ocorre com as classes não\-genéricas.  Consulte as regras sobre a herança de classes genéricas de base neste tópico.  
  
-   Decida se deseja implementar uma ou mais interfaces genéricas.  
  
     Por exemplo, se você estiver criando uma classe que será usada para criar itens em uma coleção baseado em genéricos, você pode ter que implementar uma interface, como <xref:System.IComparable%601> onde `T` é o tipo de sua classe.  
  
 Para obter um exemplo de uma classe genérica simples, consulte [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 As regras para parâmetros de tipo e restrições tem várias implicações para o comportamento da classe genérica, especialmente com relação de herança e membro de acessibilidade.  Antes de prosseguir, você deve entender alguns termos.  Para uma classe genérica `Node<T>,` código do cliente pode referenciar a classe ou especificando um argumento de tipo, para criar um tipo construído fechado \(`Node<int>`\).  Como alternativa, ele pode deixar o parâmetro de tipo não for especificado, por exemplo, quando você especifica uma classe genérica de base criar uma abertura construído tipo \(`Node<T>`\).  Classes genéricas podem herdar de concretos, fechadas construídos ou abrir construídos classes base:  
  
 [!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 Não genérico, em outras palavras, as classes concretas, pode herdar de classes base construídos fechadas, mas não a partir de classes construídos abertos ou parâmetros de tipo porque não há nenhuma maneira em tempo de execução de código do cliente fornecer o argumento do tipo necessário para instanciar a classe base.  
  
 [!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 Classes genéricas que herdam de tipos construídos abertos devem fornecer argumentos de tipo para qualquer parâmetro de tipo de classe base que não é compartilhado pela classe herdando, conforme demonstrado no código a seguir:  
  
 [!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 Classes genéricas que herdam de tipos construídos abertos devem especificar restrições que são um superconjunto de ou implica, as restrições no tipo base:  
  
 [!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 Tipos genéricos podem usar vários parâmetros de tipo e restrições, da seguinte maneira:  
  
 [!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 Abrir tipo construído construído e fechado pode ser usado como parâmetros do método:  
  
 [!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 Se uma classe genérica implementa uma interface, todas as instâncias dessa classe podem ser convertidas em interface.  
  
 Classes genéricas são invariável.  Em outras palavras, se um parâmetro de entrada especifica um `List<BaseClass>`, você obterá um erro de tempo de compilação se você tentar fornecer um `List<DerivedClass>`.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Salvar o estado de enumeradores](http://go.microsoft.com/fwlink/?LinkId=112390)   
 [Um quebra\-cabeça da herança, parte 1](http://go.microsoft.com/fwlink/?LinkId=112380)