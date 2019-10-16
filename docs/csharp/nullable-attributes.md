---
title: Atualizar APIs com atributos para definir expectativas nulas
description: Este artigo explica as motivações e técnicas para adicionar atributos descritivos para descrever o estado nulo de argumentos e retornar valores de APIs
ms.date: 07/31/2019
ms.openlocfilehash: c51ec81f77bb1d31168848d8d51e68a08965d42c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319066"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Atualizar bibliotecas para usar tipos de referência anuláveis e comunicar regras anuláveis a chamadores

A adição de [tipos de referência anuláveis](nullable-references.md) significa que você pode declarar se um valor `null` é ou não permitido ou esperado para cada variável. Isso fornece uma ótima experiência à medida que você escreve o código. Você receberá avisos se uma variável não anulável puder ser definida como `null`. Você receberá avisos se uma variável anulável não for marcada como nula antes de você desreferenciá-la. Atualizar suas bibliotecas pode levar tempo, mas os benefícios valem a pena. Quanto mais informações você fornecer ao compilador sobre *quando* um valor `null` é permitido ou proibido, os melhores avisos que os usuários da sua API obterão. Vamos começar com um exemplo familiar. Imagine que sua biblioteca tenha a seguinte API para recuperar uma cadeia de caracteres de recurso:

```csharp
bool TryGetMessage(string key, out string message)
```

O exemplo anterior segue o conhecido padrão `Try*` no .NET. Há dois argumentos de referência para essa API: o `key` e o parâmetro `message`. Essa API tem as seguintes regras relacionadas à nulidade desses argumentos:

- Os chamadores não devem passar `null` como o argumento para `key`.
- Os chamadores podem passar uma variável cujo valor é `null` como o argumento para `message`.
- Se o método `TryGetMessage` retornar `true`, o valor de `message` não será nulo. Se o valor de retorno for `false,`, o valor de `message` (e seu estado nulo) será NULL.

A regra para `key` pode ser completamente expressa pelo tipo de variável: `key` deve ser um tipo de referência não anulável. O parâmetro `message` é mais complexo. Ele permite `null` como o argumento, mas garante que, em caso de sucesso, que o argumento `out` não seja nulo. Para esses cenários, você precisa de um vocabulário mais rico para descrever as expectativas.

Atualizar sua biblioteca para referências anuláveis requer mais do que o de incêndio `?` em algumas das variáveis e nomes de tipo. O exemplo anterior mostra que você precisa examinar suas APIs e considerar suas expectativas para cada argumento de entrada. Considere as garantias para o valor de retorno e quaisquer argumentos `out` ou `ref` no retorno do método. Em seguida, comunique essas regras ao compilador, e o compilador fornecerá avisos quando os chamadores não obedecem a essas regras.

Esse trabalho leva tempo. Vamos começar com as estratégias para tornar sua biblioteca ou reconhecimento anulável de aplicativo, ao mesmo tempo em que equilibra outros requisitos e resultados finais. Você verá como balancear o desenvolvimento contínuo habilitando tipos de referência anuláveis. Você aprenderá os desafios para definições de tipo genérico. Você aprenderá a aplicar atributos para descrever as condições anteriores e posteriores em APIs individuais.

## <a name="choose-a-nullable-strategy"></a>Escolher uma estratégia anulável

A primeira opção é se os tipos de referência anuláveis devem estar ativados ou desativados por padrão. Você tem duas estratégias:

- Habilite tipos de referência anuláveis para o projeto inteiro e desabilite-o no código que não está pronto.
- Só habilite tipos de referência anuláveis para o código anotado para tipos de referência anuláveis.

A primeira estratégia funciona melhor quando você está adicionando outros recursos à biblioteca ao atualizá-los para tipos de referência anuláveis. Todo o novo desenvolvimento tem reconhecimento anulável. À medida que você atualiza o código existente, você habilita os tipos de referência anuláveis nessas classes.

Seguindo essa primeira estratégia, faça o seguinte:

1. Habilite tipos anuláveis para todo o projeto adicionando o elemento `<Nullable>enable</Nullable>` aos seus arquivos *csproj* . 
1. Adicione o `#nullable disable` pragma a cada arquivo de origem em seu projeto. 
1. Conforme você trabalha em cada arquivo, remova o pragma e resolva os avisos.

