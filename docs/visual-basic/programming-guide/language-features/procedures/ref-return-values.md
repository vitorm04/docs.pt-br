---
title: "Valores de retorno de referência (Visual Basic)"
ms.custom: 
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 560607f7aa304b25314daabeef3952e6bbef7426
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="support-for-reference-return-values-visual-basic"></a>Suporte para valores de retorno de referência (Visual Basic)

Começando com o c# 7, oferece suporte a linguagem c# *fazer referência a valores de retorno*. Uma maneira de entender os valores de retorno de referência é que eles são o oposto de argumentos que são transmitidos por referência a um método. Quando um argumento passado por referência é modificado, as alterações são refletidas no valor da variável no chamador. Quando um método fornece um valor de retorno de referência para um chamador, as modificações feitas para o valor de retorno de referência pelo chamador são refletidas nos dados de chamada do método.

Visual Basic não permite a você criar métodos com referência retorna valores, mas permite a você consumir os valores de retorno de referência. Em outras palavras, você pode chamar um método com um valor de retorno de referência e modificar esse valor de retorno, e as alterações para o valor de retorno de referência são refletidas nos dados de chamada do método.

## <a name="modifying-the-ref-return-value-directly"></a>Modificando o valor de retorno de ref diretamente

Para métodos que sempre tenha êxito e não têm `ByRef` parâmetros, você pode modificar o valor de retorno de referência diretamente. Você pode fazer isso atribuindo o novo valor para as expressões que retorna o valor de retorno de referência. 

O exemplo c# a seguir define uma `NumericValue.IncrementValue` valor de retorno do método que incrementa um valor interno e o retorna como uma referência. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

A referência de retornar o valor é então modificado pelo chamador no seguinte exemplo do Visual Basic. Observe que a linha com o `NumericValue.IncrementValue` chamada de método não atribui um valor para o método. Em vez disso, ele atribui um valor para o valor de retorno de referência retornado pelo método.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Usando um método auxiliar

Em outros casos, modificar o valor de retorno de referência de uma chamada de método diretamente não sempre pode ser desejável. Por exemplo, um método de pesquisa que retorna uma cadeia de caracteres pode não localizar sempre uma correspondência. Nesse caso, você deseja modificar o valor de retorno de referência somente se a pesquisa for bem-sucedida.

O exemplo c# a seguir ilustra esse cenário. Define uma `Sentence` classe escrita em c# inclui um `FindNext` método que localiza a próxima palavra em uma frase que começa com uma subcadeia de caracteres especificada. A cadeia de caracteres é retornada como um valor retornado de referência e uma variável `Boolean` passada pela referência para o método indica se a pesquisa foi bem-sucedida. O valor de retorno de referência indica que o chamador não é possível apenas ler o valor retornado; Ele também pode modificá-la e modificação é refletida nos dados contidos internamente no `Sentence` classe.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Modificando diretamente a referência do valor de retorno nesse caso não é confiável, desde que a chamada de método pode não conseguir encontrar uma correspondência e retorna a primeira palavra da frase. Nesse caso, o chamador inadvertidamente modificará a primeira palavra da frase. Isso poderia ser evitado pelo chamador retornando um `null` (ou `Nothing` no Visual Basic). Mas nesse caso, a tentativa de modificar uma cadeia de caracteres cujo valor é `Nothing` lança um <xref:System.NullReferenceException>. Se também poderia ser evitado pelo chamador retornando <xref:System.String.Empty?displayProperty=nameWithType>, mas isso requer que o chamador definir uma variável de cadeia de caracteres cujo valor é <xref:System.String.Empty?displayProperty=nameWithType>. Enquanto o chamador pode modificar essa cadeia de caracteres, a modificação em si não existe nenhum propósito, desde que a cadeia de caracteres modificada não tem nenhuma relação com as palavras na frase armazenada pelo `Sentence` classe.

A melhor maneira de lidar com esse cenário é passar o valor de retorno de referência por referência a um método auxiliar. O método auxiliar, em seguida, contém a lógica para determinar se a chamada de método foi bem-sucedida e, em caso positivo, para modificar a referência do valor de retorno. O exemplo a seguir fornece uma implementação possíveis.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Consulte também

[Passando argumentos por valor e por referência](passing-arguments-by-value-and-by-reference.md)   
[Procedimentos no Visual Basic](index.md)   


