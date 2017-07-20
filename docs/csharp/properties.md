---
title: Propriedades
description: Propriedades
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.translationtype: Human Translation
ms.sourcegitcommit: f9eab74a3b259037aff30320753191eee95aa974
ms.openlocfilehash: 763a76a8ea0e48fd6935c951ce584efad50dabb9
ms.contentlocale: pt-br
ms.lasthandoff: 04/25/2017

---

# <a name="properties"></a>Propriedades

As propriedades são cidadãos de primeira classe no C#. A linguagem define uma sintaxe que permite aos desenvolvedores escrever código que expresse sua intenção de design com precisão.

As propriedades se comportam como campos quando são acessadas.
No entanto, diferentemente dos campos, as propriedades são implementadas com acessadores, que definem as instruções que são executadas quando uma propriedade é acessada ou atribuída.

## <a name="property-syntax"></a>Sintaxe de propriedade

A sintaxe para propriedades é uma extensão natural para os campos. Um campo define um local de armazenamento:

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

Uma definição de propriedade contém declarações para um acessador `get` e `set` que recupera e atribui o valor dessa propriedade:

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

A sintaxe mostrada acima é a sintaxe da *propriedade automática*. O compilador gera o local de armazenamento para o campo que dá suporte à propriedade. O compilador também implementa o corpo dos acessadores `get` e `set`.

Às vezes, você precisa inicializar uma propriedade para um valor diferente do padrão para seu tipo.  O C# permite isso definindo um valor após a chave de fechamento da propriedade. Você pode preferir que o valor inicial para a propriedade `FirstName` seja a cadeia de caracteres vazia em vez de `null`. Você deve especificar isso conforme mostrado abaixo:

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

Isso é mais útil para propriedades somente leitura, como você verá posteriormente neste tópico.

Você mesmo também pode definir o armazenamento, conforme mostrado abaixo:

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Quando uma implementação de propriedade é uma única expressão, você pode usar *membros aptos para expressão* para getter ou setter:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Essa sintaxe simplificada será usada quando aplicável ao longo deste tópico.

A definição da propriedade mostrada acima é uma propriedade de leitura/gravação. Observe a palavra-chave `value` no acessador set. O acessador `set` sempre tem um parâmetro único chamado `value`. O acessador `get` deve retornar um valor que seja conversível para o tipo da propriedade (`string`, neste exemplo).
 
Essas são as noções básicas sobre a sintaxe. Há muitas variações diferentes que oferecem suporte a uma variedade de linguagens de design diferentes. Vamos explorá-las e conhecer as opções de sintaxe para cada uma.

## <a name="scenarios"></a>Cenários

Os exemplos acima mostraram um dos casos mais simples de definição de propriedade: uma propriedade de leitura/gravação sem validação. Ao escrever o código que você deseja nos acessadores `get` e `set`, você pode criar vários cenários diferentes.

### <a name="validation"></a>Validação

Você pode escrever código no acessador `set` para garantir que os valores representados por uma propriedade sejam sempre válidos. Por exemplo, suponha que uma regra para a classe `Person` é que o nome não pode ser um espaço em branco. Você escreveria isso da seguinte maneira:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

O exemplo acima aplica a regra de que o nome não deve ser em branco ou espaço em branco. Se um desenvolvedor escreve

```csharp
hero.FirstName = "";
```

Essa atribuição lança uma `ArgumentException`. Como um acessador set de propriedade deve ter um tipo de retorno void, você relata erros no acessador set lançando uma exceção.

Esse é um caso simples de validação. Você pode estender essa mesma sintaxe para qualquer coisa necessária em seu cenário. Você pode verificar as relações entre diferentes propriedades ou validar em relação a qualquer condição externa. Todas as instruções de C# válidas são válidas em um acessador de propriedade.

### <a name="read-only"></a>Somente leitura

Até aqui, todas as definições de propriedade que você viu são de propriedades de leitura/gravação com acessadores públicos. Essa não é a única acessibilidade válida para as propriedades.
Você pode criar propriedades somente leitura ou dar acessibilidade diferente aos acessadores get e set. Suponha que sua classe `Person` só deva habilitar a alteração do valor da propriedade `FirstName` em outros métodos naquela classe. Você pode dar acessibilidade `private` ao acessador set, em vez de `public`:

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

Agora, a propriedade `FirstName` pode ser acessada de qualquer código, mas só pode ser atribuída de outro código na classe `Person`.

