---
title: Instrução using – Referência de C#
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989175"
---
# <a name="using-statement-c-reference"></a>Instrução using (Referência de C#)

Fornece uma sintaxe conveniente que garante o uso correto de objetos <xref:System.IDisposable>. A partir de C# `using` 8.0, a <xref:System.IAsyncDisposable> declaração garante o uso correto dos objetos.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar a instrução `using`.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

Começando com C# 8.0, você pode usar a `using` seguinte sintaxe alternativa para a declaração que não requer aparelhos:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Comentários

<xref:System.IO.File> e <xref:System.Drawing.Font> são exemplos de tipos gerenciados que acessam recursos não gerenciados (nesse caso, identificadores de arquivo de caso e contextos de dispositivo). Há muitos outros tipos de recursos não gerenciados e tipos de biblioteca de classes que os encapsula. Todos esses tipos <xref:System.IDisposable> devem implementar <xref:System.IAsyncDisposable> a interface ou a interface.

Quando o tempo de vida de um objeto `IDisposable` é limitado a um único método, você deve declará-lo e instanciá-lo na instrução `using`. A instrução `using` chama o método <xref:System.IDisposable.Dispose%2A> no objeto da forma correta e (quando você o usa como mostrado anteriormente) ele também faz com que o objeto em si saia do escopo assim que <xref:System.IDisposable.Dispose%2A> é chamado. Dentro `using` do bloco, o objeto é somente leitura e não pode ser modificado ou reatribuído. Se o objeto `IAsyncDisposable` for `IDisposable`implementado `using` em <xref:System.IAsyncDisposable.DisposeAsync%2A> vez `awaits` de <xref:System.Threading.Tasks.Task>, a declaração chamará o e o devolvido .

A `using` declaração <xref:System.IDisposable.Dispose%2A> garante <xref:System.IAsyncDisposable.DisposeAsync%2A>que (ou ) seja chamado `using` mesmo se ocorrer uma exceção dentro do bloco. Você pode obter o mesmo resultado `try` colocando o <xref:System.IDisposable.Dispose%2A> objeto <xref:System.IAsyncDisposable.DisposeAsync%2A> dentro `finally` de um bloco e, `using` em seguida, chamando (ou em um bloco; na verdade, é assim que a declaração é traduzida pelo compilador. O exemplo de código anterior se expande para o seguinte código em tempo de compilação (observe as chaves extras para criar o escopo limitado para o objeto):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

A nova `using` sintaxe de declaração se traduz em código semelhante. O `try` bloco é aberto onde a variável é declarada. O `finally` bloco é adicionado no fechamento do bloco de fechamento, normalmente no final de um método.

Para obter mais `try` - `finally` informações sobre a declaração, consulte o artigo [try-finally.](try-finally.md)

Várias instâncias de um tipo `using` podem ser declaradas em uma única declaração, como mostrado no exemplo a seguir. Observe que você não pode usar variáveis`var`digitadas implicitamente ( ) quando você declara várias variáveis em uma única declaração:

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Você também pode combinar várias declarações do mesmo tipo usando a nova sintaxe introduzida com C# 8, como mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Você pode instanciar o objeto de `using` recurso e, em seguida, passar a variável para a declaração, mas esta não é uma prática recomendada. Nesse caso, após o controle sair do bloco `using`, o objeto permanecerá no escopo, mas provavelmente não terá acesso a seus recursos não gerenciados. Em outras palavras, ele não é mais totalmente inicializado. Se você tentar usar o objeto fora do bloco `using`, corre o risco de causar o lançamento de uma exceção. Por essa razão, é melhor instanciar `using` o objeto na `using` declaração e limitar seu escopo ao bloco.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Para obter mais informações sobre como descartar objetos `IDisposable`, veja [Usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte [A instrução using](~/_csharplang/spec/statements.md#the-using-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Palavras-chave](index.md)
- [Diretiva de uso](using-directive.md)
- [Coleta de lixo](../../../standard/garbage-collection/index.md)
- [Usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interface IDisposable](xref:System.IDisposable)
- [usando a declaração em C# 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
