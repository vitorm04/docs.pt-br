---
title: Tipos de referência nulamente - referência C#
description: Saiba mais sobre os tipos de referência nula e como usá-los
ms.date: 04/06/2020
ms.openlocfilehash: cbc7397ac76b43b79a4168f4c61fe2c631b4a46b
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888312"
---
# <a name="nullable-reference-types-c-reference"></a>Tipos de referência anulados (referência C#)

> [!NOTE]
> Este artigo abrange tipos de referência anulados. Você também pode declarar [tipos de valor anulados](nullable-value-types.md).

Os tipos de referência anulados estão disponíveis a partir de C# 8.0, em código que optou por um *contexto de reconhecimento anulado*. Os tipos de referência nulidade, os avisos de análise estática nula e o [operador que perdoa nulos](../operators/null-forgiving.md) são recursos opcionais de linguagem. Todos são desligados por padrão. Um *contexto anulado* é controlado no nível do projeto usando configurações de compilação ou em código usando pragmas.

 Em um contexto de consciência nula:

- Uma variável de `T` um tipo de referência deve ser inicializada com não nulidade, e nunca pode ser atribuída a um valor que possa ser `null`.
- Uma variável de `T?` um tipo de `null` referência `null`pode ser inicializada com `null` ou atribuída, mas é necessário verificar-se com antes de fazer referência.
- Uma `m` variável `T?` de tipo é considerada não nula quando você aplica `m!`o operador de perdão nulo, como em .

As distinções entre um tipo `T` de referência não `T?` anulado e um tipo de referência nula são aplicadas pela interpretação do compilador das regras anteriores. Uma variável `T` de tipo e `T?` uma variável de tipo são representadas pelo mesmo tipo .NET. O exemplo a seguir declara uma seqüência de string não anulada e uma seqüência de seqüência sem nulidade e, em seguida, usa o operador que perdoa nulo para atribuir um valor a uma seqüência não anulada:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

As variáveis `notNull` `nullable` e ambas são <xref:System.String> representadas pelo tipo. Como os tipos não anulados e anulados são armazenados como o mesmo tipo, existem vários locais onde o uso de um tipo de referência anulado não é permitido. Em geral, um tipo de referência anulado não pode ser usado como uma classe base ou interface implementada. Um tipo de referência anulada não pode ser usado em qualquer criação de objeto ou expressão de teste de tipo. Um tipo de referência anulado não pode ser o tipo de expressão de acesso de membro. Os exemplos a seguir mostram essas construções:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Referências anuladas e análise estática

Os exemplos na seção anterior ilustram a natureza dos tipos de referência anulados. Os tipos de referência anulados não são novos tipos de classe, mas sim anotações sobre os tipos de referência existentes. O compilador usa essas anotações para ajudá-lo a encontrar possíveis erros de referência nulos em seu código. Não há diferença de tempo de execução entre um tipo de referência não anulado e um tipo de referência anulado. O compilador não adiciona nenhuma verificação de tempo de execução para tipos de referência não anulados. Os benefícios estão na análise de tempo de compilação. O compilador gera avisos que ajudam você a encontrar e corrigir possíveis erros nulos em seu código. Você declara sua intenção, e o compilador avisa quando seu código viola essa intenção.

Em um contexto habilitado nulo, o compilador realiza análisees estáticas em variáveis de qualquer tipo de referência, tanto anuladas quanto não anuladas. O compilador rastreia o estado nulo de cada variável de referência como *não nulo* ou *talvez nulo*. O estado padrão de uma referência não anulada não é *nulo*. O estado padrão de uma referência anulada talvez seja *nulo.*

Os tipos de referência não anulados devem ser sempre seguros para desfazer porque seu estado nulo não é *nulo*. Para aplicar essa regra, o compilador emite avisos se um tipo de referência não anulado não for inicializado a um valor não nulo. As variáveis locais devem ser atribuídas onde são declaradas. Cada construtor deve atribuir cada campo, seja em seu corpo, um chamado construtor, ou usando uma inicializadora de campo. O compilador emite avisos se uma referência não anulada for atribuída a uma referência cujo estado talvez seja *nulo*. No entanto, como uma referência não anulada não é *nula,* nenhum aviso é emitido quando essas variáveis são desreferenciadas.

Os tipos de referência anulados podem `null`ser inicializados ou atribuídos a . Portanto, a análise estática deve determinar que uma variável não é *nula* antes de ser desreferenciada. Se uma referência anulada for determinada como *talvez nula,* ela não pode ser atribuída a uma variável de referência não anulada. A classe a seguir mostra exemplos desses avisos:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

O trecho a seguir mostra onde o compilador emite avisos ao usar esta classe:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Os exemplos anteriores demonstram a análise estática do compilador para determinar o estado nulo das variáveis de referência. O compilador aplica regras de idioma para verificações e atribuições nulas para informar sua análise.  O compilador não pode fazer suposições sobre a semântica de métodos ou propriedades. Se você chamar métodos que realizam verificações nulas, o compilador não pode saber que esses métodos afetam o estado nulo de uma variável. Há uma série de atributos que você pode adicionar às suas APIs para informar o compilador sobre a semântica de argumentos e valores de devolução. Esses atributos foram aplicados a muitas APIs comuns nas bibliotecas .NET Core. Por exemplo, <xref:System.String.IsNullOrEmpty%2A> foi atualizado, e o compilador interpreta corretamente esse método como uma verificação nula. Para obter mais informações sobre os atributos aplicáveis à análise estática do estado nulo, consulte o artigo sobre [atributos anulados](../../nullable-attributes.md).

## <a name="setting-the-nullable-context"></a>Definindo o contexto nulo

Há duas maneiras de controlar o contexto nulo. No nível do projeto, `<Nullable>enable</Nullable>` você pode adicionar a configuração do projeto. Em um único arquivo de origem `#nullable enable` C#, você pode adicionar o pragma para ativar o contexto anulado. Veja o artigo sobre [a definição de uma estratégia anulada](../../nullable-attributes.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte as seguintes propostas para a especificação do [idioma C#:](~/_csharplang/spec/introduction.md)

- [Tipos de referência anuláveis](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Especificação de tipos de referência anulados de rascunho](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de valor anuláveis](nullable-value-types.md)
