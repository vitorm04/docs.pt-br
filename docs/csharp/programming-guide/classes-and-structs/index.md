---
title: "Classes e structs (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, classes"
  - "Linguagem C#, objetos"
  - "Linguagem C#, estruturas"
  - "classes [C#], visão geral"
  - "objetos [C#]"
  - "estruturas [C#], sobre estruturas"
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
caps.handback.revision: 48
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classes e structs (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

As classes e estruturas são dois dois constructos básicos do sistema de tipo comum no .NET Framework.  Cada uma é essencialmente uma estrutura de dados que encapsula um conjunto de dados e comportamentos que devem ficar juntos como uma unidade lógica.  Os dados e os comportamentos são os *membros* da classe ou estrutura e incluem seus métodos, propriedades e eventos e assim por diante, como listado posteriormente neste tópico.  
  
 Uma declaração de classe ou de estrutura é como um plano gráfico que é usado para criar instâncias ou objetos em tempo de execução.  Se você definir uma classe ou estrutura chamada `Person`, `Person` é o nome do tipo.  Se você declarar e inicializar uma variável `p` de tipo `Person`, `p`, diz\-se que é um objeto ou uma instância de `Person`.  Várias instâncias do mesmo tipo de `Person` podem ser criadas, e cada instância pode ter valores diferentes em suas propriedades e campos.  
  
 Uma classe é um tipo de referência.  Quando um objeto da classe é criado, a variável à qual o objeto é atribuído contém apenas uma referência a essa memória.  Quando a referência de objeto é atribuída a uma nova variável, a nova variável refere\-se ao objeto original.  Alterações feitas por uma variável são refletidas em outra variável porque ambas referem\-se aos mesmos dados.  
  
 Um struct é um tipo de valor.  Quando um estrutura é criada, a variável à qual a estrutura é atribuída contém os dados reais de estrutura.  Quando a estrutura é atribuída a uma nova variável, ela é copiada.  A nova variável e a variável original, portanto, contêm duas cópias separadas dos mesmos dados.  As alterações feitas em uma cópia não afetam a outra cópia.  
  
 Em geral, as classes são usadas para modelar comportamento mais complexo ou dados destinados a serem alterados depois da criação de um objeto de classe.  As estruturas são mais adequadas a pequenas estruturas de dados que contém principalmente dados que não estejam destinados a serem modificados após a criação da estrutura.  
  
 Para obter mais informações, consulte [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md), [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md) e [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## Exemplo  
 No exemplo a seguir, `MyCustomClass` é definido com três membros do nível superior do namespace `ProgrammingGuide`.  Uma instância \(objeto\) de `MyCustomClass` é criada no método `Main` na classe `Program` e os métodos e propriedades do objeto são acessados usando notação de ponto.  
  
 [!code-cs[csProgGuideObjects#88](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
## Encapsulamento  
 O *Encapsulamento*, às vezes, é chamado de primeira coluna ou princípio de programação orientada a objeto.  De acordo com o princípio de encapsulamento, uma classe ou estrutura pode especificar qual a capacidade de acesso de cada um dos seus membros para codificar fora da classe ou estrutura.  Os métodos e variáveis que não são destinados ao uso fora da classe ou do assembly podem estar ocultos para limitar o potencial para erros de codificação ou explorações maliciosas.  
  
 Para obter mais informações sobre classes, consulte [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) e [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### Membros  
 Todos os métodos, campos, constantes, propriedades e eventos devem ser declarados dentro de um tipo; eles são chamados *membros* do tipo.  Em C\#, não há variáveis globais ou métodos, porque existem alguns outros idiomas.  Mesmo o ponto de entrada de um programa, o método `Main`, deve ser declarado em uma classe ou estrutura.  A lista a seguir inclui todos os diversos tipos de membros que podem ser declarados em uma classe ou estrutura.  
  
-   [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Métodos](../../../fsharp/language-reference/members/methods.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### Acessibilidade  
 Alguns métodos e propriedades foram criados para serem chamados ou acessados de código de fora de sua classe ou estrutura, conhecido como *código cliente*.  Outros métodos e propriedades podem ser apenas para uso na classe ou estrutura em si.  É importante limitar a acessibilidade do seu código para que somente o código do cliente intencionado possa chegar a ele.  Você especifica o quanto seus tipos e os membros deles são acessíveis para o cliente usando os modificadores de acesso [público](../../../csharp/language-reference/keywords/public.md), [protegido](../../../csharp/language-reference/keywords/protected.md), [interno](../../../csharp/language-reference/keywords/internal.md), `protected internal` e [particular](../../../csharp/language-reference/keywords/private.md).  A acessibilidade padrão é `private`.  Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### Herança  
 As classes \(mas não estruturas\) aceitam o conceito de herança.  Uma classe que deriva de outra classe \(a *classe base*\) automaticamente contém todos os membros públicos, protegidos e internos da classe base, exceto seus construtores e destruidores.  Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md) e [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 As classes podem ser declaradas como [abstract](../../../csharp/language-reference/keywords/abstract.md), o que significa que um ou mais dos seus métodos não possuem implementação.  Embora as classes abstratas não possam ser instanciadas diretamente, pode servir como classes base para outras classes que fornecem uma implementação ausente.  As classes também podem ser declaradas como [sealed](../../../csharp/language-reference/keywords/sealed.md) para impedir que outras classes herdem delas.  Para obter mais informações, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### Interfaces  
 As classes e estruturas podem herdar várias interfaces.  Herdar de uma interface significa que o tipo implementa todos os métodos definidos na interface.  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
### Tipos genéricos  
 As classes e estruturas podem ser definidas com um ou mais parâmetros de tipo.  O código do cliente fornece o tipo quando ele cria uma instância do tipo.  Por exemplo, a classe <xref:System.Collections.Generic.List%601> no namespace <xref:System.Collections.Generic> é definida com um parâmetro de tipo.  O código do cliente cria uma instância de `List<string>` ou de `List<int>` para especificar o tipo que a lista conterá.  Para obter mais informações, consulte [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md).  
  
### Tipos estáticos  
 As classes \(mas não estruturas\) podem ser declaradas como [static](../../../csharp/language-reference/keywords/static.md).  Uma classe estática pode conter somente membros estáticos e não pode ser instanciada com a palavra\-chave new.  Uma cópia da classe é carregada em memória quando o programa é carregado e seus membros são acessados por meio do nome da classe.  As classes e estruturas podem conter os membros estáticos.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### Tipos aninhados  
 Uma classe ou estrutura pode ser aninhada dentro de outra classe ou estrutura.  Para obter mais informações, consulte [Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### Tipos parciais  
 É possível definir parte de uma classe, estrutura ou método em um arquivo de código e a outra parte em um arquivo separado de código.  Para obter mais informações, consulte [Métodos e classes parciais](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### Inicializadores de Objeto  
 É possível criar uma instância e inicializar objetos de classe ou de estrutura, e coleções de objetos, sem chamar explicitamente o construtor.  Para obter mais informações, consulte [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### Tipos anônimos  
 Em situações onde não é conveniente ou necessário criar uma determinada classe, por exemplo, quando você estiver preenchendo uma lista com estruturas de dados que você não precisa manter ou transmitir a outro método, você usa tipos anônimos.  Para obter mais informações, consulte [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### Métodos de extensão  
 É possível "estender" uma classe sem criar uma classe derivada, criando um tipo separado cujos métodos podem ser chamados como se pertencessem ao tipo original.  Para obter mais informações, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### Variáveis Locais Tipadas Implicitamente  
 Em uma classe ou um método de estrutura, você pode usar a tipagem implícita para instruir o compilador a determinar o tipo correto no tempo de compilação.  Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)