Você pode adicionar qualquer modificador de acesso restritivo aos acessadores get ou set. Nenhum modificador de acesso que você colocar no acessador individual deve ser mais limitado que o modificador de acesso da definição de propriedade. O que está acima é válido porque a propriedade `FirstName` é `public`, mas o acessador set é `private`. Você não pode declarar uma propriedade `private` com um acessador `public`. As declarações de propriedade também podem ser declaradas `protected`, `internal`, `protected internal` ou até mesmo `private`.   

Também é válido colocar o modificador mais restritivo no acessador `get`. Por exemplo, você poderia ter uma propriedade `public`, mas restringir o acessador `get` como `private`. Esse cenário raramente acontece na prática.

Você também pode restringir modificações a uma propriedade para que ela possa ser definida somente em um construtor ou um inicializador de propriedade. Você pode modificar a classe `Person` da seguinte maneira:

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

Esse recurso é mais comumente usado para inicializar coleções que são expostas como propriedades somente leitura:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Propriedades computadas

Uma propriedade não precisa simplesmente retornar o valor de um campo de membro. Você pode criar propriedades que retornam um valor computado. Vamos expandir o objeto `Person` para retornar o nome completo, computado pela concatenação dos nomes e sobrenomes:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

O exemplo acima usa a sintaxe de *interpolação de cadeia de caracteres* para criar a cadeia de caracteres formatada para o nome completo.

Você também pode usar *membros aptos para expressão*, que fornecem uma maneira mais sucinta para criar a propriedade `FullName` computada:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
Os *membros aptos para expressão* usam a sintaxe *expressão lambda* para definir um método que contenha uma única expressão. Aqui, essa expressão retorna o nome completo do objeto person.

### <a name="lazy-evaluated-properties"></a>Propriedades avaliadas lentas

Você pode combinar o conceito de uma propriedade computada com o armazenamento e criar uma *propriedade avaliada lenta*.  Por exemplo, você poderia atualizar a propriedade `FullName` para que a formatação da cadeia de caracteres só acontecesse na primeira vez que ela foi acessada:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

No entanto, o código acima contém um bug. Se o código atualizar o valor das propriedades `FirstName` ou `LastName`, o campo `fullName`, anteriormente avaliado, será inválido. Você precisa atualizar os acessadores `set` das propriedades `FirstName` e `LastName` para que o campo `fullName` seja calculado novamente:

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Esta versão final avalia a propriedade `FullName` apenas quando necessário.
Se a versão calculada anteriormente for válida, ela será usada. Se outra alteração de estado invalidar a versão calculada anteriormente, ela será recalculada. Os desenvolvedores que usam essa classe não precisam saber dos detalhes da implementação. Nenhuma dessas alterações internas afetam o uso do objeto Person. Esse é o motivo principal para o uso de propriedades para expor os membros de dados de um objeto.
 
### <a name="inotifypropertychanged"></a>INotifyPropertyChanged

A última situação em que você precisa escrever código em um acessador de propriedade é para oferecer suporte à interface `INotifyPropertyChanged`, usada para notificar os clientes de vinculação de dados que um valor foi alterado. Quando o valor de uma propriedade for alterado, o objeto aciona o evento `PropertyChanged` para indicar a alteração. As bibliotecas de vinculação de dados, por sua vez, atualizam os elementos de exibição com base nessa alteração. O código a seguir mostra como você implementaria `INotifyPropertyChanged` para a propriedade `FirstName` dessa classe person.

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

O operador `?.` é chamado de *operador condicional nulo*. Ele verifica uma referência nula antes de avaliar o lado direito do operador. O resultado final é que, se não houver nenhum assinante para o evento `PropertyChanged`, o código para acionar o evento não é executado. Ela lançaria uma `NullReferenceException` sem essa verificação, nesse caso. Consulte a página sobre [`events`](delegates-events.md) para obter mais detalhes. Este exemplo também usa o novo operador `nameof` para converter o símbolo de nome da propriedade em sua representação de texto.
O uso de `nameof` pode reduzir erros no local em que você digitou errado o nome da propriedade.

Novamente, este é um exemplo de um caso em que você pode escrever código em seus acessadores para dar suporte aos cenários você precisa.

## <a name="summing-up"></a>Resumindo

As propriedades são uma forma de campos inteligentes em uma classe ou objeto. De fora do objeto, elas parecem como campos no objeto. No entanto, as propriedades podem ser implementadas usando a paleta completa de funcionalidades do C#.
Você pode fornecer validação, acessibilidade diferente, avaliação lenta ou quaisquer requisitos necessários aos seus cenários.

