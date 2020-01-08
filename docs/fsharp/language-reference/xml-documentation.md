---
title: Documentação XML
description: Saiba mais sobre o F# suporte no para gerar documentação de comentários.
ms.date: 05/16/2016
ms.openlocfilehash: 0a87915c361fc88f0c05264e1c17278fd656a167
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344685"
---
# <a name="xml-documentation"></a>Documentação XML

Você pode produzir documentação de comentários de código de barra tripla (///) F#no. Os comentários XML podem preceder declarações nos arquivos de código (. FS) ou de assinatura (. FSI).

## <a name="generating-documentation-from-comments"></a>Gerando documentação de comentários

O suporte no F# para gerar documentação de comentários é o mesmo que em outras linguagens de .NET Framework. Como em outras linguagens de .NET Framework, a [opção-doc do compilador](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) permite que você produza um arquivo XML que contém informações que você pode converter em documentação usando uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB). A documentação gerada usando ferramentas que são projetadas para uso com assemblies que são escritos em outras linguagens de .NET Framework geralmente produzem uma exibição das APIs com base na forma compilada de F# construções. A menos que as F#ferramentas tenham suporte especificamente, a documentação gerada por essas F# ferramentas não corresponde à exibição de uma API.

Para obter mais informações sobre como gerar documentação do XML, consulte [comentários &#40;de documentação XML&#35; &#41;guia de programação C](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Marcas recomendadas

Há duas maneiras de escrever comentários de documentação XML. Uma delas é apenas escrever a documentação diretamente em um comentário de barra tripla, sem usar marcas XML. Se você fizer isso, todo o texto do comentário será levado como a documentação resumida da construção de código que segue imediatamente. Use esse método quando desejar escrever apenas um breve resumo para cada construção. O outro método é usar marcas XML para fornecer documentação mais estruturada. O segundo método permite que você especifique anotações separadas para um breve resumo, comentários adicionais, documentação para cada parâmetro e parâmetro de tipo e exceções lançadas e uma descrição do valor de retorno. A tabela a seguir descreve as marcas XML que são F# reconhecidas em comentários de código XML.

|Sintaxe de marca|Descrição|
|----------|-----------|
|**\<c\>** _text_ **\</c\>**|Especifica que o *texto* é o código. Essa marca pode ser usada por geradores de documentação para exibir texto em uma fonte apropriada para o código.|
|**\<resumo\>** _texto_ **\</Summary\>**|Especifica que o *texto* é uma breve descrição do elemento Program. A descrição geralmente é uma ou duas frases.|
|**\<comentários\>** _texto_ **\</Remarks\>**|Especifica que o *texto* contém informações suplementares sobre o elemento Program.|
|**\<param Name = "** _Name_ **"\>** _Descrição_ **\</param\>**|Especifica o nome e a descrição de um parâmetro de função ou método.|
|**\<typeparam Name = "** _Name_ **"\>** _Descrição_ **\</typeparam\>**|Especifica o nome e a descrição de um parâmetro de tipo.|
|**\<retorna\>** _texto_ **\</Returns\>**|Especifica que o *texto* descreve o valor de retorno de uma função ou método.|
|**\<exception cref="** _type_ **"\>** _description_ **\</exception\>**|Especifica o tipo de exceção que pode ser gerado e as circunstâncias sob as quais ela é gerada.|
|**\<ver cref = "** _referência_ **"\>** _texto_ **\</See\>**|Especifica um link embutido para outro elemento de programa. A *referência* é o nome que aparece no arquivo de documentação XML. O *texto* é o texto mostrado no link.|
|**\<seealso cref="** _reference_ **"/\>**|Especifica um link consulte também a documentação de outro tipo. A *referência* é o nome que aparece no arquivo de documentação XML. Consulte também os links geralmente aparecem na parte inferior de uma página de documentação.|
|texto do **\<\>** **\</para\>**|Especifica um parágrafo de texto. Isso é usado para separar o texto dentro da marca de **comentários** .|

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

Este é um comentário de documentação XML típico em um arquivo de assinatura.

### <a name="code"></a>Código

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir mostra o método alternativo, sem marcas XML. Neste exemplo, o texto inteiro no comentário é considerado um resumo. Observe que se você não especificar uma marca de resumo explicitamente, não deverá especificar outras marcas, como **param** ou **retorna** marcas.

### <a name="code"></a>Código

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Veja também

- [Referência da Linguagem F#](index.md)
- [Opções do Compilador](compiler-options.md)
