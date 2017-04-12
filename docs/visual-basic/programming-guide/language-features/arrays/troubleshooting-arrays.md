---
title: Solucionando problemas de matrizes (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: db38c0c2a4f8b74a6b862f86f426b4d8837f4424
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a>Solucionando problemas de matrizes (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Erros de compilação declarar e inicializar uma matriz  
 Erros de compilação podem surgir de compreensão das regras para declarar, criando e inicializando matrizes. As causas mais comuns de erros são os seguintes:  
  
-   Fornecendo uma [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) cláusula após especificar os comprimentos de dimensão na declaração da variável de matriz. As seguintes linhas de código mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Especificar tamanhos de dimensão para mais do que a matriz de nível superior de uma matriz denteada. A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Omitindo o `New` palavra-chave ao especificar os valores de elemento. A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Fornecendo uma `New` cláusula sem chaves (`{}`). As seguintes linhas de código mostram inválidas declarações desse tipo.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Acessar uma matriz fora dos limites  
 O processo de inicializar uma matriz atribui um limite superior e um limite inferior de cada dimensão. Cada acesso a um elemento da matriz deve especificar um índice válido ou subscrição, para cada dimensão. Se qualquer índice estiver abaixo de seu limite inferior ou acima de seu limite superior, um <xref:System.IndexOutOfRangeException>resultados de exceção.</xref:System.IndexOutOfRangeException> O compilador não pode detectar um erro, para que ocorra um erro em tempo de execução.  
  
### <a name="determining-bounds"></a>Determinando limites  
 Se outro componente passar uma matriz para o seu código, por exemplo como um argumento de procedimento, você não souber o tamanho da matriz ou os comprimentos das suas dimensões. Você sempre deve determinar o limite superior de cada dimensão de uma matriz antes de tentar acessar quaisquer elementos. Se a matriz foi criada por alguns meios diferente de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` cláusula, o limite inferior pode ser algo diferente de 0, e é mais seguro determinar esse limite inferior também.  
  
### <a name="specifying-the-dimension"></a>Especificar a dimensão  
 Ao determinar os limites de uma matriz multidimensional, tome cuidado como especificar a dimensão. O `dimension` parâmetros da <xref:System.Array.GetLowerBound%2A>e <xref:System.Array.GetUpperBound%2A>métodos são baseadas em 0, enquanto o `Rank` parâmetros do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>e <xref:Microsoft.VisualBasic.Information.UBound%2A>funções são baseados em 1.</xref:Microsoft.VisualBasic.Information.UBound%2A> </xref:Microsoft.VisualBasic.Information.LBound%2A> </xref:System.Array.GetUpperBound%2A> </xref:System.Array.GetLowerBound%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Como: inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
