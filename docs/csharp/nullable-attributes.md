---
title: Atualizar APIs para tipos de referência anulados com atributos que definem expectativas de valores nulos
description: Aprenda a usar os atributos descritivos AllowNull, DisallowNull, MaybeNull, NotNull e muito mais para descrever completamente o estado nulo de suas APIs.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5d7a864ba1b66ad6b4ae7b0391d170a29147c537
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805839"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Atualize bibliotecas para usar tipos de referência anulados e comunicar regras anuladas aos chamadores

A adição de tipos de [referência anulados](nullable-references.md) significa que você pode declarar se um `null` valor é permitido ou esperado para cada variável. Além disso, você pode aplicar uma `AllowNull` `DisallowNull`série `MaybeNull` `NotNull`de `NotNullWhen` `MaybeNullWhen`atributos: , , , , , , , , e `NotNullIfNotNull` descrever completamente os estados nulos de argumento e valores de devolução. Isso proporciona uma grande experiência enquanto você escreve código. Você recebe avisos se uma variável não-nula pode ser definida como `null`. Você recebe avisos se uma variável anulada não for verificada nula antes de desreferencia-la. Atualizar suas bibliotecas pode levar tempo, mas os pagamentos valem a pena. Quanto mais informações você fornecer ao compilador sobre *quando* um `null` valor é permitido ou proibido, melhores avisos os usuários de sua API receberão. Vamos começar com um exemplo familiar. Imagine que sua biblioteca tem a seguinte API para recuperar uma seqüência de recursos:

```csharp
bool TryGetMessage(string key, out string message)
```

O exemplo anterior segue `Try*` o padrão familiar em .NET. Existem dois argumentos de referência `key` para `message` esta API: o e o parâmetro. Esta API tem as seguintes regras relativas à nulidade desses argumentos:

- Os chamadores `null` não devem `key`passar como argumento para .
- Os chamadores podem passar `null` uma variável `message`cujo valor é como o argumento para .
- Se `TryGetMessage` o `true`método retornar, `message` o valor de não é nulo. Se o valor `false,` de `message` devolução for o valor de (e seu estado nulo) é nulo.

A regra `key` para pode ser completamente expressa `key` pelo tipo de variável: deve ser um tipo de referência não anulado. O `message` parâmetro é mais complexo. Permite `null` como argumento, mas garante que, `out` no sucesso, esse argumento não é nulo. Para esses cenários, você precisa de um vocabulário mais rico para descrever as expectativas.

Atualizar sua biblioteca para referências anuladas `?` requer mais do que polvilhar algumas das variáveis e nomes de tipo. O exemplo anterior mostra que você precisa examinar suas APIs e considerar suas expectativas para cada argumento de entrada. Considere as garantias para o `out` valor `ref` de devolução, e quaisquer ou argumentos sobre o retorno do método. Em seguida, comunique essas regras ao compilador, e o compilador fornecerá avisos quando os chamadores não cumprirem essas regras.

Este trabalho leva tempo. Vamos começar com estratégias para tornar sua biblioteca ou aplicativo anulado, ao mesmo tempo em que equilibra mos outros requisitos e entregas. Você verá como equilibrar o desenvolvimento contínuo permitindo tipos de referência anulados. Você aprenderá desafios para definições de tipos genéricos. Você aprenderá a aplicar atributos para descrever pré e pós-condições em APIs individuais.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Escolha uma estratégia para tipos de referência anulados

A primeira escolha é se os tipos de referência anulados devem estar ligados ou desligados por padrão. Você tem duas estratégias:

- Habilite tipos de referência anulados para todo o projeto e desative-o em código que não está pronto.
- Apenas habilite tipos de referência anulados para código que tenha sido anotado para tipos de referência anulados.

A primeira estratégia funciona melhor quando você está adicionando outros recursos à biblioteca à medida que você atualizá-la para tipos de referência anulados. Todo novo desenvolvimento é anulado. Ao atualizar o código existente, você habilita tipos de referência anulados nessas classes.

Seguindo esta primeira estratégia, você faz o seguinte:

1. Habilite tipos de referência anulados `<Nullable>enable</Nullable>` para todo o projeto adicionando o elemento aos seus arquivos *csproj.*
1. Adicione `#nullable disable` o pragma a cada arquivo de origem do seu projeto.
1. Ao trabalhar em cada arquivo, remova o pragma e aborde quaisquer avisos.

