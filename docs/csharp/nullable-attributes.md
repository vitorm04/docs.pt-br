---
title: Atualizar APIs para tipos de referência anulados com atributos que definem expectativas de valores nulos
description: Aprenda a usar os atributos descritivos AllowNull, DisallowNull, MaybeNull, NotNull e muito mais para descrever completamente o estado nulo de suas APIs.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 7f78bd0224f93b4b9dcc2b9d4e3577db06497907
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389593"
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

As regras para suas APIs são provavelmente `TryGetValue` mais complicadas, como você viu com o cenário da API. Muitas de suas APIs têm regras mais complexas para `null`quando as variáveis podem ou não ser . Nestes casos, você usará atributos para expressar essas regras. Os atributos que descrevem a semântica de sua API são encontrados no artigo sobre [Atributos que impactam a análise anulada](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Definições genéricas e nulidade

Comunicar corretamente o estado nulo de tipos genéricos e métodos genéricos requer cuidados especiais. Isso decorre do fato de que um tipo de valor anulado e um tipo de referência anulado são fundamentalmente diferentes. Um `int?` é um `Nullable<int>`sinônimo `string?` de `string` , enquanto é com um atributo adicionado pelo compilador. O resultado é que o compilador não `T?` pode gerar `T` código `class` correto `struct`para sem saber se é um ou um .

Isso não significa que você não pode usar um tipo de valor (tipo de valor ou tipo de referência) como o argumento de tipo para um tipo genérico fechado. Ambos `List<string?>` `List<int?>` são instanciações `List<T>`válidas de .

O que isso significa é que `T?` você não pode usar em uma classe genérica ou declaração de método sem restrições. Por exemplo, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> não será alterado `T?`para retornar . Você pode superar essa limitação adicionando ou a `struct` `class` restrição. Com qualquer uma dessas restrições, o compilador sabe `T` `T?`como gerar código para ambos e .

Você pode querer restringir os tipos usados para um argumento de tipo genérico para serem tipos não anulados. Você pode fazer isso `notnull` adicionando a restrição nesse argumento de tipo. Quando essa restrição é aplicada, o argumento do tipo não deve ser um tipo anulado.
