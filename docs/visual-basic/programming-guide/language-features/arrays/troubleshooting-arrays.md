---
title: Solucionando problemas de matrizes (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833367"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Solucionando problemas de matrizes (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Declarar e inicializar uma matriz de erros de compilação  
 Erros de compilação podem surgir de compreensão das regras para declarar, criando e inicializando matrizes. As causas mais comuns de erros são as seguintes:  
  
-   Fornecendo uma [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) cláusula depois de especificar os tamanhos da dimensão na declaração da variável de matriz. As linhas de código a seguir mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Especificando os comprimentos de dimensão por mais de uma matriz de nível superior de uma matriz denteada. A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Omitindo o `New` palavra-chave ao especificar os valores de elemento. A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Fornecendo uma `New` cláusula sem as chaves (`{}`). As linhas de código a seguir mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Acessar uma matriz fora dos limites  
 O processo de inicializar uma matriz atribui um limite superior e um limite inferior para cada dimensão. Todos os acessos a um elemento da matriz devem especificar um índice válido ou subscrito, para cada dimensão. Se qualquer índice estiver abaixo de seu limite inferior ou acima de seu limite superior, um <xref:System.IndexOutOfRangeException> resultados de exceção. O compilador não pode detectar o erro, portanto, ocorre um erro em tempo de execução.  
  
### <a name="determining-bounds"></a>Determinando limites  
 Se outro componente passa uma matriz para o seu código, por exemplo como um argumento de procedimento, você não sabe o tamanho da matriz ou os comprimentos de suas dimensões. Você sempre deve determinar o limite superior de cada dimensão de uma matriz antes de tentar acessar todos os elementos. Se a matriz tiver sido criada por meios que não seja um Visual Basic `New` cláusula, o limite inferior pode ser algo diferente de 0, e é mais seguro determinar o limite inferior também.  
  
### <a name="specifying-the-dimension"></a>Especifica a dimensão  
 Ao determinar os limites de uma matriz multidimensional, lembre-se de como você especifica a dimensão. O `dimension` parâmetros do <xref:System.Array.GetLowerBound%2A> e <xref:System.Array.GetUpperBound%2A> métodos são baseados em 0, enquanto o `Rank` parâmetros do Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> e <xref:Microsoft.VisualBasic.Information.UBound%2A> funções são baseados em 1.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Como: Inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
