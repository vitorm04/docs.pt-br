---
title: Valores retornados de referência (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791801"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Suporte para valores retornados por referência (Visual Basic)

Começando com C# 7.0, o C# dá suporte a idioma *fazer referência a valores de retorno*. Uma maneira de entender os valores retornados por referência é que eles são o oposto de argumentos que são passados por referência a um método. Quando um argumento passado por referência é modificado, as alterações são refletidas no valor da variável no chamador. Quando um método fornece um valor de retorno de referência para um chamador, as modificações feitas para o valor retornado por referência pelo chamador são refletidas nos dados de um método chamado.

Visual Basic não permite a métodos de autor com referência de valores de retorno, mas ela permitem consumir valores retornados por referência. Em outras palavras, você pode chamar um método com um valor de retorno de referência e modificar esse valor de retorno, e as alterações para o valor retornado por referência são refletidas nos dados de um método chamado.

## <a name="modifying-the-ref-return-value-directly"></a>Modificar o valor de retorno de ref diretamente

Para métodos que sempre ter êxito e não têm `ByRef` parâmetros, você pode modificar diretamente o valor retornado por referência. Você pode fazer isso, atribua o novo valor às expressões que retorna o valor retornado por referência. 

O seguinte C# exemplo define uma `NumericValue.IncrementValue` valor de retorno do método que incrementa um valor interno e o retorna como uma referência. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

A referência de retornar o valor é modificado, em seguida, pelo chamador no exemplo do Visual Basic a seguir. Observe que a linha com o `NumericValue.IncrementValue` chamada de método não atribui um valor para o método. Em vez disso, ele atribui um valor para o valor retornado por referência retornado pelo método.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Usando um método auxiliar

Em outros casos, modificando o valor de retorno de referência de uma chamada de método diretamente pode não sempre ser desejável. Por exemplo, um método de pesquisa que retorna uma cadeia de caracteres pode não sempre encontrar uma correspondência. Nesse caso, você deseja modificar o valor retornado por referência somente se a pesquisa for bem-sucedida.

O seguinte C# exemplo ilustra esse cenário. Ele define uma `Sentence` classe escrito em C# inclui um `FindNext` método que localiza a próxima palavra em uma sentença que começa com uma subcadeia de caracteres especificada. A cadeia de caracteres é retornada como um valor retornado de referência e uma variável `Boolean` passada pela referência para o método indica se a pesquisa foi bem-sucedida. O valor retornado por referência indica que o chamador não pode apenas ler o valor retornado; Ele também pode modificá-lo e essa modificação é refletida nos dados contidos em internamente o `Sentence` classe.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Modificando diretamente a referência de valor retornado nesse caso não é confiável, uma vez que a chamada de método poderá não conseguir encontrar uma correspondência e retornar a primeira palavra na frase. Nesse caso, o chamador modifique inadvertidamente a primeira palavra da sentença. Isso poderia ser evitado pelo chamador retornar um `null` (ou `Nothing` no Visual Basic). Mas nesse caso, a tentativa de modificar uma cadeia de caracteres cujo valor é `Nothing` lança um <xref:System.NullReferenceException>. Se também poderia ser evitada pelo chamador retornando <xref:System.String.Empty?displayProperty=nameWithType>, mas isso requer que o chamador definir uma variável de cadeia de caracteres cujo valor é <xref:System.String.Empty?displayProperty=nameWithType>. Enquanto o chamador pode modificar essa cadeia de caracteres, a modificação em si tem nenhuma finalidade, desde que a cadeia de caracteres modificada não tem relação com as palavras na frase armazenada pelo `Sentence` classe.

A melhor maneira de lidar com esse cenário é passar o valor de retorno de referência por referência para um método auxiliar. O método auxiliar, em seguida, contém a lógica para determinar se a chamada de método foi bem-sucedida e, se tivesse, para modificar a valor retornado de referência. O exemplo a seguir fornece uma implementação possível.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Consulte também

- [Passando argumentos por valor e por referência](passing-arguments-by-value-and-by-reference.md)
- [Procedimentos no Visual Basic](index.md)
