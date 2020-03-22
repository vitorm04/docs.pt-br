---
title: Valores de retorno do árbitro
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186930"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Suporte para valores de retorno de referência (Visual Basic)

Começando com C# 7.0, o idioma C# suporta *valores de retorno de referência*. Uma maneira de entender os valores de retorno de referência é que eles são o oposto de argumentos que são passados por referência a um método. Quando um argumento aprovado por referência é modificado, as alterações são refletidas no valor da variável no chamador. Quando um método fornece um valor de retorno de referência a um chamador, as modificações feitas no valor de retorno de referência pelo chamador são refletidas nos dados do método chamado.

O Visual Basic não permite que você autorde métodos com valores de retorno de referência, mas permite que você consuma valores de retorno de referência. Em outras palavras, você pode chamar um método com um valor de retorno de referência e modificar esse valor de retorno, e as alterações no valor de retorno de referência são refletidas nos dados do método chamado.

## <a name="modifying-the-ref-return-value-directly"></a>Modificando diretamente o valor de retorno do ref

Para métodos que sempre `ByRef` têm sucesso e não têm parâmetros, você pode modificar o valor de retorno de referência diretamente. Você faz isso atribuindo o novo valor às expressões que retornam o valor de retorno de referência.

O exemplo C# a `NumericValue.IncrementValue` seguir define um método que incrementa um valor interno e o retorna como um valor de retorno de referência.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

O valor de retorno de referência é então modificado pelo chamador no exemplo Visual Basic a seguir. Observe que a `NumericValue.IncrementValue` linha com a chamada do método não atribui um valor ao método. Em vez disso, ele atribui um valor ao valor de retorno de referência retornado pelo método.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Usando um método auxiliar

Em outros casos, modificar diretamente o valor de retorno de referência de uma chamada de método pode nem sempre ser desejável. Por exemplo, um método de pesquisa que retorna uma string pode nem sempre encontrar uma correspondência. Nesse caso, você deseja modificar o valor de retorno de referência somente se a pesquisa for bem sucedida.

O exemplo C# a seguir ilustra este cenário. Ele define `Sentence` uma classe escrita em `FindNext` C# inclui um método que encontra a próxima palavra em uma frase que começa com uma substring especificada. A cadeia de caracteres é retornada como um valor retornado de referência e uma variável `Boolean` passada pela referência para o método indica se a pesquisa foi bem-sucedida. O valor de retorno de referência indica que, além da leitura do valor retornado, o chamador `Sentence` também pode modificá-lo, e essa modificação é refletida nos dados contidos internamente na classe.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Modificar diretamente o valor de retorno de referência neste caso não é confiável, uma vez que a chamada do método pode não encontrar uma correspondência e retornar a primeira palavra na frase. Nesse caso, o interlocutor modificará inadvertidamente a primeira palavra da sentença. Isso pode ser evitado pelo chamador que retorna um `null` (ou `Nothing` no Visual Basic). Mas nesse caso, tentar modificar uma string `Nothing` cujo <xref:System.NullReferenceException>valor é lança um . Se também pudesse ser impedido pelo <xref:System.String.Empty?displayProperty=nameWithType>chamador retornar, mas isso requer que <xref:System.String.Empty?displayProperty=nameWithType>o chamador defina uma variável de string cujo valor é . Embora o chamador possa modificar essa seqüência, a modificação em si não serve `Sentence` para nada, uma vez que a seqüência modificada não tem relação com as palavras na frase armazenada pela classe.

A melhor maneira de lidar com esse cenário é passar o valor de retorno de referência por referência a um método auxiliar. O método auxiliar contém então a lógica para determinar se a chamada do método foi bem sucedida e, se o fez, para modificar o valor de retorno de referência. O exemplo a seguir fornece uma possível implementação.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Confira também

- [Passando argumentos por valor e por referência](passing-arguments-by-value-and-by-reference.md)
- [Procedimentos no Visual Basic](index.md)
