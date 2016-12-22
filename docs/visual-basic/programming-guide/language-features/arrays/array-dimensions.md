---
title: "Dimens&#245;es de matriz no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], dimensões"
  - "matrizes [Visual Basic], classificação"
  - "matrizes [Visual Basic], retangulares"
  - "dimensões, matrizes"
  - "classificação, matrizes"
  - "matrizes retangulares"
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Dimens&#245;es de matriz no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma *Dimensão* é uma direção na qual você pode variar a especificação de uma matriz de elementos.  Uma matriz que contém o total de vendas para cada dia do mês tem uma dimensão \(o dia do mês\).  Uma matriz que contém o total de vendas por departamento para cada dia do mês tem duas dimensões \(o número do departamento e o dia do mês\).  O número de dimensões que tem uma matriz é chamado de  *classificação* .  
  
> [!NOTE]
>  Você pode usar o <xref:System.Array.Rank%2A> propriedade para determinar as dimensões de quantos possui de uma matriz.  
  
## Trabalhando com dimensões  
 Você especifica um elemento de uma matriz, fornecendo um *index* ou *Subscript* para cada uma das suas dimensões.  Os elementos são contíguos ao longo de cada dimensão de índice até o índice mais alto para a dimensão.  
  
 As ilustrações a seguir mostram a estrutura conceitual de matrizes com diferentes classificações.  Cada elemento nas ilustrações mostra os valores de índice que a acessam.  Por exemplo, você pode acessar o primeiro elemento da segunda linha da matriz bidimensional especificando índices `(1, 0)`.  
  
 ![Diagrama gráfico de matriz unidimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.png "ArrayExDimOne")  
Matriz unidimensional  
  
 ![Diagrama gráfico de matriz bidimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.png "ArrayExDimTwo")  
Matriz bidimensional  
  
 ![Diagrama gráfico de matriz tridimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
Matriz tridimensional  
  
### Uma dimensão  
 Muitas matrizes possuem apenas uma dimensão, como o número de pessoas de cada idade.  O único requisito para especificar um elemento é a idade para a qual o elemento contém a contagem.  Portanto, esse uma matriz usa apenas um índice.  O exemplo a seguir declara uma variável para conter uma  *matriz unidimensional*  das contagens de idade para idades de 0 a 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### Duas dimensões  
 Algumas matrizes possuem duas dimensões, como o número de escritórios em cada andar de cada prédio em um campus.  A especificação de um elemento requer o número de construção e o andar, e cada elemento contém a contagem para essa combinação de construção e andar.  Portanto, essa matriz usa dois índices.  O exemplo a seguir declara uma variável para conter  *uma matriz bidimensiona*  de contagem de escritórios, de edifícios de 0 até 40 e andares de 0 a 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Uma matriz bidimensional também é chamada de  *matriz retangular* .  
  
### Três dimensões  
 Algumas matrizes possuem três dimensões, tais como valores em espaço tridimensional.  Tal uma matriz usa três índices, que nesse caso representam as coordenadas x, y e z do espaço físico.  O exemplo a seguir declara uma variável para conter uma  *matriz tridimensional*  de temperaturas do ar em vários pontos em um volume tridimensional.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### Mais de três dimensões  
 Embora uma matriz possa ter até 32 dimensões, é raro ter mais de três.  
  
> [!NOTE]
>  Quando você adiciona as dimensões para uma matriz, o armazenamento total necessário para a matriz aumenta consideravelmente, então use matrizes multidimensionais com cuidado.  
  
## Usando diferentes dimensões  
 Suponha que você queira controlar quantidades de vendas para cada dia do mês presente.  Você pode declarar um matriz unidimensional com 31 elementos, um para cada dia do mês, como o exemplo a seguir mostra.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Agora suponha que você deseja controlar as mesmas informações não só para cada dia do mês mas também para cada mês do ano.  Você pode declarar uma matriz bidimensional com 12 linhas \(meses\) e 31 colunas \(para os dias\), como mostra o exemplo a seguir.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Agora suponha que você decidiu fazer sua matriz armazenar informações para mais de um ano.  Se você quiser controlar quantidades de vendas para 5 anos, você pode declarar uma matriz tridimensional com 5 camadas, 12 linhas e 31 colunas, como mostra a exemplo a seguir.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Observe que, porque cada índice varia de 0 para o seu máximo, cada dimensão da `salesAmounts` é declarado como um número menor que o comprimento necessário para essa dimensão.  Observe também que o tamanho da matriz aumenta com cada nova dimensão.  Os três tamanhos nos exemplos anteriores são 31, 372 e 1,860 elementos respectivamente.  
  
> [!NOTE]
>  Você pode criar uma matriz sem usar o `Dim` instrução ou o `New` cláusula.  Por exemplo, você pode chamar o método <xref:System.Array.CreateInstance%2A>, ou outro componente pode passar ao seu código uma matriz criada dessa maneira.  Essa matriz pode ter um limite inferior diferente de 0.  Você sempre pode testar o limite inferior de uma dimensão usando o <xref:System.Array.GetLowerBound%2A> método ou a `LBound` função.  
  
## Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)