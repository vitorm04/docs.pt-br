---
title: Documentação XML (F#)
description: 'Saiba mais sobre o suporte em F # para gerar a documentação de comentários.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a4cb132e65b630821e5eb2b39276c1de99aff80
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214128"
---
# <a name="xml-documentation"></a>Documentação XML

Você pode gerar documentação de barra tripla (/ / /) comentários em F # de código. Comentários XML podem preceder declarações em arquivos de código (. FS) ou arquivos de assinatura (. FSI).

## <a name="generating-documentation-from-comments"></a>Gerando a documentação de comentários

O suporte em F # para gerar a documentação de comentários é o mesmo que em outras linguagens do .NET Framework. Como em outras linguagens do .NET Framework, o [-opção de compilador doc](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) permite que você produza um arquivo XML que contém informações que você pode converter em documentação usando uma ferramenta como o Sandcastle. A documentação gerada usando as ferramentas que são projetadas para uso com assemblies que são escritos em outras linguagens do .NET Framework em geral produzir uma exibição das APIs que se baseia a forma compilada de construções no F #. A menos que especificamente suporte a ferramentas F #, documentação gerada por essas ferramentas não coincide com a exibição do F # de uma API.

Para obter mais informações sobre como gerar a documentação de XML, consulte [comentários da documentação XML &#40;C&#35; guia de programação&#41;](https://msdn.microsoft.com/library/b2s063f7).

## <a name="recommended-tags"></a>Marcações recomendadas

Há duas maneiras para escrever comentários de documentação XML. Uma é simplesmente escrever a documentação diretamente em um comentário de barra tripla, sem o uso de marcas XML. Se você fizer isso, o texto de comentário inteiro será interpretado como a documentação de resumida para a construção de código que segue imediatamente. Use esse método quando quiser escrever um breve resumo para cada constructo. O outro método é usar as marcas XML para fornecer mais documentação estruturada. O segundo método permite que você especifique notas separadas para um breve resumo, comentários adicionais, a documentação para cada parâmetro e o parâmetro de tipo e as exceções geradas e uma descrição do valor de retorno. A tabela a seguir descreve as marcas XML que são reconhecidas em comentários de código XML do F #.

|Sintaxe de marca|Descrição|
|----------|-----------|
|**&lt;c&gt;***texto***&lt;/c&gt;**|Especifica que *texto* é o código. Essa marca pode ser usada por geradores de documentação para exibir texto em uma fonte que é apropriada para o código.|
|**&lt;Resumo&gt;***texto*** &lt; /summary&gt;**|Especifica que *texto* é uma breve descrição do elemento de programa. A descrição é geralmente uma ou duas sentenças.|
|**&lt;comentários&gt;***texto*** &lt; /remarks&gt;**|Especifica que *texto* contém informações suplementares sobre o elemento de programa.|
|**&lt;nome do parâmetro = "***nome***"&gt;***descrição***&lt;/param&gt;**|Especifica o nome e descrição para um parâmetro de método ou função.|
|**&lt;typeparam nome = "***nome***"&gt;***descrição***&lt;/typeparam&gt;**|Especifica o nome e uma descrição para um parâmetro de tipo.|
|**&lt;Retorna&gt;***texto*** &lt; /returns&gt;**|Especifica que *texto* descreve o valor de retorno de uma função ou método.|
|**&lt;exceção cref = "***tipo***"&gt;***descrição***&lt;/exception&gt;**|Especifica o tipo de exceção que pode ser gerada e as circunstâncias sob as quais ela é gerada.|
|**&lt;Consulte cref = "***referência***"&gt;***texto*** &lt; /see&gt;**|Especifica um link embutido para outro elemento de programa. O *referência* é o nome como ele aparece no arquivo de documentação XML. O *texto* é o texto mostrado no link.|
|**&lt;seealso cref = "***referência***" /&gt;**|Especifica um link também consulte a documentação para outro tipo. O *referência* é o nome como ele aparece no arquivo de documentação XML. Consulte também geralmente aparecem na parte inferior de uma página de documentação de links.|
|**&lt;parágrafo&gt;***texto***&lt;/para&gt;**|Especifica um parágrafo de texto. Isso é usado para separar o texto dentro de **comentários** marca.|

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