Esta primeira estratégia tem um trabalho mais inicial para adicionar o pragma a cada arquivo. A vantagem é que cada novo arquivo de código adicionado ao projeto será anulado. Qualquer novo trabalho será anulado; apenas o código existente deve ser atualizado.

A segunda estratégia funciona melhor se a biblioteca estiver geralmente estável, e o foco principal do desenvolvimento é adotar tipos de referência anulados. Você liga os tipos de referência anulados à medida que anota APIs. Quando terminar, você habilita tipos de referência anulados para todo o projeto.

Seguindo esta segunda estratégia você faz o seguinte:

1. Adicione `#nullable enable` o pragma ao arquivo que você deseja tornar anulado.
1. Dirija qualquer aviso.
1. Continue estes dois primeiros passos até que você tenha feito toda a biblioteca anulada.
1. Habilite tipos anulados para `<Nullable>enable</Nullable>` todo o projeto adicionando o elemento aos seus arquivos *csproj.*
1. Remova `#nullable enable` os pragmas, já que eles não são mais necessários.

Esta segunda estratégia tem menos trabalho na frente. A troca é que a primeira tarefa quando você cria um novo arquivo é adicionar o pragma e torná-lo anulado. Se algum desenvolvedor da sua equipe esquecer, esse novo código está agora em atraso no trabalho para tornar todo o código anulado.

Qual dessas estratégias você escolhe depende de quanto desenvolvimento ativo está acontecendo em seu projeto. Quanto mais maduro e estável o seu projeto, melhor a segunda estratégia. Quanto mais recursos estão sendo desenvolvidos, melhor a primeira estratégia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Os avisos anulados devem introduzir alterações de quebra?

Antes de habilitar tipos de referência anulados, as variáveis são consideradas *alheias a nulidade*. Uma vez habilitado tipos de referência anulados, todas essas variáveis são *não anuladas*. O compilador emitirá avisos se essas variáveis não forem inicializadas para valores não nulos.

Outra fonte provável de avisos são os valores de devolução quando o valor não foi inicializado.

O primeiro passo para abordar os avisos `?` do compilador é usar anotações em parâmetros e tipos de retorno para indicar quando argumentos ou valores de devolução podem ser nulos. Quando as variáveis de referência não devem ser nulas, a declaração original está correta. Ao fazer isso, seu objetivo não é apenas corrigir avisos. O objetivo mais importante é fazer com que o compilador entenda sua intenção de potenciais valores nulos. Ao examinar os avisos, você chega à sua próxima grande decisão para sua biblioteca. Deseja considerar modificar assinaturas de API para comunicar mais claramente sua intenção de design? Uma melhor assinatura de `TryGetMessage` API para o método examinado anteriormente poderia ser:

```csharp
string? TryGetMessage(string key);
```

O valor de retorno indica sucesso ou falha, e carrega o valor se o valor foi encontrado. Em muitos casos, alterar assinaturas de API pode melhorar a forma como comunicam valores nulos.

No entanto, para bibliotecas públicas ou bibliotecas com grandes bases de usuários, você pode preferir não introduzir nenhuma alteração de assinatura da API. Para esses casos e outros padrões comuns, você pode aplicar atributos `null`para definir mais claramente quando um argumento ou valor de retorno pode ser . Se você considerar ou não alterar a superfície de sua API, você provavelmente descobrirá `null` que anotações de tipo por si só não são suficientes para descrever valores para argumentos ou valores de retorno. Nesses casos, você pode aplicar atributos para descrever mais claramente uma API.

## <a name="attributes-extend-type-annotations"></a>Atributos estendem anotações de tipo

Vários atributos foram adicionados para expressar informações adicionais sobre o estado nulo das variáveis. Todo o código que você escreveu antes de C# 8 introduzir tipos de referência nulos foi *nulo alheio*. Isso significa que qualquer variável de tipo de referência pode ser nula, mas verificações nulas não são necessárias. Uma vez que seu código é *anulado ciente,* essas regras mudam. Os tipos de `null` referência nunca devem ser o valor, e os tipos de referência anulados devem ser verificados `null` antes de serem desreferenciados.

