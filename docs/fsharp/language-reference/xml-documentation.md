---
title: Documentação XML (F#)
description: Saiba mais sobre o suporte no F# para gerar a documentação de comentários.
ms.date: 05/16/2016
ms.openlocfilehash: c5305dea8832112644710b2863269ef00feddd10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902168"
---
# <a name="xml-documentation"></a>Documentação XML

Você pode gerar documentação de barra tripla (/ / /) código comentários no F#. Comentários XML podem preceder declarações em arquivos de código (. FS) ou arquivos de assinatura (. FSI).

## <a name="generating-documentation-from-comments"></a>Gerando a documentação de comentários

O suporte no F# para gerar a documentação de comentários é o mesmo que em outras linguagens do .NET Framework. Como em outras linguagens do .NET Framework, o [-opção de compilador doc](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) permite que você produza um arquivo XML que contém informações que você pode converter em documentação usando uma ferramenta como [DocFX](https://dotnet.github.io/docfx/) ou [ Sandcastle](https://github.com/EWSoftware/SHFB). A documentação gerada usando as ferramentas que são projetadas para uso com assemblies que são escritos em outras linguagens do .NET Framework em geral produzir uma exibição das APIs que se baseia a forma compilada de F# constrói. A menos que especificamente suportam a ferramentas de F#, documentação gerada por essas ferramentas não coincide com o F# modo de exibição de uma API.

Para obter mais informações sobre como gerar a documentação de XML, consulte [comentários da documentação XML &#40;C&#35; guia de programação&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Marcações recomendadas

Há duas maneiras para escrever comentários de documentação XML. Uma é simplesmente escrever a documentação diretamente em um comentário de barra tripla, sem o uso de marcas XML. Se você fizer isso, o texto de comentário inteiro será interpretado como a documentação de resumida para a construção de código que segue imediatamente. Use esse método quando quiser escrever um breve resumo para cada constructo. O outro método é usar as marcas XML para fornecer mais documentação estruturada. O segundo método permite que você especifique notas separadas para um breve resumo, comentários adicionais, a documentação para cada parâmetro e o parâmetro de tipo e as exceções geradas e uma descrição do valor de retorno. A tabela a seguir descreve as marcas XML que são reconhecidas no F# comentários de código XML.

|Sintaxe de marca|Descrição|
|----------|-----------|
|**\<c\>**_text_**\</c\>**|Especifica que *texto* é o código. Essa marca pode ser usada por geradores de documentação para exibir texto em uma fonte que é apropriada para o código.|
|**\<summary\>**_text_**\</summary\>**|Especifica que *texto* é uma breve descrição do elemento de programa. A descrição é geralmente uma ou duas sentenças.|
|**\<remarks\>**_text_**\</remarks\>**|Especifica que *texto* contém informações suplementares sobre o elemento de programa.|
|**\<param name="**_name_**"\>**_description_**\</param\>**|Especifica o nome e descrição para um parâmetro de método ou função.|
|**\<typeparam name="**_name_**"\>**_description_**\</typeparam\>**|Especifica o nome e uma descrição para um parâmetro de tipo.|
|**\<returns\>**_text_**\</returns\>**|Especifica que *texto* descreve o valor de retorno de uma função ou método.|
|**\<exception cref="**_type_**"\>**_description_**\</exception\>**|Especifica o tipo de exceção que pode ser gerada e as circunstâncias sob as quais ela é gerada.|
|**\<see cref="**_reference_**"\>**_text_**\</see\>**|Especifica um link embutido para outro elemento de programa. O *referência* é o nome como ele aparece no arquivo de documentação XML. O *texto* é o texto mostrado no link.|
|**\<seealso cref="**_reference_**"/\>**|Especifica um link também consulte a documentação para outro tipo. O *referência* é o nome como ele aparece no arquivo de documentação XML. Consulte também geralmente aparecem na parte inferior de uma página de documentação de links.|
|**\<para\>**_text_**\</para\>**|Especifica um parágrafo de texto. Isso é usado para separar o texto dentro de **comentários** marca.|

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

Este é um comentário de documentação XML típico em um arquivo de assinatura.

### <a name="code"></a>Código

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir mostra o método alternativo, sem as marcas XML. Neste exemplo, todo o texto do comentário é considerado um resumo. Observe que se você não especificar explicitamente uma marca de resumida, você deve especificar outras marcas, como **param** ou **retorna** marcas.

### <a name="code"></a>Código

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Opções do Compilador](compiler-options.md)