Essa primeira estratégia tem mais trabalho antecipado para adicionar o pragma a cada arquivo. A vantagem é que todos os novos arquivos de código adicionados ao projeto serão habilitados para permitir valor nulo. Qualquer trabalho novo terá reconhecimento de Nullable; somente o código existente deve ser atualizado.

A segunda estratégia funciona melhor se a biblioteca costuma ser estável e o foco principal do desenvolvimento é adotar tipos de referência anuláveis. Você ativa os tipos de referência anuláveis ao anotar APIs. Quando tiver terminado, habilite os tipos de referência anuláveis para o projeto inteiro.

Seguindo essa segunda estratégia, você faz o seguinte:

1. Adicione o `#nullable enable` pragma ao arquivo em que você deseja tornar o reconhecimento anulável.
1. Resolva os avisos.
1. Continue essas duas primeiras etapas até que você tenha feito o reconhecimento de toda a biblioteca.
1. Habilite tipos anuláveis para todo o projeto adicionando o elemento `<Nullable>enable</Nullable>` aos seus arquivos *csproj* . 
1. Remova os pragmas `#nullable enable`, pois eles não são mais necessários.

Essa segunda estratégia tem menos trabalho de antecedência. A desvantagem é que a primeira tarefa quando você cria um novo arquivo é adicionar o pragma e torná-lo indesejado de forma anulável. Se algum desenvolvedor da sua equipe esquecer, esse novo código estará no registro posterior do trabalho para tornar todos os incompatíveis com o código anulável.

Qual dessas estratégias você escolhe depende de quanto o desenvolvimento ativo está ocorrendo em seu projeto. Quanto mais maduro e estável for seu projeto, melhor a segunda estratégia. Quanto mais recursos estiverem sendo desenvolvidos, melhor será a primeira estratégia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Os avisos que permitem valor nulo apresentam alterações significativas?

Antes de habilitar tipos de referência anuláveis, as variáveis são consideradas *alheios anuláveis*. Depois de habilitar tipos de referência anuláveis, todas essas variáveis são *não anuláveis*. O compilador emitirá avisos se essas variáveis não forem inicializadas para valores não nulos.

Outra provável fonte de avisos é retornar valores quando o valor não tiver sido inicializado.

A primeira etapa para abordar os avisos do compilador é usar as anotações `?` nos tipos de parâmetro e de retorno para indicar quando argumentos ou valores de retorno podem ser nulos. Quando variáveis de referência não devem ser nulas, a declaração original está correta. Como você faz isso, seu objetivo não é apenas corrigir avisos. A meta mais importante é fazer com que o compilador entenda sua intenção por possíveis valores nulos. Ao examinar os avisos, você chegará à sua próxima decisão principal para sua biblioteca. Deseja considerar a modificação de assinaturas de API para comunicar mais claramente sua intenção de design? Uma assinatura de API melhor para o método `TryGetMessage` examinado anteriormente poderia ser:

```csharp
string? TryGetMessage(string key);
```

O valor de retorno indica êxito ou falha e transporta o valor se o valor foi encontrado. Em muitos casos, a alteração de assinaturas de API pode melhorar a forma como elas comunicam valores nulos.

No entanto, para bibliotecas públicas ou bibliotecas com grandes bases de usuários, você pode preferir não introduzir nenhuma alteração de assinatura de API. Para esses casos e outros padrões comuns, você pode aplicar atributos para definir de forma mais clara quando um argumento ou valor de retorno pode ser `null`. Se você considerar ou não a alteração da superfície de sua API, provavelmente descobrirá que as anotações de tipo sozinhas não são suficientes para descrever valores `null` para argumentos ou valores de retorno. Nessas instâncias, você pode aplicar atributos para descrever mais claramente uma API. 

## <a name="attributes-extend-type-annotations"></a>Atributos estendem anotações de tipo

Vários atributos foram adicionados para expressar informações adicionais sobre o estado nulo de variáveis. Todo o código que você C# escreveu antes de 8 apresentou tipos de referência anuláveis era *nulo alheios*. Isso significa que qualquer variável de tipo de referência pode ser nula, mas verificações nulas não são necessárias. Depois que o código estiver com *reconhecimento nulo*, essas regras serão alteradas. Os tipos de referência nunca devem ser o valor `null`, e os tipos de referência anuláveis devem ser verificados em relação a `null` antes de serem desreferenciados.

