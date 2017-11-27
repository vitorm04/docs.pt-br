---
title: Solucionando problemas de matrizes (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a>Solucionando problemas de matrizes (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Erros de compilação declarar e inicializar uma matriz  
 Erros de compilação podem surgir de erro das regras para declarar, criando e inicializando matrizes. As causas mais comuns de erros são os seguintes:  
  
-   Fornecendo um [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) cláusula depois de especificar tamanhos de dimensão na declaração de variável de matriz. As linhas de código a seguir mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Especificando os comprimentos de dimensão para mais do que a matriz de nível superior de uma matriz denteada. A linha de código a seguir mostra uma declaração inválida deste tipo.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   A omissão de `New` palavra-chave ao especificar os valores de elemento. A linha de código a seguir mostra uma declaração inválida deste tipo.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Fornecendo um `New` cláusula sem as chaves (`{}`). As linhas de código a seguir mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Acessar uma matriz fora dos limites  
 O processo de inicializar uma matriz atribui um limite superior e um limite inferior de cada dimensão. Todo o acesso a um elemento da matriz deve especificar um índice válido ou subscrição, para cada dimensão. Se qualquer índice estiver abaixo de seu limite inferior ou acima de seu limite superior, um <xref:System.IndexOutOfRangeException> resultados de exceção. O compilador não pode detectar um erro, portanto ocorre um erro em tempo de execução.  
  
### <a name="determining-bounds"></a>Determinar os limites  
 Se outro componente passa uma matriz para o seu código, por exemplo como um argumento de procedimento, você não souber o tamanho de matriz ou os comprimentos de suas dimensões. Você sempre deve determinar o limite superior de cada dimensão de uma matriz antes de tentar acessar todos os elementos. Se a matriz foi criada por meios diferente de um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` cláusula, o limite inferior pode ser algo diferente de 0, e é mais seguro determinar esse limite inferior também.  
  
### <a name="specifying-the-dimension"></a>Especificação de dimensão  
 Ao determinar os limites de uma matriz multidimensional, tome cuidado como especificar a dimensão. O `dimension` parâmetros do <xref:System.Array.GetLowerBound%2A> e <xref:System.Array.GetUpperBound%2A> métodos são baseados em 0, enquanto o `Rank` parâmetros do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> e <xref:Microsoft.VisualBasic.Information.UBound%2A> funções são baseados em 1.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
