---
title: "Como modificar o conteúdo de uma cadeia de caracteres – Guia de C#"
ms.date: 02/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a67cf24c0f6024d23bc1106943d3447620f18b1f
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-modify-string-contents-in-c"></a>Como modificar o conteúdo de uma cadeia de caracteres em C# #

Este artigo demonstra várias técnicas para produzir um `string` modificando um `string` existente. Todas as técnicas demonstradas retornam o resultado das modificações como um novo objeto `string`. Para demonstrar isso claramente, todos os exemplos armazenam o resultado em uma nova variável. Em seguida, você pode examinar o `string` original e o `string` resultante da modificação quando você executa cada exemplo.

Há várias técnicas demonstradas neste artigo. Você pode substituir o texto existente. Você pode procurar padrões e substituir o texto correspondente com outro texto. Você pode tratar uma cadeia de caracteres como uma sequência de caracteres. Você também pode usar métodos de conveniência que removem o espaço em branco. Você deve escolher as técnicas que mais se aproximam do seu cenário.

## <a name="replace-text"></a>Substituir texto

O código a seguir cria uma nova cadeia de caracteres, substituindo o texto existente por um substituto.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

O código anterior demonstra essa propriedade *immutable* de cadeias de caracteres. Você pode ver no exemplo anterior que a cadeia de caracteres original, `source`, não é modificada. O método <xref:System.String.Replace%2A?displayProperty=nameWithType> cria uma nova `string` contendo as modificações.

O método <xref:System.String.Replace%2A> pode substituir cadeias de caracteres ou caracteres únicos. Em ambos os casos, todas as ocorrências do texto pesquisado são substituídas.  O exemplo a seguir substitui todos os caracteres ' ' com '\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

A cadeia de caracteres de origem não é alterada e uma nova cadeia de caracteres é retornada com a substituição.

## <a name="trim-white-space"></a>Cortar espaço em branco

Você pode usar os métodos <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType> e <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> para remover espaços em branco à esquerda ou à direita.  O código a seguir mostra um exemplo de cada um desses casos. A cadeia de caracteres de origem não é alterada; esses métodos retornam uma nova cadeia de caracteres com o conteúdo modificado.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Remover texto

Você pode remover texto de uma cadeia de caracteres usando o método <xref:System.String.Remove%2A?displayProperty=nameWithType>. Esse método remove um número de caracteres começando em um índice específico. O exemplo a seguir mostra como usar <xref:System.String.IndexOf%2A?displayProperty=nameWithType> seguido por <xref:System.String.Remove%2A> para remover texto de uma cadeia de caracteres:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Substituir padrões correspondentes

Você pode usar [expressões regulares](../../standard/base-types/regular-expressions.md) para substituir padrões correspondentes de texto com um novo texto, possivelmente definido por um padrão. O exemplo a seguir usa a classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> para localizar um padrão em uma cadeia de caracteres de origem e substituí-lo pela capitalização correta. O método <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> usa uma função que fornece a lógica de substituição como um de seus argumentos. Neste exemplo, essa função `LocalReplaceMatchCase` é uma **função local** declarada dentro do método de exemplo. `LocalReplaceMatchCase` usa a classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> para criar a cadeia de caracteres de substituição com a capitalização correta.

Expressões regulares são mais úteis para localizar e substituir texto que segue um padrão, em vez de texto conhecido. Consulte [Como pesquisar cadeias de caracteres](search-strings.md) para obter mais detalhes. O padrão de pesquisa "the\s" procura a palavra "the" seguida por um caractere de espaço em branco. Essa parte do padrão garante que isso não corresponda a "there" na cadeia de caracteres de origem. Para obter mais informações sobre elementos de linguagem de expressão regular, consulte [Linguagem de expressão regular – referência rápida](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

O método <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> retorna uma cadeia de caracteres imutável com o conteúdo no objeto <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Modificar caracteres individuais

Você pode produzir uma matriz de caracteres de uma cadeia de caracteres, modificar o conteúdo da matriz e, em seguida, criar uma nova cadeia de caracteres com base no conteúdo modificado da matriz.

O exemplo a seguir mostra como substituir um conjunto de caracteres em uma cadeia de caracteres. Primeiro, ele usa o método <xref:System.String.ToCharArray?displayProperty=nameWithName> para criar uma matriz de caracteres. Ele usa o método <xref:System.String.IndexOf%2A> para localizar o índice inicial da palavra "fox". Os próximos três caracteres são substituídos por uma palavra diferente. Por fim, uma nova cadeia de caracteres é construída com a matriz de caracteres atualizada.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Modificações não seguras à cadeia de caracteres

Usando código **não seguro**, é possível modificar uma cadeia de caracteres "no local" depois que ela é criada. Código não seguro usa muitos dos recursos do .NET projetados para minimizar determinados tipos de bugs no código. Você precisa usar o código não seguro para modificar uma cadeia de caracteres em vigor porque a classe de cadeia de caracteres foi projetada como um tipo **immutable**. Depois de ela ser criada, seu valor não é alterado. O código não seguro contorna a essa propriedade, acessando e modificando a memória usada por um `string` sem usar métodos `string` normais.
O exemplo a seguir é fornecido para as raras situações em que você deseja modificar uma cadeia de caracteres no local usando código não seguro. O exemplo mostra como usar a palavra-chave `fixed`. A palavra-chave `fixed` impede que o GC (coletor de lixo) mova o objeto de cadeia de caracteres na memória enquanto o código acessa a memória usando o ponteiro não seguro. Ele também demonstra um possível efeito colateral das operações não seguras em cadeias de caracteres, que resultam da forma com que o compilador C# armazena (interna) as cadeias de caracteres internamente. Em geral, você não deve usar essa técnica, a menos que seja absolutamente necessário. É possível aprender mais sobre [não seguro](../language-reference/keywords/unsafe.md) e [fixo](../language-reference/keywords/fixed-statement.md) nos artigos. A referência à API para <xref:System.String.Intern%2A> inclui informações sobre centralização de cadeia de caracteres.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Você pode experimentar estes exemplos examinando o código em nosso [repositório GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Ou então, você pode baixar os exemplos [como um arquivo zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET Framework](../../standard/base-types/regular-expressions.md)  
 [Linguagem de expressão regular – referência rápida](../../standard/base-types/regular-expression-language-quick-reference.md)  