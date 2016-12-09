---
title: Sistema de tipo comum detalhado
description: Sistema de tipo comum detalhado
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 35098ce238af88229fddf2adc7cf762848781ebc

---

# <a name="common-type-system-in-depth"></a>Sistema de tipo comum detalhado

Este tópico contém as seções a seguir que exploram o Common Type System detalhadamente:

* [Tipos no .NET](#types-in-net)

* [Definições de tipo](#type-definitions)

* [Membros de tipos](#type-members)

* [Características de membros de tipo](#characteristics-of-type-members)


## <a name="types-in-net"></a>Tipos no .NET

Todos os tipos no .NET são tipos de valor ou tipos de referência. 

Tipos de valor são tipos de dados cujos objetos são representados pelo valor real do objeto. Se uma instância de um tipo de valor é atribuída a uma variável, essa variável recebe uma nova cópia do valor.

Tipos de referência são tipos de dados cujos objetos são representados por uma referência (semelhante a um ponteiro) para o valor real do objeto. Se um tipo de referência é atribuído a uma variável, essa variável referencia (aponta para) o valor original. Nenhuma cópia é feita. 

O Common Type System no .NET dá suporte às seguintes cinco categorias de tipos:

* [Classes](#classes)

* [Estruturas](#structures)

* [Enumerações](#enumerations)

* [Interfaces](#interfaces)

* [Delegados](#delegates)

### <a name="classes"></a>Classes

Uma classe é um tipo de referência que pode ser derivado diretamente de outra classe e que é derivada implicitamente de [System.Object](xref:System.Object). A classe define as operações que um objeto (que é uma instância da classe) pode executar (métodos, eventos ou propriedades) e os dados que o objeto contém (campos). Embora uma classe geralmente inclua a definição e a implementação (diferente de interfaces, por exemplo, que contêm somente a definição sem implementação), ela pode ter um ou mais membros que não têm implementação.

A tabela a seguir descreve algumas das características que uma classe pode ter. Cada linguagem que dá suporte ao tempo de execução fornece uma maneira para indicar que uma classe ou um membro da classe tem uma ou mais dessas características. No entanto, as linguagens de programação individuais que segmentam o .NET não podem disponibilizar todas essas características.

Característica | Descrição
-------------- | -----------
sealed | Especifica que outra classe não pode ser derivada desse tipo.
implementa | Indica que a classe usa uma ou mais interfaces, fornecendo implementações de membros da interface.
abstract | Indica que a classe não pode ser instanciada. Para usá-la, você deve derivar outra classe a partir dela.
herda | Indica que as instâncias da classe podem ser usadas em qualquer lugar em que a classe base for especificada. Uma classe derivada que herda de uma classe base pode usar a implementação de todos os membros públicos fornecidos pela classe base ou a classe derivada pode substituir a implementação dos membros públicos com sua própria implementação.
exportado ou não exportado | Indica se uma classe está visível fora do assembly em que ela está definida. Essa característica só se aplica a classes de nível superior e não a classes aninhadas.

> [!NOTE]
> Uma classe também pode ser aninhada em uma classe ou estrutura pai. Classes aninhadas também têm características de membro. Para obter mais informações, consulte [Tipos aninhados](#nested-types).

Membros da classe que não tenham implementação são membros abstratos. Uma classe que tenha um ou mais membros abstratos é ela própria abstrata. Não é possível criar novas instâncias dessa classe. Algumas linguagens que segmentam o tempo de execução permitem marcar uma classe como abstrata mesmo que nenhum de seus membros seja abstrato. É possível usar uma classe abstrata quando você deseja encapsular um conjunto básico de funcionalidades que as classes derivadas podem herdar ou substituir quando apropriado. Classes que não são abstratas são chamadas de classes concretas.

Uma classe pode implementar qualquer número de interfaces, mas pode herdar apenas uma classe base além de [System.Object](xref:System.Object), de que todas as classes herdam implicitamente. Todas as classes devem ter pelo menos um construtor, que inicializa novas instâncias da classe. Se você não definir explicitamente um construtor, a maioria dos compiladores fornecerá automaticamente um construtor padrão (sem parâmetros).

### <a name="structures"></a>Estruturas

Uma estrutura é um tipo de valor que é derivado implicitamente de [System.ValueType](xref:System.ValueType) que, por sua vez, é derivado de [System.Object](xref:System.Object). Uma estrutura é muito útil para representar valores cujos requisitos de memória são pequenos e passar valores como parâmetros por valor para os métodos que tenham parâmetros fortemente tipados. No .NET, todos os tipos de dados primitivos ([Booliano](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64)) são definidos como estruturas.

Assim como as classes, as estruturas definem os dados (os campos da estrutura) e as operações que podem ser executadas nesses dados (os métodos da estrutura). Isso significa que você pode chamar métodos em estruturas, incluindo os métodos virtuais definidos nas classes [System.Object](xref:System.Object) e [System.ValueType](xref:System.ValueType) e todos os métodos definidos no próprio tipo de valor. Em outras palavras, as estruturas podem ter campos, propriedades e eventos, bem como métodos estáticos e não estáticos. É possível criar instâncias de estruturas, passá-las como parâmetros, armazená-las como variáveis locais ou armazená-las em um campo de outro tipo de valor ou tipo de referência. As estruturas também podem implementar interfaces.

Tipos de valor também são diferentes das classes em vários pontos. Primeiro, embora herdem implicitamente de [System.ValueType](xref:System.ValueType), eles não podem herdar diretamente de qualquer tipo. Da mesma forma, todos os tipos de valor são lacrados, o que significa que nenhum outro tipo pode ser derivado deles. Eles também não exigem construtores.

Para cada tipo de valor, o Common Language Runtime fornece um tipo disponível demarcado correspondente, que é uma classe com o mesmo estado e comportamento que o tipo de valor. Uma instância de um tipo de valor é demarcada quando é passada para um método que aceita um parâmetro de tipo [System.Object](xref:System.Object). Ele é não demarcado (ou seja, convertido de uma instância de uma classe de volta para uma instância de um tipo de valor) quando o controle retorna de uma chamada de método que aceita um tipo de valor como um parâmetro por referência. Algumas linguagens exigem que você use sintaxe especial quando o tipo demarcado é necessário. Outras usam automaticamente o tipo demarcado quando necessário. Ao definir um tipo de valor, você está definindo o tipo demarcado e não demarcado.

### <a name="enumerations"></a>Enumerações

Uma enumeração (enum) é um tipo de valor que é herdado diretamente de [System.Enum](xref:System.Enum) e que fornece nomes alternativos para valores de um tipo primitivo subjacente. Um tipo de enumeração tem um nome, um tipo subjacente que deve ser um dos tipos inteiros com ou sem sinal internos (como [Byte](xref:System.Byte), [Int32](xref:System.Int32) ou [UInt64](xref:System.UInt64)) e um conjunto de campos. Os campos são campos literais estáticos, cada um deles representa uma constante. O mesmo valor pode ser atribuído a vários campos. Quando isso ocorre, você deve marcar um dos valores como o valor de enumeração primário para reflexão e conversão da cadeia de caracteres.

Você pode atribuir um valor de tipo subjacente a uma enumeração e vice-versa (nenhuma conversão é exigida pelo tempo de execução). É possível criar uma instância de uma enumeração e chamar os métodos de [System.Enum](xref:System.Enum), assim como qualquer método definido no tipo subjacente da enumeração. No entanto, algumas linguagens talvez não deixem passar uma enumeração como um parâmetro quando uma instância do tipo subjacente é necessária (ou vice-versa).

As seguintes restrições adicionais se aplicam a enumerações: 

* Elas não podem definir seus próprios métodos.

* Elas não podem implementar interfaces.

* Elas não podem definir propriedades ou eventos.

* Elas não podem ser genéricas, a menos que sejam genéricas apenas por estarem aninhadas dentro de um tipo genérico. Ou seja, uma enumeração não pode ter parâmetros de tipo próprios. 

> [!NOTE]
> Tipos aninhados (incluindo enumerações) criados com o C# incluem os parâmetros de tipo de todos os tipos genéricos e, portanto, serão genéricos mesmo se não tiverem parâmetros de tipo próprios. Para obter mais informações, consulte o tópico de referência [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])). 

O atributo [FlagsAttribute](xref:System.FlagsAttribute) denota um tipo especial de enumeração chamado campo de bits. O próprio tempo de execução não faz distinção entre enumerações tradicionais e campos de bits, mas a linguagem pode fazer isso. Quando é feita essa distinção, operadores bit a bit podem ser usados em campos de bits, mas não em enumerações, para gerar valores sem nome. Enumerações geralmente são usadas para listas de elementos exclusivos, como dias da semana, país ou nomes de região etc. Os campos de bits são geralmente usados para listas de qualidades ou quantidades que possam ocorrer em combinação, como `Red And Big And Fast`.

O exemplo a seguir mostra como usar campos de bit e enumerações tradicionais.

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a>Interfaces

Uma interface define um contrato que especifica um relacionamento "possível" ou um relacionamento de "propriedade". Interfaces são geralmente usadas para implementar a funcionalidade, como comparação e classificação (interfaces [IComparable](xref:System.IComparable) e [IComparable&lt;T&gt;](xref:System.IComparable%601)), testes de igualdade (a interface [IEquatable&lt;T&gt;](xref:System.IEquatable%601)), ou a enumeração de itens em uma coleção (as interfaces [IEnumerable](xref:System.Collections.IEnumerable) e [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601)). Interfaces podem ter propriedades, métodos, eventos e todos os que são membros abstratos; ou seja, embora a interface defina os membros e suas assinaturas, ela deixa para o tipo que implementa a interface para definir a funcionalidade de cada membro da interface. Isso significa que qualquer classe ou estrutura que implementa uma interface deve fornecer definições para os membros abstratos declarados na interface. Uma interface pode exigir qualquer classe de implementação ou estrutura para também implementar uma ou mais outras interfaces.

As restrições a seguir se aplicam a interfaces: 

* Uma interface pode ser declarada com qualquer acessibilidade, mas membros da interface devem ter acessibilidade pública.

* Interfaces não podem definir construtores.

* Interfaces não podem definir campos.

* Interfaces podem definir apenas membros de instância. Elas não podem definir membros estáticos.

Cada linguagem deve fornecer regras para mapear uma implementação para a interface que exija o membro, porque mais de uma interface pode declarar um membro com a mesma assinatura e esses membros podem ter implementações separadas.

### <a name="delegates"></a>Delegados

Os delegados são tipos de referência que têm um propósito semelhante aos de ponteiros de função no C++. Eles são usados para manipuladores de eventos e funções de retorno de chamada no .NET. Diferentemente de ponteiros de função, delegados são seguros, verificáveis e fortemente tipados. Um tipo de delegado pode representar qualquer método de instância ou método estático que tenha uma assinatura compatível. 

Um parâmetro de um delegado será compatível com o parâmetro correspondente de um método se o tipo do parâmetro de delegado for mais restritivo do que o tipo do parâmetro de método, porque isso garante que um argumento passado para o delegado possa ser passado com segurança para o método.

Da mesma forma, o tipo de retorno de um delegado será compatível com o tipo de retorno de um método se o tipo de retorno do método for mais restritivo do que o tipo de retorno do delegado, porque isso garante que o valor retornado do método possa ser convertido com segurança para o tipo retorno do delegado.

Por exemplo, um delegado que tenha um parâmetro de tipo [IEnumerable](xref:System.Collections.IEnumerable) e um tipo de retorno de [Object](xref:System.Object) pode representar um método que tenha um parâmetro de tipo [Object](xref:System.Object) e um valor retornado de tipo [IEnumerable](xref:System.Collections.IEnumerable). 

 Diz-se que um delegado está associado ao método que representa. Além de estar associado ao método, um delegado pode ser associado a um objeto. O objeto representa o primeiro parâmetro do método e é passado para o método sempre que o delegado é invocado. Se o método for um método de instância, o objeto associado será passado como parâmetro `this` implícito (`Me` no Visual Basic). Se o método for estático, o objeto será passado como o primeiro parâmetro formal do método e a assinatura do delegado deverá corresponder aos parâmetros restantes. 
 
 Todos os delegados herdam de [System.MulticastDelegate](xref:System.MulticastDelegate), que herda de [System.Delegate](xref:System.Delegate). As linguagens C# e Visual Basic não permitem a herança desses tipos. Em vez disso, elas fornecem palavras-chave para declarar delegados.
 
 Como delegados herdam de [MulticastDelegate](xref:System.MulticastDelegate), um delegado tem uma lista dos métodos que o delegado representa e que são executados quando o delegado é invocado. Todos os métodos na lista recebem os argumentos fornecidos quando o delegado é invocado.

> [!NOTE]
> O valor retornado não é definido para um delegado que tenha mais de um método na lista de invocação, mesmo que o delegado tenha um tipo de retorno.

Em muitos casos, como acontece com métodos de retorno de chamada, um delegado representa apenas um método e as únicas ações que você precisa realizar são criar e invocar o delegado. 

Para delegados que representam vários métodos, o .NET fornece métodos das classes de delegado [Delegate](xref:System.Delegate) e [MulticastDelegate](xref:System.MulticastDelegate) para dar suporte a operações como adicionar um método à lista de invocação de um delegado (o método [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate))), remover um método (o método [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate))) e obter a lista de invocação (o método [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList)).

> [!NOTE]
> Não é necessário usar esses métodos para delegados de manipuladores de eventos em C# ou Visual Basic, porque essas linguagens fornecem sintaxe para adicionar e remover manipuladores de eventos.

## <a name="type-definitions"></a>Definições de tipo

Uma definição de tipo inclui o seguinte: 

* Qualquer atributo definido no tipo.

* A acessibilidade do tipo (visibilidade).

* O nome do tipo.

* O tipo de base do tipo.

* Qualquer interface implementada pelo tipo.

* Definições para cada um dos membros do tipo.

### <a name="attributes"></a>Atributos

Atributos fornecem metadados adicionais definidos pelo usuário. Com frequência, eles são usados para armazenar informações adicionais sobre um tipo em seu assembly ou para modificar o comportamento de um membro de tipo no ambiente do tempo de design ou do tempo de execução. 

Os atributos são as próprias classes herdadas de [System.Attribute](xref:System.Attribute). Linguagens que dão suporte ao uso de atributos têm sua própria sintaxe para aplicar atributos a um elemento de linguagem. Os atributos podem ser aplicados a praticamente qualquer elemento de linguagem. Os elementos específicos para os quais um atributo pode ser aplicado são definidos pelo [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) aplicado à classe de atributo.

### <a name="type-accessibility"></a>Acessibilidade de tipo

Todos os tipos têm um modificador que rege sua acessibilidade de outros tipos. A tabela a seguir descreve as acessibilidades de tipo que o tempo de execução dá suporte.

Acessibilidade | Descrição
------------- | -----------
public | O tipo é acessível por todos os assemblies.
assembly | O tipo é acessível somente dentro do assembly.

A acessibilidade de um tipo aninhado depende do domínio de acessibilidade, que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido. Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.

O domínio de acessibilidade de um membro aninhado `M` declarado em um tipo `T` em um programa `P` é definido da seguinte forma (observe que `M` pode ser um tipo): 

* Se a acessibilidade declarada de `M` for `public`, o domínio de acessibilidade de `M` será o domínio de acessibilidade de `T`.

* Se a acessibilidade declarada de `M` for `protected internal`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto de programa de `P` e o texto de programa de qualquer tipo derivado de `T` declarado fora de `P`.

* Se a acessibilidade declarada de `M` for `protected`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto do programa de `T` e qualquer tipo derivado de `T`.

* Se a acessibilidade declarada de `M` for `internal`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto de programa de `P`.

* Se a acessibilidade declarada de `M` for `private`, o domínio de acessibilidade de `M` será o texto de programa de `T`.

### <a name="type-names"></a>Nomes de tipo

O Common Type System impõe apenas duas restrições de nomes: 

* Todos os nomes são codificados como cadeias de caracteres Unicode (16 bits).

* Não são permitidos nomes que tenham um valor (16 bits) inserido de 0x0000.

No entanto, a maioria das linguagens impõe restrições adicionais em nomes de tipo. Todas as comparações são feitas em uma base byte por byte e, assim, diferenciam maiúsculas de minúsculas e são independentes de localidade.

Embora um tipo possa referenciar tipos de outros módulos e assemblies, um tipo deve ser totalmente definido em um módulo do .NET. (Dependendo do suporte do compilador, no entanto, ele pode ser dividido em vários arquivos de código-fonte.) Nomes de tipo precisam ser exclusivos somente dentro de um namespace. Para identificar totalmente um tipo, o nome de tipo deve ser qualificado pelo namespace que contém a implementação do tipo.

### <a name="base-types-and-interfaces"></a>Tipos de base e interfaces

Um tipo pode herdar valores e comportamentos de outro tipo. O Common Type System não permite que tipos sejam herdados de mais de um tipo de base.

Um tipo pode implementar um número qualquer de interfaces. Para implementar uma interface, um tipo deve implementar todos os membros virtuais dessa interface. Um método virtual pode ser implementado por um tipo derivado e pode ser invocado estática ou dinamicamente.

## <a name="type-members"></a>Membros de tipos

O tempo de execução permite que você defina os membros do tipo, o que especifica o comportamento e o estado de um tipo. Os membros de tipo incluem o seguinte:

* [Campos](#fields)

* [Propriedades](#properties)

* [Métodos](#methods)

* [Construtores](#constructors)

* [Eventos](#events)

* [Tipos aninhados](#nested-types)

### <a name="fields"></a>Campos

Um campo descreve e contém parte do estado do tipo. Campos podem ser de qualquer tipo com suporte pelo tempo de execução. Geralmente, os campos são `private` ou `protected`, de forma que são acessíveis somente de dentro da classe ou de uma classe derivada. Se o valor de um campo puder ser modificado fora de seu tipo, um acessador do conjunto de propriedades normalmente será usado. Os campos expostos publicamente geralmente são somente leitura e podem ser de dois tipos: 

* Constantes, cujo valor é atribuído no tempo de design. Esses são membros estáticos de uma classe, embora eles não sejam definidos usando a palavra-chave `static` (`Shared` no Visual Basic).

* Variáveis somente leitura, cujos valores podem ser atribuídos no construtor da classe.

O exemplo a seguir ilustra esses dois usos de campos somente leitura.

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a>Propriedades

Uma propriedade nomeia um valor ou um estado do tipo e define métodos para obter ou definir o valor da propriedade. Propriedades podem ser tipos primitivos, coleções de tipos primitivos, tipos definidos pelo usuário ou coleções de tipos definidos pelo usuário. Propriedades são, frequentemente, usadas para manter a interface pública de um tipo independente da representação real do tipo. Isso permite que as propriedades reflitam os valores que não estão armazenados diretamente na classe (por exemplo, quando uma propriedade retorna um valor computado) ou para realizar uma validação antes de os valores serem atribuídos a campos privados. O exemplo a seguir ilustra o padrão mais recente.

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

Além de incluir a própria propriedade, a MSIL (Microsoft Intermediate Language) para um tipo que contém uma propriedade legível inclui um método `get`*_propertyname* e a MSIL para um tipo que contém uma propriedade gravável inclui um método `set`*_propertyname*.

### <a name="methods"></a>Métodos

Um método descreve as operações disponíveis no tipo. A assinatura do método especifica os tipos permitidos de todos seus parâmetros e o valor retornado.

Embora a maioria dos métodos defina o número exato de parâmetros necessários para chamadas de método, alguns métodos dão suporte a um número variável de parâmetros. O parâmetro final declarado desses métodos é marcado com o atributo [ParamArrayAttribute](xref:System.ParamArrayAttribute). Compiladores de linguagem normalmente fornecem uma palavra-chave, como `params` no C# e `ParamArray` no Visual Basic, que tornam o uso explícito de [ParamArrayAttribute](xref:System.ParamArrayAttribute) desnecessário.

### <a name="constructors"></a>Construtores

Um construtor é um tipo especial de método que cria novas instâncias de uma classe ou estrutura. Assim como qualquer outro método, um construtor pode incluir parâmetros. No entanto, os construtores não têm nenhum valor retornado (ou seja, eles retornam `void`). 

Se o código-fonte para uma classe não definir explicitamente um construtor, o compilador incluirá um construtor padrão (sem parâmetros). No entanto, se o código-fonte de uma classe definir apenas construtores com parâmetros, o compilador do C# não gerará um construtor sem parâmetros.

Se o código-fonte de uma estrutura definir construtores, eles deverão ser parametrizados. Uma estrutura não pode definir um construtor padrão (sem parâmetros) e os compiladores não geram construtores sem parâmetros para estruturas ou outros tipos de valor. Todos os tipos de valor têm um construtor padrão implícito. Esse construtor é implementado pelo Common Language Runtime e inicializa todos os campos da estrutura com seus valores padrão. 

### <a name="events"></a>Eventos

Um evento define um incidente que pode ser respondido e define métodos para assinar, cancelar a assinatura e acionar o evento. Eventos são frequentemente usados para informar outros tipos de alterações de estado.

### <a name="nested-types"></a>Tipos aninhados

Um tipo aninhado é um tipo membro de outros tipos. Os tipos aninhados devem ser unidos ao tipo de contenção e não devem ser utilizados como tipos de uso geral. Os tipos aninhados são úteis quando o tipo declarativo usa e cria instâncias do tipo aninhado e o uso do tipo aninhado não é exposto em membros públicos.

Os tipos aninhados são confusos para alguns desenvolvedores e não devem ficar publicamente visíveis, a menos que haja um motivo forte para a visibilidade. Em uma biblioteca bem projetada, os desenvolvedores raramente precisam usar tipos aninhados para instanciar objetos ou declarar variáveis.

## <a name="characteristics-of-type-members"></a>Características de membros de tipo

O Common Type System permite que os membros de tipo tenham várias características. No entanto, as linguagens não necessariamente dão suporte a todas elas. A tabela a seguir descreve as características de um membro.

Característica | Pode ser aplicado a | Descrição
-------------- | ------------ | -----------
abstract | Métodos, propriedades e eventos | O tipo não fornece a implementação do método. Tipos que herdam ou implementam métodos abstratos devem fornecer uma implementação para o método. A única exceção é quando o tipo derivado é um tipo abstrato. Todos os métodos abstratos são virtuais.
private | Todos | Acessível somente dentro do mesmo tipo que o membro ou de um tipo aninhado.
família | Todos | Acessível dentro do mesmo tipo que o membro e de tipos derivados herdados dele.
assembly | Todos | Acessível somente no assembly no qual o tipo é definido.
família e assembly | Todos | Acessíveis somente em tipos qualificados para acesso de família e assembly.
família ou assembly | Todos | Acessíveis somente dentro de tipos qualificados para acesso de família ou assembly.
public | Todos | Acessíveis dentro de qualquer tipo.
final | Métodos, propriedades e eventos | Um método virtual não pode ser substituído em um tipo derivado.
initialize-only | Campos | O valor pode apenas ser inicializado e não pode ser gravado após a inicialização.
instância | Campos, métodos, propriedades e eventos | Se um membro não estiver marcado como `static` (C#), `Shared` (Visual Basic), `virtual` (C#) ou `Overridable` (Visual Basic), ele será um membro de instância (não há palavra-chave de instância). Haverá tantas cópias desses membros na memória quanto objetos que as usam.
literal | Campos | O valor atribuído ao campo é um valor fixo, conhecido no tempo de compilação, de um tipo de valor interno. Às vezes, campos literais são conhecidos como constantes.
newslot ou override | Todos | Define como o membro interage com os membros herdados que têm a mesma assinatura: `newslot` oculta membros herdados que têm a mesma assinatura; `override` substitui a definição de um método virtual herdado. O padrão é newslot.
static | Campos, métodos, propriedades e eventos | O membro pertence ao tipo no qual está definido e não a uma instância particular do tipo; o membro existirá mesmo se uma instância do tipo não tiver sido criada e será compartilhado entre todas as instâncias do tipo.
virtual | Métodos, propriedades e eventos | O método pode ser implementado por um tipo derivado e pode ser invocado estática ou dinamicamente. Se a invocação dinâmica for usada, o tipo da instância que faz a chamada no tempo de execução (em vez do tipo conhecido no tempo de compilação) determinará qual implementação do método será chamada. Para invocar um método virtual estaticamente, a variável precisará ser convertida em um tipo que usa a versão desejada do método.

### <a name="overloading"></a>Sobrecarga

Cada membro de tipo tem uma assinatura exclusiva. Assinaturas de método consistem no nome de método e em uma lista de parâmetros (a ordem e os tipos dos argumentos do método). Os vários métodos com o mesmo nome podem ser definidos em um tipo desde que suas assinaturas sejam diferentes. Quando dois ou mais métodos com o mesmo nome forem definidos, diz-se que o método está sobrecarregado. Por exemplo, em [System.Char](xref:System.Char), o método `IsDigit` está sobrecarregado. Um método utiliza um [Char](xref:System.Char). O outro método utiliza uma [Cadeia de Caracteres](xref:System.String) e um [Int32](xref:System.Int32). 

> [!NOTE]
> O tipo de retorno não é considerado parte da assinatura do método. Ou seja, os métodos não poderão ser sobrecarregados se diferirem somente pelo tipo de retorno.

### <a name="inheriting-overriding-and-hiding-members"></a>Herança, substituição e membros ocultos

Um tipo derivado herda todos os membros de seu tipo de base; ou seja, esses membros são definidos e disponibilizados para o tipo derivado. O comportamento, ou qualidades, de membros herdados pode ser modificado de duas maneiras: 

* Um tipo derivado pode ocultar um membro herdado definindo um novo membro com a mesma assinatura. Isso pode ser feito para fazer um membro privado anteriormente público ou para definir o novo comportamento de um método herdado marcado como `final`.

* Um tipo derivado pode substituir um método virtual herdado. O método de substituição fornece uma nova definição do método que será invocado com base no tipo do valor no tempo de execução em vez do tipo de variável conhecido no tempo de compilação. Um método poderá substituir um método virtual somente se o método virtual não estiver marcado como `final` e o novo método for tão acessível quanto o método virtual.

## <a name="see-also"></a>Consulte também

[Conversão de tipos no .NET Framework](type-conversion.md)


<!--HONumber=Nov16_HO5-->


