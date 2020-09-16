---
title: Documentação XML
description: 'Saiba mais sobre o suporte no F # para gerar documentação de comentários.'
ms.date: 05/16/2016
ms.openlocfilehash: 03d14cef910d149f0c7a2f3a49c8cf4606ac5305
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556571"
---
# <a name="xml-documentation"></a>Documentação XML

Você pode produzir a documentação de comentários de código de barra tripla (///) em F #. Os comentários XML podem preceder declarações nos arquivos de código (. FS) ou de assinatura (. FSI).

## <a name="generating-documentation-from-comments"></a>Gerando documentação de comentários

O suporte no F # para gerar documentação de comentários é o mesmo que em outras linguagens de .NET Framework. Como em outras linguagens de .NET Framework, a [opção-doc do compilador](./compiler-options.md) permite que você produza um arquivo XML que contém informações que você pode converter em documentação usando uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB). A documentação gerada usando ferramentas projetadas para uso com assemblies que são escritos em outras linguagens de .NET Framework geralmente produz uma exibição das APIs que se baseiam na forma compilada de construções F #. A menos que as ferramentas especificamente ofereçam suporte a F #, a documentação gerada por essas ferramentas não corresponde à exibição F # de uma API.

Para obter mais informações sobre como gerar documentação do XML, consulte [comentários de documentação xml &#40;guia de programação C&#35;&#41;](../../csharp/programming-guide/xmldoc/index.md).

## <a name="recommended-tags"></a>Marcas recomendadas

Há duas maneiras de escrever comentários de documentação XML. Uma delas é apenas escrever a documentação diretamente em um comentário de barra tripla, sem usar marcas XML. Se você fizer isso, todo o texto do comentário será levado como a documentação resumida da construção de código que segue imediatamente. Use esse método quando desejar escrever apenas um breve resumo para cada construção. O outro método é usar marcas XML para fornecer documentação mais estruturada. O segundo método permite que você especifique anotações separadas para um breve resumo, comentários adicionais, documentação para cada parâmetro e parâmetro de tipo e exceções lançadas e uma descrição do valor de retorno. A tabela a seguir descreve as marcas XML que são reconhecidas nos comentários de código XML F #.

|Sintaxe de marca|Descrição|
|----------|-----------|
|**\<c\>**_texto_**\</c\>**|Especifica que o *texto* é o código. Essa marca pode ser usada por geradores de documentação para exibir texto em uma fonte apropriada para o código.|
|**\<summary\>**_texto_**\</summary\>**|Especifica que o *texto* é uma breve descrição do elemento Program. A descrição geralmente é uma ou duas frases.|
|**\<remarks\>**_texto_**\</remarks\>**|Especifica que o *texto* contém informações suplementares sobre o elemento Program.|
|**\<param name="**_name_**"\>**_ndescrição_**\</param\>**|Especifica o nome e a descrição de um parâmetro de função ou método.|
|**\<typeparam name="**_name_**"\>**_ndescrição_**\</typeparam\>**|Especifica o nome e a descrição de um parâmetro de tipo.|
|**\<returns\>**_texto_**\</returns\>**|Especifica que o *texto* descreve o valor de retorno de uma função ou método.|
|**\<exception cref="**_type_**"\>**_ndescrição_**\</exception\>**|Especifica o tipo de exceção que pode ser gerado e as circunstâncias sob as quais ela é gerada.|
|**\<see cref="**_reference_**"\>**_texto_**\</see\>**|Especifica um link embutido para outro elemento de programa. A *referência* é o nome que aparece no arquivo de documentação XML. O *texto* é o texto mostrado no link.|
|**\<seealso cref="**_reference_**"/\>**|Especifica um link consulte também a documentação de outro tipo. A *referência* é o nome que aparece no arquivo de documentação XML. Consulte também os links geralmente aparecem na parte inferior de uma página de documentação.|
|**\<para\>**_texto_**\</para\>**|Especifica um parágrafo de texto. Isso é usado para separar o texto dentro da marca de **comentários** .|

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

## <a name="see-also"></a>Confira também

- [Referência de linguagem F #](index.md)
- [Opções do compilador](compiler-options.md)
