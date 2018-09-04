---
title: Classes e structs (Guia de Programação em C#)
description: Descreve o uso de classes e estruturas (structs) em C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 8860b519ece14a13e2a3350d299aa67598eadcc2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513979"
---
# <a name="classes-and-structs-c-programming-guide"></a>Classes e structs (Guia de Programação em C#)
Classes e structs são duas das construções básicas do Common Type System no .NET Framework. Cada um é, essencialmente, uma estrutura de dados que encapsula um conjunto de dados e os comportamentos que são uma unidade lógica. Os dados e os comportamentos são os *membros* da classe ou struct, e eles incluem seus métodos, propriedades e eventos, e etc., conforme listado neste tópico.  
  
 Uma declaração de classe ou struct é como um plano que é usado para criar instâncias ou objetos em tempo de execução. Se você definir uma classe ou struct chamado `Person`, `Person` será o nome do tipo. Se você declarar e inicializar um `p` variável do tipo `Person`, `p` será considerado um objeto ou uma instância de `Person`. Várias instâncias do mesmo tipo `Person` podem ser criadas, e cada instância pode ter valores diferentes em suas propriedades e campos.  
  
 Uma classe é um tipo de referência. Quando um objeto da classe é criado, a variável à qual o objeto é atribuído armazena apenas uma referência na memória. Quando a referência de objeto é atribuída a uma nova variável, a nova variável refere-se ao objeto original. As alterações feitas por meio de uma variável são refletidas na outra variável porque ambas se referem aos mesmos dados.  
  
 Um struct é um tipo de valor. Quando um struct é criado, a variável à qual o struct está atribuído contém os dados reais do struct. Quando o struct é atribuído a uma nova variável, ele é copiado. A nova variável e a variável original, portanto, contêm duas cópias separadas dos mesmos dados. As alterações feitas em uma cópia não afetam a outra cópia.  
  
 Em geral, as classes são usadas para modelar o comportamento mais complexo ou dados que serão modificados depois que um objeto de classe for criado. Os structs são mais adequados para estruturas de dados pequenas que contêm principalmente dados que não serão modificados depois que o struct for criado.  
  
 Para obter mais informações, consulte [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md), [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md) e [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `CustomClass` no namespace `ProgrammingGuide` tem três membros: um construtor de instância, uma propriedade chamada `Number` e um método chamado `Multiply`. O método `Main` na classe `Program` cria uma instância (objeto) de `CustomClass`, e o método e a propriedade do objeto são acessados usando a notação de ponto.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Encapsulamento  
 *Encapsulamento* é chamado, ocasionalmente, de primeiro pilar ou princípio da programação orientada a objeto. De acordo com o princípio de encapsulamento, uma classe ou struct pode especificar qual membro será codificado fora da classe ou struct. Os métodos e as variáveis que não serão usados fora da classe ou assembly poderão ser ocultados para limitar erros de codificação potenciais ou explorações maliciosas.  
  
 Para obter mais informações sobre classes, consulte [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) e [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Membros  
 Todos os métodos, campos, constantes, propriedades e eventos devem ser declarados em um tipo. Eles são chamados de *membros* do tipo. No C#, não existem variáveis globais ou métodos como em algumas das outras linguagens. Até mesmo um ponto de entrada de um programa, o método `Main`, deve ser declarado em uma classe ou struct. A lista a seguir inclui todos os vários tipos de membros que podem ser declarados em uma classe ou struct.  
  
-   [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
-   [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Acessibilidade  
 Alguns métodos e propriedades devem ser chamados ou acessado pelo código fora de sua classe ou struct, também conhecido como *código de cliente*. Outros métodos e propriedades podem ser usados apenas na classe ou struct em si. É importante limitar o acessibilidade do código para que somente o código do cliente desejado possa fazer contato. É possível especificar quão acessível seus tipos e seus membros são para o código do cliente usando os modificadores de acesso [público](../../../csharp/language-reference/keywords/public.md), [protegido](../../../csharp/language-reference/keywords/protected.md), [interno](../../../csharp/language-reference/keywords/internal.md), [interno protegido](../../../csharp/language-reference/keywords/protected-internal.md), [privado](../../../csharp/language-reference/keywords/private.md) e [privado protegido](../../../csharp/language-reference/keywords/private-protected.md). A acessibilidade padrão é `private`. Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Herança  
 Classes (mas não structs) dão suporte ao conceito de herança. Uma classe que deriva de outra classe (a *classe base*) contém automaticamente todos os membros públicos, protegidos e internos da classe base, exceto seus construtores e finalizadores. Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md) e [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 As classes podem ser declaradas como [abstratas](../../../csharp/language-reference/keywords/abstract.md), o que significa que um ou mais dos seus métodos não têm nenhuma implementação. Embora as classes abstratas não possam ser instanciadas diretamente, elas servem como classes base para outras classes que fornecem a implementação ausente. As classes também podem ser declaradas como [lacradas](../../../csharp/language-reference/keywords/sealed.md) para impedir que outras classes herdem delas. Para obter mais informações, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfaces  
 Classes e estruturas podem herdar várias interfaces. Herdar de uma interface significa que o tipo implementa todos os métodos definidos na interface. Para obter mais informações, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Tipos genéricos  
 Classes e estruturas podem ser definidas com um ou mais parâmetros de tipo. O código do cliente fornece o tipo quando ele cria uma instância do tipo. Por exemplo a classe <xref:System.Collections.Generic.List%601> no namespace <xref:System.Collections.Generic> é definida com um parâmetro de tipo. O código do cliente cria uma instância de um `List<string>` ou `List<int>` para especificar o tipo que a lista conterá. Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Tipos estáticos  
 As classes (mas não structs) podem ser declaradas como [estáticas](../../../csharp/language-reference/keywords/static.md). Uma classe estática pode conter apenas membros estáticos e não pode ser instanciada com a palavra-chave *new*. Uma cópia da classe é carregada na memória quando o programa é carregado e seus membros são acessados pelo nome da classe. Classes e structs podem conter membros estáticos. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Tipos aninhados  
 Uma classe ou struct pode ser aninhado em outra classe ou struct. Para obter mais informações, consulte [Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Tipos parciais  
 Você pode definir parte de uma classe, struct ou método em um arquivo de código e outra parte em um arquivo de código separado. Para obter mais informações, consulte [Classes parciais e métodos](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicializadores de objeto  
 Você pode instanciar e inicializar objetos de classe ou struct e coleções de objetos sem chamar explicitamente seu construtor. Para obter mais informações, consulte [Inicializadores de coleção e objeto](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Tipos anônimos  
 Em situações nas quais não é conveniente ou necessário criar uma classe nomeada, por exemplo, quando você estiver preenchendo uma lista com estruturas de dados que você não precisa manter ou passar para outro método, use tipos anônimos. Para obter mais informações, consulte [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Métodos de extensão  
 Você pode "estender" uma classe sem criar uma classe derivada criando um tipo separado cujos métodos podem ser chamados como se pertencessem ao tipo original. Para obter mais informações, consulte [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Variáveis Locais Tipadas Implicitamente  
 Dentro de um método de classe ou struct, você pode usar digitação implícita para instruir o compilador para determinar o tipo correto no tempo de compilação. Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
