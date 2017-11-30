---
title: "Dimensões de matriz no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a>Dimensões de matriz no Visual Basic
Um *dimensão* é uma direção na qual você pode variar a especificação de elementos uma matriz de. Uma matriz que contém as vendas total para cada dia do mês tem uma dimensão (o dia do mês). Uma matriz que contém as total de vendas por departamento para cada dia do mês tem duas dimensões (o número do departamento e o dia do mês). O número de dimensões que tem uma matriz é chamado seu *classificação*.  
  
> [!NOTE]
>  Você pode usar o <xref:System.Array.Rank%2A> propriedade para determinar quantas dimensões tem de uma matriz.  
  
## <a name="working-with-dimensions"></a>Trabalhando com dimensões  
 Você especifica um elemento de uma matriz, fornecendo um *índice* ou *subscrito* para cada uma das suas dimensões. Os elementos são contíguos ao longo de cada dimensão de índice 0 até o índice mais alto para essa dimensão.  
  
 As ilustrações a seguir mostram a estrutura conceitual de matrizes com diferentes classificações. Cada elemento nas ilustrações mostra os valores de índice que acessá-lo. Por exemplo, você pode acessar o primeiro elemento da segunda linha da matriz bidimensional especificando índices `(1, 0)`.  
  
 ![Diagrama de gráfico de um &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
Matriz unidimensional  
  
 ![Diagrama de gráfico de duas &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
matriz bidimensional  
  
 ![Diagrama de gráfico de três &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
matriz tridimensional  
  
### <a name="one-dimension"></a>Uma dimensão  
 Muitas matrizes possuem apenas uma dimensão, como o número de pessoas de cada idade. O único requisito para especificar um elemento é a idade para a qual o elemento contém a contagem. Portanto, essa matriz usa apenas um índice. O exemplo a seguir declara uma variável para manter uma *matriz unidimensional* contagens de idade para idades de 0 a 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Duas dimensões  
 Algumas matrizes possuem duas dimensões, como o número de escritórios em cada andar de cada prédio em um campus. A especificação de um elemento requer o número de construção e o andar, e cada elemento contém a contagem para essa combinação de edifício e andar. Portanto, essa matriz usa dois índices. O exemplo a seguir declara uma variável para manter uma *matriz bidimensional* contagem de escritórios, de edifícios de 0 até 40 e Pisos de 0 a 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Uma matriz bidimensional também é chamada um *matriz retangular*.  
  
### <a name="three-dimensions"></a>Três dimensões  
 Algumas matrizes possuem três dimensões, como valores em espaço tridimensional. Essa matriz usa três índices, que nesse caso representam as coordenadas de z de espaço físico, x e y. O exemplo a seguir declara uma variável para manter uma *matriz tridimensional* temperaturas do ar em vários pontos em um volume tridimensional.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Mais de três dimensões  
 Embora uma matriz pode ter até 32 dimensões, é raro ter mais de três.  
  
> [!NOTE]
>  Quando você adiciona dimensões para uma matriz, o armazenamento total necessário para a matriz aumenta consideravelmente, então use matrizes multidimensionais com cuidado.  
  
## <a name="using-different-dimensions"></a>Usando dimensões diferentes  
 Suponha que você deseja controlar quantidades de vendas para cada dia do mês atual. Você pode declarar uma matriz unidimensional com 31 elementos, um para cada dia do mês, como o exemplo a seguir mostra.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Agora suponha que você deseja controlar as mesmas informações não só para cada dia do mês, mas também para cada mês do ano. Você pode declarar uma matriz bidimensional com 12 linhas (meses) e 31 colunas (para os dias), como mostra o exemplo a seguir.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Agora suponha que você optar por ter sua matriz armazenar informações para mais de um ano. Se você quiser controlar quantidades de vendas por cinco anos, você pode declarar uma matriz tridimensional com 5 camadas, 12 linhas e 31 colunas, como mostra o exemplo a seguir.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Observe que, como cada índice varia de 0 até seu máximo, cada dimensão de `salesAmounts` é declarada como menor que o comprimento necessário para a dimensão. Observe também que o tamanho da matriz aumenta com cada nova dimensão. Os três tamanhos nos exemplos anteriores são 31, 372 e 1,860 elementos respectivamente.  
  
> [!NOTE]
>  Você pode criar uma matriz sem usar o `Dim` instrução ou o `New` cláusula. Por exemplo, você pode chamar o <xref:System.Array.CreateInstance%2A> método ou outro componente pode passar ao seu código uma matriz criada dessa maneira. Essa matriz pode ter um limite inferior diferente de 0. Você sempre pode testar o limite inferior de uma dimensão usando o <xref:System.Array.GetLowerBound%2A> método ou o `LBound` função.  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
