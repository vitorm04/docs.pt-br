---
title: Novidades no C# 6 – Guia do C#
description: Aprenda os novos recursos da versão 6 do C#
ms.date: 12/12/2018
ms.openlocfilehash: 1c8c8003f81d4c15f2abdc26dc15849d88582843
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654569"
---
# <a name="whats-new-in-c-6"></a>Novidades no C# 6

A versão 6.0 do C# tinha muitos recursos para melhorar a produtividade para desenvolvedores. O efeito geral desses recursos é que você escreve código mais conciso e também mais legível. A sintaxe contém menos cerimônia para várias práticas comuns. É mais fácil de ver a intenção do design com menos cerimônia. Aprenda bem esses recursos para ser mais produtivo e escrever um código mais legível. Você pode se concentrar mais nos recursos do que nos constructos da linguagem.

O restante deste artigo oferece uma visão geral de cada um desses recursos, com um link para explorá-los. Explore também os recursos em uma [exploração interativa sobre o C# 6](../tutorials/exploration/csharp-6.yml) na seção de tutoriais.

## <a name="read-only-auto-properties"></a>Propriedades automáticas somente leitura

As *Propriedades automáticas somente leitura* fornecem uma sintaxe mais concisa para criar tipos imutáveis. Você declara a propriedade automática apenas com um acessador get:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

As propriedades `FirstName` e `LastName` só podem ser definidas no corpo de um construtor:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

A tentativa de definir `LastName` em outro método gera um erro de compilação `CS0200`:

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Esse recurso habilita o suporte real à linguagem para criar tipos imutáveis e usar a sintaxe de propriedade automática mais concisa e conveniente.

Se a adição dessa sintaxe não remover um método acessível, essa será uma [alteração compatível com binário](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicializadores de propriedade automática

Os *Inicializadores de propriedade automática* permitem que você declare o valor inicial de uma propriedade automática como parte da declaração de propriedade.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

O membro `Grades` é inicializado no local em que é declarado. Isso facilita realizar a inicialização exatamente uma vez. A inicialização faz parte da declaração de propriedade, tornando mais fácil igualar a alocação de armazenamento com a interface pública para objetos `Student`.

## <a name="expression-bodied-function-members"></a>Membros de função aptos para expressão

Muitos membros que você escreve são instruções simples que poderiam ser expressões simples. Nesse caso, escreva um membro apto para expressão. Isso funciona para métodos e propriedades somente leitura. Por exemplo, uma substituição de `ToString()` é, geralmente, uma ótima candidata:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Você também pode usar essa sintaxe para propriedades somente leitura:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

A alteração de um membro existente para um membro de corpo da expressão é uma [alteração compatível com binário](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>usando estático

O aprimoramento *using static* permite que você importe os métodos estáticos de uma única classe. Você especifica a classe que está usando:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

O <xref:System.Math> não contém nenhum método de instância. Você também pode usar `using static` para importar os métodos estáticos de uma classe para uma classe que tem os métodos estáticos e de instância. Um dos exemplos mais úteis é <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Você precisa usar o nome de classe totalmente qualificado, `System.String` em uma instrução using estática.  Não é possível usar a palavra-chave `string` em vez disso.

Quando importados de uma instrução `static using`, os métodos de extensão apenas estão no escopo quando chamados usando a sintaxe de invocação de método de extensão. Eles não estão no escopo quando chamados como um método estático. Você verá isso com frequência em consultas LINQ. Você pode importar o padrão LINQ importando <xref:System.Linq.Enumerable> ou <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Normalmente, os métodos de extensão são chamados usando expressões de invocação de método de extensão. No caso raro em que você os chama usando a sintaxe de chamada de método estático, adicione o nome de classe para resolver a ambiguidade.

A diretiva `static using` também importa todos tipos aninhados. Você pode referenciar qualquer tipo aninhado sem qualificação.

## <a name="null-conditional-operators"></a>Operadores condicionais null

O *operador condicional nulo* torna as verificações de nulos muito mais fáceis e fluidas. Substitua o acesso do membro `.` por `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

No exemplo anterior, a variável `first` é atribuída como `null` se o objeto person é `null`. Caso contrário, ele receberá o valor da propriedade `FirstName`. Mais importante, o `?.` significa que essa linha de código não gera uma `NullReferenceException` quando a variável `person` é `null`. Em vez disso, ele causa um curto-circuito e retorna `null`. Você também pode usar um operador condicional nulo para acesso de matriz ou de indexador. Substitua `[]` por `?[]` na expressão do índice.

A seguinte expressão retorna um `string`, independentemente do valor de `person`. Geralmente esse constructo é usado com o operador de *união nulo* para atribuir valores padrão quando uma das propriedades é `null`. Quando a expressão causa um curto-circuito, o valor de `null` retornado é tipado para corresponder à expressão completa.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Você também pode usar o `?.` para invocar métodos condicionalmente. O uso mais comum das funções de membro com o operador condicional nulo é invocar delegados (ou manipuladores de eventos) com segurança que podem ser `null`.  Você chamará o método `Invoke` do delegado usando o operador `?.` para acessar o membro. Veja um exemplo no artigo [padrões de delegado](../delegates-patterns.md#handling-null-delegates).

As regras do operador `?.` garantem que o lado esquerdo do operador é avaliado apenas uma vez. Isso permite diversas expressões, incluindo o exemplo a seguir usando manipuladores de eventos:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Garantir que o lado esquerdo seja avaliado apenas uma vez também permite que você use qualquer expressão, inclusive chamadas de método, no lado esquerdo do `?.`

## <a name="string-interpolation"></a>Interpolação de cadeias de caracteres

Com o C# 6, o novo recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) permite que você insira as expressões em uma cadeia de caracteres. Basta preceder a cadeia de caracteres com `$` e usar expressões entre `{` e `}` em vez de ordinais:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Este exemplo usa propriedades para as expressões substituídas. Você pode usar qualquer expressão. Por exemplo, você pode calcular a média do aluno como parte da interpolação:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

A linha de código anterior formata o valor de `Grades.Average()` como um número de ponto flutuante com duas casas decimais.

Muitas vezes, pode ser necessário formatar a cadeia de caracteres produzida usando uma cultura específica. Aproveite o fato de que o objeto produzido por uma interpolação de cadeia de caracteres pode ser convertido implicitamente em <xref:System.FormattableString?displayProperty=nameWithType>. A instância de <xref:System.FormattableString> contém a cadeia de caracteres de formato composto e os resultados da avaliação das expressões antes da conversão delas em cadeias de caracteres. Use o método <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> para especificar a cultura ao formatar uma cadeia de caracteres. O exemplo a seguir produz uma cadeia de caracteres usando a cultura de-DE (alemão). (Por padrão, a cultura alemã usa o caractere ',' para o separador decimal e o caractere '.' como o separador de milhares.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Para familiarizar-se com a interpolação de cadeia de caracteres, confira o tutorial interativo [Interpolação de cadeia de caracteres em C#](../tutorials/intro-to-csharp/interpolated-strings.yml), o artigo [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) e o tutorial [Interpolação de cadeia de caracteres em C#](../tutorials/string-interpolation.md).

## <a name="exception-filters"></a>Filtros de exceção

Os *Filtros de Exceção* são cláusulas que determinam quando uma determinada cláusula catch deve ser aplicada. Se a expressão usada para um filtro de exceção é avaliada como `true`, a cláusula catch realiza seu processamento normal em uma exceção. Se a expressão for avaliada como `false`, a cláusula `catch` será ignorada. Um uso é examinar informações sobre uma exceção para determinar se uma cláusula `catch` pode processar a exceção:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>A expressão `nameof`

A expressão `nameof` é avaliada para o nome de um símbolo. É uma ótima maneira de fazer com que as ferramentas funcionem sempre que você precisar do nome de uma variável, de uma propriedade ou de um campo de membro. Um dos usos mais comuns para `nameof` é fornecer o nome de um símbolo que causou uma exceção:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Outro uso é com aplicativos baseados em XAML que implementam a interface `INotifyPropertyChanged`:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Await em blocos catch e finally

O C# 5 tinha várias limitações quanto ao local em que você poderia colocar expressões `await`. Com o C# 6, agora você pode usar `await` em expressões `catch` ou `finally`. Isso geralmente é usado com cenários de registro em log:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Os detalhes de implementação para adicionar o suporte ao `await` dentro das cláusulas `catch` e `finally` garante que o comportamento seja consistente com o comportamento do código síncrono. Quando o código que é executado em uma cláusula `catch` ou `finally` realiza o lançamento, a execução procura por uma cláusula `catch` adequada no próximo bloco. Se houver uma exceção atual, essa exceção será perdida. O mesmo acontece com expressões aguardadas em cláusulas `catch` e `finally`: um `catch` adequado é pesquisado e a exceção atual, se houver, será perdida.  

> [!NOTE]
> Esse comportamento é a razão pela qual recomenda-se escrever cláusulas `catch` e `finally` com cuidado, a fim de evitar introduzir novas exceções.

## <a name="initialize-associative-collections-using-indexers"></a>Inicializar coleções associativas usando indexadores

Os *inicializadores de índice* são um dos dois recursos que deixam os inicializadores de coleção mais consistentes com o uso do índice. Nas versões anteriores do C#, era possível usar *inicializadores de coleção* com coleções de estilo de sequência, incluindo <xref:System.Collections.Generic.Dictionary%602>, colocando os pares chave-valor entre chaves:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Você pode usá-los com coleções <xref:System.Collections.Generic.Dictionary%602> e outros tipos nos quais o método `Add` acessível aceite mais de um argumento. A nova sintaxe permite a atribuição usando um índice na coleção:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Esse recurso significa que os contêineres associativos podem ser inicializados usando uma sintaxe semelhante à que está em vigor para contêineres de sequência de várias versões.

## <a name="extension-add-methods-in-collection-initializers"></a>Métodos `Add` de extensão em inicializadores de coleção

Outro recurso que facilita a inicialização de coleção é a capacidade de usar um *método de extensão* para o método `Add`. Esse recurso foi adicionado para a paridade com o Visual Basic. O recurso é mais útil quando você tem uma classe de coleção personalizada que tem um método com um nome diferente para adicionar novos itens semanticamente.

## <a name="improved-overload-resolution"></a>Resolução de sobrecarga aprimorada

Esse último recurso provavelmente não será notado. Havia constructos nos quais a versão anterior do compilador do C# pode ter encontrado algumas chamadas de método que envolviam expressões lambda ambíguas. Considere este método:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Em versões anteriores do C#, haveria uma falha ao chamar esse método usando a sintaxe de grupo de método:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

O compilador anterior não conseguia distinguir corretamente entre `Task.Run(Action)` e `Task.Run(Func<Task>())`. Nas versões anteriores, você precisava usar uma expressão lambda como um argumento:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

O compilador do C# 6 determina corretamente que `Task.Run(Func<Task>())` é uma opção melhor.

### <a name="deterministic-compiler-output"></a>Saída do compilador determinístico

A opção `-deterministic` instrui o compilador a produzir um assembly de saída idêntico byte a byte para compilações sucessivas dos mesmos arquivos de origem.

Por padrão, cada compilação produz uma saída exclusiva em cada compilação. O compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios. Use essa opção se desejar comparar a saída byte a byte para garantir a consistência nos builds.

Para obter mais informações, confira o artigo [Opção do compilador -deterministic](../language-reference/compiler-options/deterministic-compiler-option.md).
