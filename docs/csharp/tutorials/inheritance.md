---
title: "Herança em C#"
description: "Aprenda a usar a herança em bibliotecas e aplicativos em C#."
keywords: "herança (C#), classes base, classes derivadas, classes base abstratas"
author: rpetrusha
manager: wpickett
ms.author: ronpet
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 0c76bbcc8e60a2739b8c2735b3576842bd4f0942
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="inheritance-in-c-and-net"></a>Herança em C# e .NET #

## <a name="introduction"></a>Introdução ##

Este tutorial apresenta a herança em C#. Herança é um recurso das linguagens de programação orientadas a objeto que permite a definição de uma classe base que, por sua vez, fornece uma funcionalidade específica (dados e comportamento), e a definição de classes derivadas que herdam ou substituem essa funcionalidade.

## <a name="prerequisites"></a>Pré-requisitos ##

Este tutorial presume que você já instalou o .NET Core. Para obter instruções de instalação, confira [Guia de instalação do .NET Core](https://www.microsoft.com/net/core). Você também precisa de um editor de código. Este tutorial usa o [Visual Studio Code](https://code.visualstudio.com), embora você possa usar qualquer editor de código que quiser.

## <a name="running-the-examples"></a>Como executar os exemplos ##

Para criar e executar os exemplos neste tutorial, use o utilitário [dotnet](../../core/tools/dotnet.md) na linha de comando. Execute estas etapas para cada exemplo:

1. Crie um diretório para armazenar o exemplo.

1. Insira o comando [dotnet new console](../../core/tools/dotnet-new.md) no prompt de comando para criar um novo projeto do .NET Core.

1. Copie e cole o código do exemplo em seu editor de código.

1. Insira o comando [dotnet restore](../../core/tools/dotnet-restore.md) na linha de comando para carregar ou restaurar as dependências do projeto.

1. Insira o comando [dotnet run](../../core/tools/dotnet-run.md) para compilar e executar o exemplo.

## <a name="background-what-is-inheritance"></a>Informações: O que é a herança? ##

*Herança* é um dos atributos fundamentais da programação orientada a objeto. Ela permite que você defina uma classe filha que reutiliza (herda), estende ou modifica o comportamento de uma classe pai. A classe cujos membros são herdados é chamada de *classe base*. A classe que herda os membros da classe base é chamada de *classe derivada*.

C# e .NET oferecem suporte apenas à *herança única*. Ou seja, uma classe pode herdar apenas de uma única classe. No entanto, a herança é transitiva, o que permite que você defina uma hierarquia de herança para um conjunto de tipos. Em outras palavras, o tipo `D` pode herdar do tipo `C`, que herda do tipo `B`, que herda do tipo de classe base `A`. Como a herança é transitiva, os membros do tipo `A` estão disponíveis ao tipo `D`.

Nem todos os membros de uma classe base são herdados por classes derivadas. Os membros a seguir não são herdados:

- [Construtores estáticos](../programming-guide/classes-and-structs/static-constructors.md), que inicializam os dados estáticos de uma classe.

- [Construtores de instância](../programming-guide/classes-and-structs/constructors.md), que você chama para criar uma nova instância da classe. Cada classe deve definir seus próprios construtores.

- [Finalizadores](../programming-guide/classes-and-structs/destructors.md), que são chamados pelo coletor de lixo do tempo de execução para destruir as instâncias de uma classe.

Enquanto todos os outros membros de uma classe base são herdados por classes derivadas, o fato de serem visíveis ou não depende de sua acessibilidade. A acessibilidade de um membro afeta sua visibilidade para classes derivadas da seguinte maneira:

- Membros [Privados](../language-reference/keywords/private.md) são visíveis apenas em classes derivadas que estão aninhadas em sua classe base. Caso contrário, eles não são visíveis em classes derivadas. No exemplo a seguir, `A.B` é uma classe aninhada derivada de `A`, e `C` deriva de `A`. O campo `A.value` privado fica visível em A.B. No entanto, se você remover os comentários do método `C.GetValue` e tentar compilar o exemplo, ele produzirá um erro do compilador CS0122: "'A.value' está inacessível devido ao seu nível de proteção".

   [!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- Membros [Protegidos](../language-reference/keywords/protected.md) são visíveis apenas em classes derivadas.

- Membros [Internos](../language-reference/keywords/protected.md) são visíveis apenas em classes derivadas localizadas no mesmo assembly que a classe base. Eles não são visíveis em classes derivadas localizadas em um assembly diferente da classe base.

- Membros [Públicos] (../language-reference/keywords/protected.md) são visíveis em classes derivadas e fazem parte da interface pública da classe derivada. Membros herdados público podem ser chamados como se tivessem sido definidos na classe derivada. No exemplo a seguir, a classe `A` define um método chamado `Method1`, e a classe `B` herda da classe `A`. Depois, o exemplo chama `Method1` como se fosse um método de instância em `B`.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Classes derivadas também podem *substituir* membros herdados fornecendo uma implementação alternativa. Para poder substituir um membro, o membro na classe base deve ser marcado com a palavra-chave [virtual](../language-reference/keywords/virtual.md). Por padrão, os membros da classe base não são marcados como `virtual` e não podem ser substituídos. A tentativa de substituir um membro não virtual, como faz o exemplo a seguir, gera o erro do compilador CS0506: "<member> não consegue substituir o membro herdado <member>, pois ele não está marcado como virtual, abstrato ou de substituição.

   ```csharp
   public class A
   {
      public void Method1()
      {
         // Do something.
      }
   }

   public class B : A
   {
      public override void Method1()  // Generates CS0506.
      {
         // Do something else.
      }
   }
   ```

Em alguns casos, uma classe derivada *deve* substituir a implementação da classe base. Membros de classe base marcados com a palavra-chave [abstrato](../language-reference/keywords/abstract.md) exigem que as classes derivadas os substituam. A tentativa de compilar o exemplo a seguir gera um erro do compilador CS0534, "<class> não implementa o membro abstrato herdado <member>', pois a classe `B` não fornece uma implementação para `A.Method1`.

   ```csharp
   public abstract class A
   {
      public abstract void Method1();
   }

   public class B : A                  // Generates CS0534.
   {
      public void Method3()
      {
         // Do something.
      }
   }
   ```

A herança se aplica apenas a classes e interfaces. Outras categorias de tipo (structs, delegados e enumerações) não dão suporte à herança. Por isso, a tentativa de compilar o código da seguinte maneira produz um erro de compilador CS0527: "O tipo 'ValueType' na lista de interface não é uma interface". A mensagem de erro indica que, embora você possa definir as interfaces implementadas por um struct, não há suporte para a herança.

   ```csharp
   using System;

   public struct ValueStructure : ValueType       // Generates CS0527.
   {
   }
   ```

## <a name="implicit-inheritance"></a>Herança implícita ##

Apesar dos tipos possíveis de herança por meio de herança única, todos os tipos no sistema de tipo .NET herdam implicitamente de @System.Object ou de um tipo derivado dele. Isso garante a disponibilidade de funcionalidades comuns para qualquer tipo.

Para ver o que significa herança implícita, vamos definir uma nova classe, `SimpleClass`, que é simplesmente uma definição de classe vazia:

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Podemos usar reflexão (o que nos permite inspecionar os metadados de um tipo para obter informações sobre o tipo) para obter uma lista dos membros que pertencem ao tipo `SimpleClass`. Embora não tenhamos definido membros em nossa classe `SimpleClass`, a saída do exemplo indica que ele tem nove membros na verdade. Um deles é um construtor sem parâmetros (ou padrão) fornecido automaticamente para o tipo `SimpleClass` pelo compilador em C#. Os membros sete e oito são membros de @System.Object, o tipo do qual todas as classes e interfaces no sistema do tipo .NET herdam implicitamente.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

A herança implícita da classe @System.Object torna esses métodos disponíveis para a classe `SimpleClass`:

- O método `ToString` público, que converte um objeto `SimpleClass` em sua representação de cadeia de caracteres, o nome de tipo totalmente qualificado. Nesse caso, o método `ToString` retorna a cadeia de caracteres "SimpleClass".

- Três métodos de teste de igualdade de dois objetos: o método `Equals(Object)` da instância pública, o método `Equals(Object, Object)` do público estático e o método `ReferenceEquals(Object, Object)` de público estático. Por padrão, esses métodos testam a igualdade de referência; ou seja, para que seja iguais, duas variáveis de objeto devem fazer referência ao mesmo objeto.

- O método público `GetHashCode`, que calcula um valor que permite o uso de uma instância do tipo em conjuntos de hash.

- O método público `GetType`, que retorna um objeto @System.Type que representa o tipo `SimpleClass`.

- O método protegido @System.Object.Finalize, que é projetado para liberar recursos não gerenciados antes que a memória de um objeto seja reivindicada pelo coletor de lixo.

- O método protegido @System.Object.MemberwiseClone, que cria um clone superficial do objeto atual.

Devido à herança implícita, podemos chamar qualquer membro herdado de um objeto `SimpleClass` como se fosse um membro definido na classe `SimpleClass`. Por exemplo, o exemplo a seguir chama o método `SimpleClass.ToString`, que `SimpleClass` herda de @System.Object.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

A tabela a seguir lista as categorias de tipos que você pode criar em C#, e os tipos de onde eles herdam implicitamente. Cada tipo base disponibiliza um conjunto diferente de membros por meio de herança para tipos derivados implicitamente.

| Categoria do tipo | Herda implicitamente de... |
| :--- | :---: | ---: |
| classe | @System.Object |
| struct | @System.ValueType, @System.Object |
| enum | @System.Enum, System.ValueType, @System.Object |
| delegado | @System.MulticastDelegate, @System.Delegate, @System.Object |

## <a name="inheritance-and-an-is-a-relationship"></a>Herança e um relacionamento "é um(a)" ##

Normalmente, a herança é usada para expressar um relacionamento "é um(a)" entre uma classe base e uma ou mais classes derivadas, em que as classes derivadas são versões especializadas da classe base; a classe derivada é um tipo de classe base. Por exemplo, a classe `Publication` representa uma publicação de qualquer tipo e as classes `Book` e `Magazine` representam tipos específicos de publicações.

   [!NOTE] Uma classe ou struct pode implementar uma ou mais interfaces. Embora a implementação da interface seja apresentada geralmente como uma alternativa para herança única, ou como uma forma de usar a herança com structs, ela tem como objetivo expressar um relacionamento diferente (um relacionamento "pode fazer") entre uma interface e seu tipo de implementação em comparação com a herança. Uma interface define um subconjunto de funcionalidades (como a capacidade de testar a igualdade, comparar ou classificar objetos ou dar suporte à formatação e análise sensível à cultura) que disponibiliza para seus tipos de implementação.

Observe que "é um(a)" também expressa o relacionamento entre um tipo e uma instanciação específica desse tipo. No exemplo a seguir, `Automobile` é uma classe que tem três propriedades somente leitura exclusivas: `Moke`, o fabricante do automóvel; `Model`, o tipo de automóvel; e `Year`, o ano de fabricação. Nossa classe `Automobile` também tem um construtor cujos argumentos são atribuídos aos valores de propriedade. Ela também substitui o método @System.Object.ToString para produzir uma cadeia de caracteres que identifica exclusivamente a instância `Automobile` em vez da classe `Automobile`.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Nesse caso, não devemos depender da herança para representar marcas e modelos de carro específicos. Por exemplo, não precisamos definir um tipo `Packard` para representar automóveis fabricados pela empresa Packard Motor Car Company. Em vez disso, podemos representá-los criando um objeto `Automobile` com os valores apropriados passados ao construtor de classe, como o exemplo a seguir.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Um relacionamento é-um(a) baseado na herança é mais bem aplicado a uma classe base e em classes derivadas que adicionam outros membros à classe base, ou que exigem funcionalidades adicionais não incluídas na classe base.

## <a name="designing-the-base-class-and-derived-classes"></a>Criação da classe base e das classes derivadas ##

Vamos examinar o processo de criação de uma classe base e de suas classes derivadas. Nesta seção, definiremos uma classe base, `Publication`, que representa uma publicação de qualquer tipo, como um livro, revista, jornal, diário, artigo etc. Também definiremos uma classe `Book` que deriva de `Publication`. Poderíamos ampliar facilmente o exemplo para definir outras classes derivadas, como `Magazine`, `Journal`, `Newspaper` e `Article`.

### <a name="the-base-publication-class"></a>A classe base `Publication` ###

Ao criar nossa classe `Publication`, precisamos tomar várias decisões de design:

- Quais membros incluir em nossa classe base `Publication` e se os membros `Publication` fornecem implementações de método, ou se `Publication` é uma classe base abstrata que serve como modelo para suas classes derivadas.

   Nesse caso, a classe `Publication` fornecerá implementações de método. A seção [Criação de classes base abstratas e de suas classes derivadas](#abstract) contém um exemplo que usa uma classe base abstrata para definir os métodos que as classes derivadas devem substituir. As classes derivadas são livres para fornecer qualquer implementação adequada ao tipo derivado.

   A capacidade de reutilizar o código (ou seja, várias classes derivadas compartilham a declaração e a implementação dos métodos de classe base, e não é necessário substituí-las) é uma vantagem das classes base não abstratas. Portanto, devemos acrescentar membros a `Publication` se houver a probabilidade do código deles ser compartilhado por um ou mais tipos `Publication` especializados. Se não conseguirmos fazer isso de forma eficiente, poderemos precisar fornecer implementações de membro praticamente idênticas em classes derivadas, em vez de uma única implementação na classe base. A necessidade de manter o código duplicado em vários locais é uma possível fonte de bugs.

   Para maximizar a reutilização do código e criar uma hierarquia de herança lógica e intuitiva, queremos garantir a inclusão na classe `Publication` apenas dos dados e da funcionalidade comuns a todos ou à maioria das publicações. Depois, as classes derivadas implementam os membros exclusivos a determinados tipos de publicação que eles representam.

- O quanto devemos ampliar nossa hierarquia de classe. Queremos desenvolver uma hierarquia de três ou mais classes, em vez de simplesmente uma classe base e uma ou mais classes derivadas? Por exemplo, `Publication` poderia ser uma classe base de `Periodical`, que por sua vez é uma classe base de `Magazine`, `Journal` e `Newspaper`.

   Para nosso exemplo, usaremos a hierarquia simples de uma classe `Publication` e uma única classe derivada, `Book`. Poderíamos ampliar facilmente o exemplo para criar algumas classes adicionais derivadas de `Publication`, como `Magazine` e `Article`.

- Se faz sentido instanciar a classe base. Se não fizer, deveremos aplicar a palavra-chave [abstract](../language-reference/keywords/abstract.md) à classe. Se for feita uma tentativa de instanciar uma classe marcada com a palavra-chave `abstract` por uma chamada direta para o construtor de classe, o compilador de C# gerará o erro CS0144, "Não é possível criar uma instância da classe abstrata ou interface". Se for feita uma tentativa de instanciar a classe por meio da reflexão, o método de reflexão lançará um @System.MemberAccessException. Caso contrário, nossa classe `Publication` poderá ser instanciada chamando seu construtor de classe.

   Por padrão, uma classe base pode ser instanciada chamando seu construtor de classe. Observe que não precisamos definir explicitamente um construtor de classe. Se não houver um presente no código-fonte da classe base, o compilador de C# fornecerá automaticamente um construtor (sem parâmetros) padrão.

   Para nosso exemplo, marcaremos a classe `Publication` como [abstract](../language-reference/keywords/abstract.md), para que não possa ser instanciada.

- Se as classes derivadas devem herdar a implementação da classe base de membros específicos, ou se têm a opção de substituir a implementação da classe base. Precisamos usar a palavra-chave [virtual](../language-reference/keywords/virtual.md) para permitir que classes derivadas substituam um método de classe base. Por padrão, os métodos definidos na classe base *não* são substituíveis.

- Se uma classe derivada representa a classe final na hierarquia de herança e não pode se ser usada como uma classe base para outras classes derivadas. Por padrão, qualquer classe pode servir como classe base. Podemos aplicar a palavra-chave [sealed](../language-reference/keywords/sealed.md) para indicar que uma classe não pode servir como classe base para quaisquer classes adicionais. A tentativa de derivar de uma classe selada gerou o erro do compilador CS0509, "não é possível derivar do tipo sealed <typeName>".

   Para nosso exemplo, marcaremos nossa classe derivada como `sealed`.

O exemplo a seguir mostra o código-fonte para a classe `Publication`, bem como uma enumeração `PublicationType` que é retornada pela propriedade `Publication.PublicationType`. Além dos membros herdados de @System.Object, a classe `Publication` define os seguintes membros exclusivos e substituições de membro:

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Um construtor

  Como a classe `Publication` é `abstract`, ela não pode ser instanciada diretamente no código, conforme exibido a seguir:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  No entanto, o construtor de instância pode ser chamado diretamente dos construtores de classe derivada, como mostra o código-fonte para a classe `Book`.

- Duas propriedades relacionadas à publicação

  `Title` é uma propriedade @System.String somente leitura cujo valor é fornecido pela chamada do construtor `Publication`, que armazena o valor em um campo privado chamado `pubTitle`.

  `Pages` é uma propriedade @System.Int32 de leitura-gravação que indica o número total de páginas da publicação. O valor é armazenado em um campo privado chamado `totalPages`. O lançamento deve ser de um número positivo ou de um @System.ArgumentOutOfRangeException.

- Membros relacionados ao publicador

  Duas propriedades somente leitura, `Publisher` e `Type`, retornam o valor dos campos `pubName` e `pubType` privados. Originalmente, os valores eram fornecidos pela chamada para o construtor da classe `Publication`.

- Membros relacionados à publicação

  Dois métodos, `Publish` e `GetPublicationDate`, definem e retornam a data de publicação. O método `Publish` define um sinalizador `published` privado como `true` quando ele é chamado, e atribui a data passada para ele como um argumento para o campo `datePublished` privado. O método `GetPublicationDate` retorna a cadeia de caracteres "NYP" se o sinalizador `published` for `false`, e o valor do campo `datePublished` for `true`.

- Membros relacionados a direitos autorais

  O método `Copyright` usa o nome do proprietário dos direitos autorais e o ano dos direitos autorais como argumentos, e os atribui aos campos `copyrName` e `copyrDate` privados. Os valores podem ser recuperados das propriedades `CopyrightName` e `CopyrightDate`.

- Uma substituição do método `ToString`

  Se um tipo não substituir o método @System.Object.ToString, ele retornará o nome totalmente qualificado do tipo, que é de pouca utilidade na diferenciação de uma instância para outra. A classe `Publication` substitui @System.Object.ToString para retornar o valor da propriedade `Title`.

A figura a seguir ilustra o relacionamento entre nossa classe base `Publication` e sua classe @System.Object herdada implicitamente.

![As classes Object e Publication](media/publication-class.jpg)

### <a name="the-book-class"></a>A classe `Book` ###

A classe `Book` representa um livro como tipo especializado de publicação. O exemplo a seguir mostra o código-fonte para a classe `Book`.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Além dos membros herdados de `Publication`, a classe `Book` define os seguintes membros exclusivos e substituições de membro:

- Dois construtores

  Os dois construtores `Book` compartilham três parâmetros comuns. Dois, *title* e *publisher*, correspondem aos parâmetros do construtor `Publication`. O terceiro é *author*, que é armazenado como um campo `authorName` privado. Um construtor inclui um parâmetro *isbn*, que é armazenado no campo `id` privado.

  O primeiro construtor usa a palavra-chave [this](../language-reference/keywords/this.md) para chamar o outro construtor. Esse é um padrão comum na definição de construtores; construtores com menos parâmetros fornecem valores padrão ao chamar o construtor com o maior número de parâmetros.

  O segundo construtor usa a palavra-chave [base](../language-reference/keywords/base.md) para passar o título e o nome do publicador para o construtor da classe base. Se você não fizer uma chamada explícita para um construtor de classe base em seu código-fonte, o compilador de C# fornecerá automaticamente uma chamada para a classe base padrão ou para o construtor sem parâmetros.

- Uma propriedade `ISBN` somente leitura, que retorna o ISBN (International Standard Book Number) do objeto `Book`, um número exclusivo com 10 ou 13 dígitos. O ISBN é fornecido como um argumento para um dos construtores `Book` e é armazenado no campo `id` privado.

- Uma propriedade `Author` somente leitura. O nome do autor é fornecido como um argumento para os dois construtores `Book` e é armazenado no campo `authorName` privado.

- Duas propriedades somente leitura relacionadas ao preço, `Price` e `Currency`. Seus valores são fornecidos como argumentos em uma chamada do método `SetPrice`. O preço é armazenado em um campo privado, `bookPrice`. A propriedade `Currency` é o símbolo de moeda ISO de três dígitos (por exemplo, USD para dólar americano) e é armazenada no campo `ISOCurrencySymbol` privado. Símbolos de moeda ISO podem ser obtidos da propriedade @System.Globalization.RegionInfo.ISOCurrencySymbol.

- Um método `SetPrice`, que define os valores dos campos `bookPrice` e `ISOCurrencySymbol`. Estes são os valores retornados pela propriedade `Price` e `Currency`.

- Substitui o método `ToString` (herdado de `Publication`) e os métodos @System.Object.Equals(System.Object) e @System.Object.GetHashCode (herdados de @System.Object).

  A menos que seja substituído, o método @System.Object.Equals (System.Object) testa a igualdade de referência. Ou seja, duas variáveis de objeto são consideradas iguais se fizerem referência ao mesmo objeto. No caso da classe `Book`, por outro lado, dois objetos `Book` devem ser iguais se eles tiverem o mesmo ISBN.

  Ao substituir o método @System.Object.Equals (System.Object), substitua também o método @System.Object.GetHashCode, que retorna um valor usado pelo tempo de execução para armazenar itens em conjuntos de hash para uma recuperação eficiente. O código de hash deve retornar um valor que é consistente com o teste de igualdade. Como substituímos @System.Object.Equals(System.Object) para retornar `true`, se as propriedades ISBN de dois objetos `Book` forem iguais, retornaremos o código hash computado chamando o método @System.String.GetHashCode da cadeia de caracteres retornada pela propriedade `ISBN`.

A figura a seguir ilustra o relacionamento entre a classe `Book` e `Publication`, sua classe base.

![Classes Publication e Book](media/book-class.jpg)

Agora podemos instanciar um objeto `Book`, chamar seus membros exclusivos e herdados e passá-lo como um argumento para um método que espera um parâmetro do tipo `Publication` ou do tipo `Book`, como mostra o exemplo a seguir.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="abstract"></a> Criação de classes base abstratas e suas classes derivadas ##

No exemplo anterior, definimos uma classe base que forneceu uma implementação para diversos métodos, a fim de permitir que classes derivadas compartilhem código. Em muitos casos, no entanto, não espera-se que a classe base forneça uma implementação. Em vez disso, a classe base é uma *classe abstrata*; ela serve como um modelo que define os membros que cada classe derivada deve implementar. Normalmente, no caso de uma classe base abstrata, a implementação de cada tipo derivado é exclusiva para esse tipo.

Por exemplo, cada forma geométrica bidimensional fechada inclui duas propriedades: área, a extensão interna da forma; e perímetro, ou a distância entre as bordas da forma. A maneira com a qual essas propriedades são calculadas, no entanto, depende completamente da forma específica. Por exemplo, a fórmula para calcular o perímetro (ou circunferência) de um círculo, é muito diferente de um triângulo.

O exemplo a seguir define uma classe base abstrata denominada `Shape` que define duas propriedades: `Area` e `Perimeter`. Observe que, além de marcar a classe com a palavra-chave [abstract](../language-reference/keywords/abstract.md), cada membro de instância também é marcado com a palavra-chave [abstract](../language-reference/keywords/abstract.md). Nesse caso, o `Shape` também substitui o método @System.Object.ToString para retornar o nome do tipo, em vez de seu nome totalmente qualificado. E define dois membros estáticos, `GetArea` e `GetPerimeter`, que permitem a recuperação fácil da área e do perímetro de uma instância de qualquer classe derivada. Quando passamos uma instância de uma classe derivada para qualquer um desses métodos, o tempo de execução chama a substituição do método da classe derivada.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Em seguida, podemos derivar algumas classes de `Shape` que representam formas específicas. O exemplo a seguir define três classes, `Triangle`, `Rectangle` e `Circle`. Cada uma usa uma fórmula exclusiva para essa forma específica para calcular a área e o perímetro. Algumas das classes derivadas também definem propriedades, como `Rectangle.Diagonal` e `Circle.Diameter`, que são exclusivas para a forma que representam.

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

O exemplo a seguir usa objetos derivados de `Shape`. Ele cria uma matriz de objetos derivados de `Shape` e chama os métodos estáticos da classe `Shape`, que retorna valores de propriedade `Shape`. Observe que o tempo de execução recupera os valores das propriedades substituídas dos tipos derivados. O exemplo também converte cada objeto `Shape` na matriz ao seu tipo derivado e, se a conversão for bem-sucedida, recupera as propriedades dessa subclasse específica de `Shape`. 

[!code-csharp[Herança](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Consulte também ##

[Classes e objetos](../tour-of-csharp/classes-and-objects.md)</br>
[Herança (Guia de Programação em C#)](../programming-guide/classes-and-structs/inheritance.md)

