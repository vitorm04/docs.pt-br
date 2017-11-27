---
title: "Documentação XML (F#)"
description: "Saiba mais sobre o suporte em F # para gerar a documentação de comentários."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d99ab1b6-e170-4ec2-a543-43ea7ab15bb2
ms.openlocfilehash: 20768a7d4ea17c926318043f658691819a3d7d2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documentation"></a>Documentação XML

Você pode gerar a documentação do triple-barra (/ / /) código comentários em F #. Comentários XML podem preceder declarações em arquivos de código (. FS) ou arquivos de assinatura (. FSI).


## <a name="generating-documentation-from-comments"></a>Gerando a documentação de comentários
O suporte em F # para gerar a documentação de comentários é a mesma que em outras linguagens do .NET Framework. Como em outras linguagens .NET Framework, o [-opção de compilador doc](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) permite a criação de um arquivo XML que contém informações que você pode converter em documentação usando uma ferramenta como Sandcastle. A documentação gerada por ferramentas que são projetadas para uso com os assemblies que são escritos em outras linguagens .NET Framework geralmente produzem uma exibição das APIs que se baseia a forma compilada de construções de linguagem F #. A menos que as ferramentas dão suporte especificamente às F #, documentação gerada por essas ferramentas não coincide com a exibição de uma API F #.

Para obter mais informações sobre como gerar a documentação do XML, consulte [comentários de documentação XML &#40; C &#35; Guia de programação &#41; ](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>Marcas recomendadas
Há duas maneiras para escrever comentários de documentação XML. Uma é apenas escrever a documentação diretamente em um comentário de barra tripla, sem o uso de marcas XML. Se você fizer isso, o texto de comentário inteiro será interpretado como a documentação de resumida para a construção de código que segue imediatamente. Use esse método quando desejar gravar um breve resumo para cada construção. O outro método é usar marcas XML para fornecer mais documentação estruturada. O segundo método permite que você especifique notas separadas para um breve resumo e uma descrição do valor de retorno, documentação para cada parâmetro e o parâmetro de tipo e exceções geradas e comentários adicionais. A tabela a seguir descreve as marcas XML que são reconhecidas em comentários de código XML do F #.



|Sintaxe de marca|Descrição|
|----------|-----------|
|**&lt;c&gt;***texto***&lt;/c&gt;**|Especifica que *texto* código. Essa marca pode ser usada pelos geradores de documentação para exibir o texto em uma fonte que é apropriada para o código.|
|**&lt;Resumo&gt;***texto***&lt;resumo&gt;**|Especifica que *texto* uma breve descrição do elemento do programa. A descrição é geralmente uma ou duas frases.|
|**&lt;comentários&gt;***texto* **&lt; /remarks&gt;**|Especifica que *texto* contém informações suplementares sobre o elemento do programa.|
|**&lt;nome do parâmetro = "***nome***"&gt;***descrição***&lt;/param&gt;**|Especifica o nome e descrição para um parâmetro de função ou método.|
|**&lt;typeparam name = "***nome***"&gt;***descrição***&lt;/typeparam&gt;**|Especifica o nome e descrição para um parâmetro de tipo.|
|**&lt;Retorna&gt;***texto* **&lt; /retorna&gt;**|Especifica que *texto* descreve o valor de retorno de uma função ou método.|
|**&lt;exceção cref = "***tipo***"&gt;***descrição***&lt;/exception&gt;**|Especifica o tipo de exceção que pode ser gerada e as circunstâncias sob as quais ela é gerada.|
|**&lt;Consulte cref = "***referência***"&gt;***texto* **&lt; /consulte&gt;**|Especifica um link embutido para outro elemento do programa. O *referência* é o nome como ele aparece no arquivo de documentação XML. O *texto* é o texto mostrado no link.|
|**&lt;Consulte também cref = "***referência***" /&gt;**|Especifica um link também consulte a documentação para outro tipo. O *referência* é o nome como ele aparece no arquivo de documentação XML. Consulte também geralmente aparecem na parte inferior de uma página de documentação de links.|
|**&lt;para&gt;***texto***&lt;/para&gt;**|Especifica um parágrafo de texto. Isso é usado para separar o texto dentro de **comentários** marca.|

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição
Este é um comentário de documentação XML típico em um arquivo de assinatura.


### <a name="code"></a>Código
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição
O exemplo a seguir mostra o método alternativo, sem marcas XML. Neste exemplo, todo o texto do comentário é considerado um resumo. Observe que se você não especificar explicitamente uma marca de resumida, você não deve especificar outras marcas, como **param** ou **retorna** marcas.


### <a name="code"></a>Código
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Opções do Compilador](compiler-options.md)
