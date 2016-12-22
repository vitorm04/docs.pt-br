---
title: "Objetos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "objetos [C#], sobre objetos"
  - "variáveis [C#]"
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Objetos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma definição de classe ou de estrutura é como um modelo que especifica o que o tipo pode fazer.  Um objeto é basicamente um bloco de memória que foi atribuído e configurado de acordo com o modelo.  Um programa pode criar vários objetos da mesma classe.  Os objetos são chamados também instâncias, e podem ser armazenados em uma variável chamada ou matriz ou na coleção.  O código do cliente é o código que usa essas variáveis para chamar os métodos e para acessar as propriedades públicas do objeto.  Em uma linguagem orientada a objeto como C\#, um programa típico consiste em vários objetos que interagem dinamicamente.  
  
> [!NOTE]
>  Os tipos estáticos se comportam de maneira diferente do que é descrito aqui.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## Instâncias de Estrutura CONTRA. instâncias de classe  
 Porque as classes são tipos de referência, uma variável de um objeto da classe contém uma referência para o endereço do objeto na heap gerenciada.  Se um segundo objeto do mesmo tipo é atribuído ao primeiro objeto, então ambas as variáveis referem\-se ao objeto no endereço.  Este ponto é abordado em detalhes posteriormente em este tópico.  
  
 As instâncias de classes são criadas usando [operador new](../../../visual-basic/language-reference/operators/new-operator.md).  Em o exemplo, `Person` é o tipo e `person1` e `person 2` são instâncias, ou objetos, do tipo.  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Como as estruturas são tipos de valor, uma variável de um objeto de estrutura armazena uma cópia do objeto inteiro.  Instâncias de estruturas também podem ser criadas usando o operador de `new` , mas isso não é necessária, como mostrado no exemplo o seguir:  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 A memória para ambos `p1` e `p2` é atribuída na pilha de segmento.  Essa memória é recuperada juntamente com o tipo ou o método no qual é declarada.  Esta é uma motivo pelo qual as estruturas são copiados na atribuição.  Por outro lado, a memória que é atribuída para uma instância da classe é recuperada automaticamente coletado como lixo \(\) no common language runtime em que todas as referências para o objeto saíram de escopo.  Não é possível destruir deterministically um objeto da classe como você pode em C\+\+.  Para obter mais informações sobre a coleta de lixo em [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], consulte [Garbage Collection](../Topic/Garbage%20Collection.md).  
  
> [!NOTE]
>  A alocação e a desalocação de memória no heap gerenciado são otimizadas para o common language runtime.  Em a maioria dos casos não há uma diferença significativa em custo de atribuir uma instância de classe na heap contra alocar de uma instância de estrutura na pilha.  
  
## Identidade do objeto CONTRA. igualdade de valor  
 Quando você compara dois objetos para igualdade, primeiro você deve distinguir se você deseja saber se as duas variáveis representam o mesmo objeto na memória, ou se os valores de um ou mais de seus campos são equivalentes.  Se você intençãp comparar valores, você deve considerar se os objetos são instâncias dos tipos de valor \(\) ou estruturas de tipos de referência \(classes, representantes, matrizes\).  
  
-   Para determinar se duas instâncias de classe referem\-se ao mesmo local na memória \(que significa que possui a mesma *identidade*\), use o método estático de <xref:System.Object.Equals%2A> .  \(<xref:System.Object?displayProperty=fullName> é a classe base implícito para todos os tipos de valor e tipos de referência, incluindo estruturas definidos pelo usuário e classes.\)  
  
-   Para determinar se a instância coloca em duas instâncias de estrutura tem os mesmos valores, use o método de <xref:System.ValueType.Equals%2A?displayProperty=fullName> .  Como todos os estruturas implicitamente herdam de <xref:System.ValueType?displayProperty=fullName>, você chama o método diretamente no seu objeto conforme mostrado no exemplo o seguir:  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 A implementação de <xref:System.ValueType?displayProperty=fullName> de `Equals` usa reflexão porque ele deve ser capaz determinar quais campos são em qualquer estrutura.  A o criar seus próprios estruturas, substituir o método de `Equals` para fornecer um algoritmo eficiente de igualdade que é específico ao seu tipo.  
  
-   Para determinar se os valores dos campos em duas instâncias de classe são iguais, você poderá usar o método de <xref:System.Object.Equals%2A> ou o [operador de \=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md).  Em o entanto, use\-as somente se a classe os substituiu ou tenha sobrecarregado para fornecer uma definição personalizado do que significa” a “igualdade para objetos do tipo.  A classe também pode implementar a interface de <xref:System.IEquatable%601> ou a interface de <xref:System.Collections.Generic.IEqualityComparer%601> .  Ambas as interfaces fornecem métodos que podem ser usados para testar a igualdade de valor.  A o criar suas próprias classes que substituem `Equals`, certifique\-se seguir as diretrizes declaradas em [Como definir a igualdade de valor para um tipo](../Topic/How%20to:%20Define%20Value%20Equality%20for%20a%20Type%20\(C%23%20Programming%20Guide\).md) e em <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  
  
## Seções relacionadas  
 para mais informações:  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Operador new](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Common Type System](../../../standard/base-types/common-type-system.md)