As regras para suas APIs são provavelmente mais complicadas, como vimos com o cenário de API `TryGetValue`. Muitas de suas APIs têm regras mais complexas para quando as variáveis podem ou não ser `null`. Nesses casos, você usará um dos seguintes atributos para expressar essas regras:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.
- Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o valor `bool` especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o valor `bool` especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento do parâmetro especificado não for nulo.

As descrições anteriores são uma referência rápida para o que cada atributo faz. Cada seção a seguir descreve o comportamento e significa mais detalhadamente.

A adição desses atributos fornece ao compilador mais informações sobre as regras para sua API. Quando o código de chamada é compilado em um contexto habilitado para valor nulo, o compilador avisa aos chamadores quando eles violam essas regras. Esses atributos não habilitam verificações adicionais em sua implementação.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Especificar pré-condições: `AllowNull` e `DisallowNull`

Considere uma propriedade de leitura/gravação que nunca retorna `null` porque ela tem um valor padrão razoável. Os chamadores passam `null` para o acessador set ao configurá-lo para esse valor padrão. Por exemplo, considere um sistema de mensagens que solicita um nome de tela em uma sala de chat. Se nenhum for fornecido, o sistema gerará um nome aleatório:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Quando você compila o código anterior em um contexto alheios anulável, tudo está bem. Depois de habilitar os tipos de referência anuláveis, a propriedade `ScreenName` se torna uma referência não anulável. Isso está correto para o acessador `get`: ele nunca retorna `null`. Os chamadores não precisam verificar a propriedade retornada para `null`. Mas agora definir a propriedade como `null` gera um aviso. Para continuar a dar suporte a esse tipo de código, adicione o atributo <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> à propriedade, conforme mostrado no código a seguir: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Talvez seja necessário adicionar uma diretiva `using` para <xref:System.Diagnostics.CodeAnalysis> para usar esse e outros atributos discutidos neste artigo. O atributo é aplicado à propriedade, não ao acessador `set`. O atributo `AllowNull` especifica *pré-condições*e só se aplica a entradas. O acessador `get` tem um valor de retorno, mas nenhum argumento de entrada. Portanto, o atributo `AllowNull` só se aplica ao acessador `set`.

O exemplo anterior demonstra o que procurar ao adicionar o atributo `AllowNull` em um argumento:

1. O contrato geral para essa variável é que ele não deve ser `null`, portanto você deseja um tipo de referência não anulável.
1. Há cenários para a variável de entrada ser `null`, embora não sejam o uso mais comum.

Geralmente, você precisará desse atributo para propriedades, ou `in`, `out` e argumentos `ref`. O atributo `AllowNull` é a melhor opção quando uma variável normalmente é não nula, mas você precisa permitir `null` como uma pré-condição.

Compare com cenários para usar `DisallowNull`: você usa esse atributo para especificar que uma variável de entrada de um tipo anulável não deve ser `null`. Considere uma propriedade em que `null` é o valor padrão, mas os clientes só podem defini-lo como um valor não nulo. Considere o código a seguir:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

O código anterior é a melhor maneira de expressar o design que o `ReviewComment` poderia ser `null`, mas não pode ser definido como `null`. Depois que esse código é ciente de forma anulável, você pode expressar esse conceito mais claramente para os chamadores usando o <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Em um contexto anulável, o acessador `ReviewComment` `get` pode retornar o valor padrão de `null`. O compilador avisa que ele deve ser verificado antes do acesso. Além disso, ele avisa aos chamadores que, embora possam ser `null`, os chamadores não devem defini-lo explicitamente como `null`. O atributo `DisallowNull` também especifica uma *pré-condição*, ele não afeta o acessador `get`. Você deve optar por usar o atributo `DisallowNull` ao observar essas características sobre:

1. A variável pode ser `null` em cenários principais, geralmente quando a primeira instância é criada.
1. A variável não deve ser definida explicitamente como `null`.

Essas situações são comuns no código que era originalmente *nulo alheios*. Pode ser que as propriedades do objeto sejam definidas em duas operações de inicialização distintas. Pode ser que algumas propriedades sejam definidas somente após a conclusão de algum trabalho assíncrono.