As regras para suas APIs são provavelmente `TryGetValue` mais complicadas, como você viu com o cenário da API. Muitas de suas APIs têm regras mais complexas para `null`quando as variáveis podem ou não ser . Nestes casos, você usará um dos seguintes atributos para expressar essas regras:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.
- [DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento para o parâmetro especificado não for nulo.

As descrições anteriores são uma referência rápida ao que cada atributo faz. Cada seção a seguir descreve o comportamento e o significado mais detalhadamente.

A adição desses atributos dá ao compilador mais informações sobre as regras para sua API. Quando o código de chamada é compilado em um contexto ativado anulado, o compilador avisará os chamadores quando eles violarem essas regras. Esses atributos não permitem verificações adicionais na sua implementação.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Especificar pré-condições: `AllowNull` e`DisallowNull`

Considere uma propriedade de leitura/gravação que nunca retorna `null` porque tem um valor padrão razoável. Os chamadores passam `null` para o acessório definido ao defini-lo para esse valor padrão. Por exemplo, considere um sistema de mensagens que pede um nome de tela em uma sala de bate-papo. Se nenhum for fornecido, o sistema gera um nome aleatório:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Quando você compila o código anterior em um contexto alheio nulo, tudo está bem. Uma vez habilitado tipos `ScreenName` de referência anulados, a propriedade se torna uma referência não anulada. Isso é correto `get` para o acessório: ele nunca retorna `null`. Os chamadores não precisam verificar a `null`propriedade devolvida para . Mas agora definir `null` a propriedade para gera um aviso. Para continuar a suportar esse tipo de <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> código, você adiciona o atributo à propriedade, conforme mostrado no código a seguir:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Você pode precisar `using` adicionar <xref:System.Diagnostics.CodeAnalysis> uma diretiva para usar este e outros atributos discutidos neste artigo. O atributo é aplicado à `set` propriedade, não ao acessório. O `AllowNull` atributo especifica *pré-condições*e só se aplica a entradas. O `get` acessório tem um valor de retorno, mas sem argumentos de entrada. Portanto, o `AllowNull` atributo só `set` se aplica ao acessório.

O exemplo anterior demonstra o que `AllowNull` procurar ao adicionar o atributo em um argumento:

1. O contrato geral para essa variável é `null`que não deveria ser, então você quer um tipo de referência não anulado.
1. Existem cenários para a `null`variável de entrada ser , embora eles não sejam o uso mais comum.

Na maioria das vezes você precisará `in`deste `out`atributo para propriedades, ou , e `ref` argumentos. O `AllowNull` atributo é a melhor escolha quando uma variável é `null` tipicamente não nula, mas você precisa permitir como uma pré-condição.

Contraste isso com `DisallowNull`cenários para usar : Você usa este atributo para especificar que uma variável de entrada de um tipo de referência anulada não deve ser `null`. Considere um `null` imóvel onde está o valor padrão, mas os clientes só podem defini-lo como um valor não nulo. Considere o código a seguir:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

O código anterior é a melhor maneira `ReviewComment` de `null`expressar o seu design `null`que o poderia ser , mas não pode ser definido para . Uma vez que este código esteja ciente nulo, você <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>pode expressar este conceito mais claramente aos chamadores usando o :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Em um contexto nulo, o `ReviewComment` `get` acessório `null`poderia retornar o valor padrão de . O compilador avisa que deve ser verificado antes do acesso. Além disso, ele adverte os chamadores `null`que, embora possa ser, os `null`chamadores não devem explicitamente defini-lo para . O `DisallowNull` atributo também especifica uma *pré-condição,* não afeta o `get` acessório. Você deve optar `DisallowNull` por usar o atributo ao observar essas características sobre:

1. A variável `null` pode estar em cenários centrais, muitas vezes quando instanciado pela primeira vez.
1. A variável não deve ser `null`explicitamente definida para .

Essas situações são comuns em códigos que originalmente *eram nulos.* Pode ser que as propriedades do objeto sejam definidas em duas operações de inicialização distintas. Pode ser que algumas propriedades sejam definidas somente após algum trabalho assíncrono ter sido concluído.

Os `AllowNull` `DisallowNull` atributos permitem especificar que as pré-condições nas variáveis podem não corresponder às anotações anuladas nessas variáveis. Estes fornecem mais detalhes sobre as características de sua API. Essas informações adicionais ajudam os chamadores a usar sua API corretamente. Lembre-se de especificar pré-condições usando os seguintes atributos:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.
- [DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Especificar pós-condições: `MaybeNull` e`NotNull`

Suponha que você tenha um método com a seguinte assinatura:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Você provavelmente escreveu um método `null` como este para retornar quando o nome procurado não foi encontrado. O `null` registro indica que o registro não foi encontrado. Neste exemplo, você provavelmente mudaria o `Customer` `Customer?`tipo de retorno de . Declarar o valor de retorno como um tipo de referência anulado especifica claramente a intenção desta API.

Por razões cobertas por [definições genéricas e nulidade](#generic-definitions-and-nullability) essa técnica não funciona com métodos genéricos. Você pode ter um método genérico que segue um padrão semelhante:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Você não pode especificar que `T?`o valor de retorno é . O método `null` retorna quando o item procurado não é encontrado. Como você não pode `T?` declarar um tipo `MaybeNull` de retorno, você adiciona a anotação ao retorno do método:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

O código precedente informa aos chamadores que o contrato implica um tipo não anulado, mas o valor de devolução *pode* realmente ser nulo.  Use `MaybeNull` o atributo quando sua API deve ser um tipo não anulado, tipicamente `null` um parâmetro de tipo genérico, mas pode haver casos em que a Sua API seria devolvida.

Você também pode especificar que `out` `ref` um valor de retorno ou um argumento ou argumento não é nulo, mesmo que o tipo seja um tipo de referência anulado. Considere um método que garanta que uma matriz seja grande o suficiente para conter uma série de elementos. Se o argumento de entrada não tiver capacidade, a rotina alocaria uma nova matriz e copiaria todos os elementos existentes nele. Se o argumento `null`de entrada for, a rotina alocaria um novo armazenamento. Se há capacidade suficiente, a rotina não faz nada:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Você pode chamar essa rotina da seguinte forma:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Depois de habilitar tipos de referência nulos, você deseja garantir que o código anterior seja compilado sem avisos. Quando o método `storage` retorna, o argumento é garantido não ser nulo. No entanto, é aceitável `EnsureCapacity` ligar com uma referência nula. Você pode `storage` fazer um tipo de `NotNull` referência anulada e adicionar a pós-condição à declaração de parâmetro:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

O código anterior expressa o contrato existente muito claramente: `null` os chamadores podem passar uma variável com o valor, mas o valor de retorno é garantido para nunca ser nulo. O `NotNull` atributo é `ref` `out` mais útil `null` para e argumentos onde pode ser passado como argumento, mas esse argumento é garantido não ser nulo quando o método retorna.

Você especifica postcondições incondicionais usando os seguintes atributos:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Especificar pós-condições `NotNullWhen`condicionais: , `MaybeNullWhen`e`NotNullIfNotNull`

Você provavelmente está `string` familiarizado <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>com o método. Este método `true` retorna quando o argumento é nulo ou uma seqüência vazia. É uma forma de verificação nula: os chamadores não precisam verificar `false`nulo o argumento se o método retornar . Para tornar um método como este anulado, você definiria o argumento para `NotNullWhen` um tipo de referência anulado e adicionaria o atributo:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Isso informa o compilador de que qualquer `false` código onde o valor de devolução é não precisa ser verificado nulo. A adição do atributo informa a análise `IsNullOrEmpty` estática do compilador `false`que realiza a `null`verificação nula necessária: quando ele retorna, o argumento de entrada não é .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

O <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> método será anotado conforme mostrado acima para .NET Core 3.0. Você pode ter métodos semelhantes em sua base de código que verificam o estado dos objetos em busca de valores nulos. O compilador não reconhecerá métodos de verificação nulas personalizados, e você precisará adicionar as anotações você mesmo. Quando você adiciona o atributo, a análise estática do compilador sabe quando a variável testada foi verificada.

Outro uso para esses `Try*` atributos é o padrão. As condições `ref` e `out` variáveis são comunicadas através do valor de retorno. Considere este método mostrado anteriormente:

```csharp
bool TryGetMessage(string key, out string message)
```

O método anterior segue um idioma típico .NET: `message` o valor de retorno indica se foi definido como valor encontrado ou, se nenhuma mensagem for encontrada, para o valor padrão. Se o `true`método retornar, `message` o valor de não é nulo; caso contrário, o `message` método define como nulo.

Você pode comunicar esse `NotNullWhen` idioma usando o atributo. Quando você atualizar a assinatura para `message` tipos `string?` de referência anulados, faça a e adicione um atributo:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

No exemplo anterior, sabe-se que o valor de `message` não é nulo quando `TryGetMessage` retorna. `true` Você deve anotar métodos semelhantes em sua base de código `null`da mesma forma: os argumentos `true`podem ser , e são conhecidos por não serem nulos quando o método retorna .

Há um atributo final que você também pode precisar. Às vezes, o estado nulo de um valor de retorno depende do estado nulo de um ou mais argumentos de entrada. Esses métodos retornarão um valor não nulo sempre `null`que determinados argumentos de entrada não forem . Para anotar corretamente esses métodos, `NotNullIfNotNull` você usa o atributo. Considere o seguinte método:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Se `url` o argumento não é nulo, `null`a saída não é . Uma vez que as referências anuladas são habilitadas, essa assinatura funciona corretamente, desde que sua API nunca aceite uma entrada nula. No entanto, se a entrada pode ser nula, então o valor de devolução também pode ser nulo. Portanto, você pode alterar a assinatura para o seguinte código:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Isso também funciona, mas muitas vezes `null` forçará os chamadores a implementar verificações extras. O contrato é que o `null` valor de `url` retorno `null`seria apenas quando o argumento de entrada é . Para expressar esse contrato, você anotaria este método como mostrado no seguinte código:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

O valor de devolução e o argumento `?` foram ambos anotados com a indicação de que qualquer um poderia ser `null`. O atributo esclarece ainda que o valor de `url` retorno não `null`será nulo quando o argumento não for .

Você especifica postcondições condicionais usando esses atributos:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento de entrada para o parâmetro especificado não for nulo.

## <a name="generic-definitions-and-nullability"></a>Definições genéricas e nulidade

Comunicar corretamente o estado nulo de tipos genéricos e métodos genéricos requer cuidados especiais. Isso decorre do fato de que um tipo de valor anulado e um tipo de referência anulado são fundamentalmente diferentes. Um `int?` é um `Nullable<int>`sinônimo `string?` de `string` , enquanto é com um atributo adicionado pelo compilador. O resultado é que o compilador não `T?` pode gerar `T` código `class` correto `struct`para sem saber se é um ou um .

Isso não significa que você não pode usar um tipo de valor (tipo de valor ou tipo de referência) como o argumento de tipo para um tipo genérico fechado. Ambos `List<string?>` `List<int?>` são instanciações `List<T>`válidas de .

O que isso significa é que `T?` você não pode usar em uma classe genérica ou declaração de método sem restrições. Por exemplo, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> não será alterado `T?`para retornar . Você pode superar essa limitação adicionando ou a `struct` `class` restrição. Com qualquer uma dessas restrições, o compilador sabe `T` `T?`como gerar código para ambos e .

Você pode querer restringir os tipos usados para um argumento de tipo genérico para serem tipos não anulados. Você pode fazer isso `notnull` adicionando a restrição nesse argumento de tipo. Quando essa restrição é aplicada, o argumento do tipo não deve ser um tipo anulado.

## <a name="conclusions"></a>Conclusões

Adicionar tipos de referência anulados fornece um vocabulário inicial para descrever `null`suas expectativas de APIs para variáveis que poderiam ser . Os atributos adicionais fornecem um vocabulário mais rico para descrever o estado nulo das variáveis como pré-condições e pós-condições. Esses atributos descrevem mais claramente suas expectativas e fornecem uma melhor experiência para os desenvolvedores que usam suas APIs.

À medida que você atualiza bibliotecas para um contexto anulado, adicione esses atributos para orientar os usuários de suas APIs ao uso correto. Esses atributos ajudam a descrever completamente o estado nulo dos argumentos de entrada e valores de retorno:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.
- [DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento de entrada para o parâmetro especificado não for nulo.
