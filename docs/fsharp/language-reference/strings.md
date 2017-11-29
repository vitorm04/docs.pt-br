---
title: Cadeias de caracteres (F#)
description: "Saiba como o tipo 'string' F # representa texto imutável como uma sequência de caracteres Unicode."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a>Cadeias de caracteres

> [!NOTE]
Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O `string` tipo representa texto imutável como uma sequência de caracteres Unicode. `string` é um alias para `System.String` no .NET Framework.

## <a name="remarks"></a>Comentários
Literais de cadeia de caracteres são delimitados pelo caractere de aspas ("). O caractere de barra invertida (\) é usado para codificar alguns caracteres especiais. A barra invertida e o próximo caractere junto são conhecidos como um *sequência de escape*. Suportada em F # de cadeia de caracteres literais são mostrados na tabela a seguir de sequências de escape.

|Caractere|Sequência de escape|
|---------|---------------|
|Backspace|\b|
|Nova linha|\n|
|Retorno de carro|\r|
|Tabulação|\t|
|Barra invertida|\\|
|Aspas|\"|
|Apóstrofo|\'|
|caractere Unicode|\u*XXXX* ou \U*XXXXXXXX* (onde *X* indica um dígito hexadecimal)|

Se precedido pelo símbolo @, o literal é uma cadeia de caracteres textual. Isso significa que qualquer sequências de escape são ignoradas, exceto pelo fato de dois caracteres de aspas são interpretadas como um aspas caractere.

Além disso, uma cadeia de caracteres pode ser delimitada por aspas triplos. Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas. Para especificar uma cadeia de caracteres que contém um inseridos entre aspas, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas. Se você usar uma cadeia de caracteres textual, você deve especificar dois caracteres de aspas para indicar um caractere de aspas simples. Se você usar uma cadeia de caracteres entre aspas triplas, você pode usar os caracteres de aspas simples sem eles sendo analisada como o fim da cadeia de caracteres. Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que contêm aspas inseridas.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

No código, cadeias de caracteres que têm quebras de linha são aceitos e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida é o último caractere antes da quebra de linha. Espaço em branco na próxima linha é ignorado quando o caractere de barra invertida é usado. O código a seguir produz uma cadeia de caracteres `str1` que tem o valor `"abc\n     def"` e uma cadeia de caracteres `str2` que tem o valor `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Você pode acessar caracteres individuais em uma cadeia de caracteres usando a sintaxe de matriz, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

A saída é `b`.

Ou você pode extrair subcadeias de caracteres usando a sintaxe de fatia de matriz, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

A saída é a seguinte.

```
abc
def
```

Você pode representar cadeias de caracteres ASCII, matrizes de bytes não assinados, digite `byte[]`. Adicionar o sufixo `B` para uma cadeia de caracteres literal para indicar que é uma cadeia de caracteres ASCII. Literais de cadeia de caracteres ASCII usados com matrizes de bytes oferecem suporte a sequências de escape como cadeias de caracteres Unicode, exceto para as sequências de escape Unicode.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>Operadores da cadeia de caracteres
Para concatenar cadeias de caracteres de duas maneiras: usando o `+` operador ou usando o `^` operador. O `+` operador mantém a compatibilidade com a cadeia de caracteres do .NET Framework tratamento de recursos.

O exemplo a seguir ilustra a concatenação de cadeia de caracteres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>Classe de cadeia de caracteres
Porque o tipo de cadeia de caracteres em F # é realmente um .NET Framework `System.String` digitar, todo o `System.String` membros estão disponíveis. Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, o `Length` propriedade e o `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caracteres Unicode. Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.

Usando o `Chars` propriedade `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>Módulo de cadeia de caracteres
Funcionalidade adicional para manipulação de cadeia de caracteres está incluída no `String` módulo o `FSharp.Core` namespace. Para obter mais informações, consulte [abreviação de módulo](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