Os atributos `AllowNull` e `DisallowNull` permitem que você especifique que as pré-condições nas variáveis podem não corresponder às anotações anuláveis nessas variáveis. Eles fornecem mais detalhes sobre as características de sua API. Essas informações adicionais ajudam os chamadores a usar sua API corretamente. Lembre-se de especificar as pré-condições usando os seguintes atributos:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Especificar pós-condições: `MaybeNull` e `NotNull`

Suponha que você tenha um método com a seguinte assinatura:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Você provavelmente escreveu um método como este para retornar `null` quando o nome procurado não foi encontrado. O `null` indica claramente que o registro não foi encontrado. Neste exemplo, você provavelmente alteraria o tipo de retorno de `Customer` para `Customer?`. Declarar o valor de retorno como um tipo de referência anulável especifica claramente a intenção dessa API. 

Por motivos abordados em [definições genéricas e nulidade](#generic-definitions-and-nullability) que a técnica não funciona com métodos genéricos. Você pode ter um método genérico que segue um padrão semelhante:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Você não pode especificar que o valor de retorno é `T?`. O método retorna `null` quando o item procurado não é encontrado. Como não é possível declarar um tipo de retorno `T?`, você adiciona a anotação `MaybeNull` ao retorno do método:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

O código anterior informa aos chamadores que o contrato implica em um tipo não anulável, mas o valor de retorno *pode* ser, na verdade, nulo.  Use o atributo `MaybeNull` quando sua API deve ser um tipo não anulável, normalmente um parâmetro de tipo genérico, mas pode haver instâncias em que `null` seriam retornadas.

Você também pode especificar que um valor de retorno ou um argumento `out` ou `ref` não seja nulo, embora o tipo seja um tipo anulável. Considere um método que garanta que uma matriz seja grande o suficiente para conter vários elementos. Se o argumento de entrada não tiver capacidade, a rotina alocaria uma nova matriz e copiaria todos os elementos existentes nela. Se o argumento de entrada for `null`, a rotina alocaria novo armazenamento. Se houver capacidade suficiente, a rotina não fará nada:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Você pode chamar essa rotina da seguinte maneira:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Depois de habilitar tipos de referência NULL, você deseja garantir que o código anterior seja compilado sem avisos. Quando o método retorna, o argumento `storage` é garantido como não nulo. No entanto, é aceitável chamar `EnsureCapacity` com uma referência nula. Você pode tornar `storage` um tipo de referência anulável e adicionar o `NotNull` post-Condition à declaração de parâmetro:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

O código anterior expressa o contrato existente muito claramente: os chamadores podem passar uma variável com o valor `null`, mas é garantido que o valor de retorno nunca seja nulo. O atributo `NotNull` é mais útil para argumentos `ref` e `out` em que `null` pode ser passado como um argumento, mas esse argumento é garantido como não nulo quando o método retorna.

Você especifica condições de erro incondicionais usando os seguintes atributos:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.
- Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Especificar pós-condições condicionais: `NotNullWhen`, `MaybeNullWhen` e `NotNullIfNotNull`

Você provavelmente está familiarizado com o método `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Esse método retorna `true` quando o argumento é nulo ou uma cadeia de caracteres vazia. É uma forma de verificação nula: os chamadores não precisam ser nulos. Verifique o argumento se o método retornar `false`. Para tornar um método como esse reconhecimento anulável, você definiria o argumento como um tipo anulável e adicionaria o atributo `NotNullWhen`:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Isso informa ao compilador que qualquer código em que o valor de retorno é `false` não precisa ser marcado como nulo. A adição do atributo informa a análise estática do compilador que `IsNullOrEmpty` executa a verificação nula necessária: quando retorna `false`, o argumento de entrada não é `null`.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

O método <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> será anotado conforme mostrado acima para o .NET Core 3,0. Você pode ter métodos semelhantes em sua base de código que verificam o estado dos objetos em busca de valores nulos. O compilador não reconhecerá os métodos de verificação NULL personalizados e você precisará adicionar as anotações por conta própria. Quando você adiciona o atributo, a análise estática do compilador sabe quando a variável testada foi marcada como nula.

Outro uso para esses atributos é o padrão `Try*`. As condições para as variáveis `ref` e `out` são comunicadas por meio do valor de retorno. Considere este método mostrado anteriormente:

```csharp
bool TryGetMessage(string key, out string message)
```

O método anterior segue um idioma .NET típico: o valor de retorno indica se `message` foi definido como o valor encontrado ou, se nenhuma mensagem for encontrada, para o valor padrão. Se o método retornar `true`, o valor de `message` não será nulo; caso contrário, o método define `message` como NULL.

Você pode comunicar esse idioma usando o atributo `NotNullWhen`. Quando você atualiza a assinatura para tipos de referência anuláveis, faça `message` a `string?` e adicione um atributo:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

No exemplo anterior, o valor de `message` é conhecido como não nulo quando `TryGetMessage` retorna `true`. Você deve anotar métodos semelhantes em sua base de código da mesma maneira: os argumentos podem ser `null` e não devem ser nulos quando o método retornar `true`.

Há um atributo final que você também pode precisar. Às vezes, o estado nulo de um valor de retorno depende do estado nulo de um ou mais argumentos de entrada. Esses métodos retornarão um valor não nulo sempre que determinados argumentos de entrada não forem `null`. Para anotar corretamente esses métodos, use o atributo `NotNullIfNotNull`. Considere o seguinte método:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Se o argumento `url` não for nulo, a saída não será `null`. Depois que as referências anuláveis estiverem habilitadas, essa assinatura funcionará corretamente, desde que sua API nunca aceite uma entrada nula. No entanto, se a entrada puder ser nula, o valor de retorno também poderá ser nulo. Portanto, você pode alterar a assinatura para o código a seguir:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Isso também funciona, mas, muitas vezes, forçará os chamadores a implementarem verificações `null` adicionais. O contrato é que o valor de retorno seria `null` somente quando o argumento de entrada `url` é `null`. Para expressar esse contrato, você anotaria esse método, conforme mostrado no código a seguir:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

O valor de retorno e o argumento foram anotados com o `?`, indicando que pode ser `null`. O atributo esclarece ainda mais que o valor de retorno não será nulo quando o argumento `url` não for `null`.

Você especifica condições recondicionais usando estes atributos:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o valor `bool` especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o valor `bool` especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento de entrada para o parâmetro especificado não for nulo.

## <a name="generic-definitions-and-nullability"></a>Definições genéricas e nulidade

Comunicar corretamente o estado nulo de tipos genéricos e métodos genéricos requer um cuidado especial. Isso deriva do fato de que um tipo de valor anulável e um tipo de referência anulável são fundamentalmente diferentes. Um `int?` é um sinônimo para `Nullable<int>`, enquanto `string?` é `string` com um atributo adicionado pelo compilador. O resultado é que o compilador não pode gerar o código correto para `T?` sem saber se `T` é um `class` ou um `struct`. 

Isso não significa que você não pode usar um tipo anulável (tipo de valor ou tipo de referência) como o argumento de tipo para um tipo genérico fechado. Tanto `List<string?>` quanto `List<int?>` são instanciações válidas de `List<T>`. 

O que significa é que você não pode usar `T?` em uma classe genérica ou declaração de método sem restrições. Por exemplo, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> não será alterado para retornar `T?`. Você pode superar essa limitação adicionando a restrição `struct` ou `class`. Com qualquer uma dessas restrições, o compilador sabe como gerar código para `T` e `T?`.

Talvez você queira restringir os tipos usados para que um argumento de tipo genérico seja de tipos não anuláveis. Você pode fazer isso adicionando a restrição `notnull` nesse argumento de tipo. Quando essa restrição é aplicada, o argumento de tipo não deve ser um tipo anulável.

## <a name="conclusions"></a>Conclusões

A adição de tipos de referência anuláveis fornece um vocabulário inicial para descrever suas expectativas de APIs para variáveis que podem ser `null`. Os atributos adicionais fornecem um vocabulário mais rico para descrever o estado nulo de variáveis como pré-condições e condições. Esses atributos descrevem mais claramente suas expectativas e fornecem uma experiência melhor para os desenvolvedores que usam suas APIs.

Conforme você atualiza as bibliotecas para um contexto anulável, adicione esses atributos para orientar os usuários de suas APIs para o uso correto. Esses atributos ajudam você a descrever totalmente o estado nulo dos argumentos de entrada e valores de retorno:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.
- Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o valor `bool` especificado.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o valor `bool` especificado.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento de entrada para o parâmetro especificado não for nulo.
