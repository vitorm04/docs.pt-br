---
title: "Solucionando problemas de matrizes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "matrizes [Visual Basic], erros de compilação"
  - "matrizes [Visual Basic], erros de declaração"
  - "matrizes [Visual Basic], erros de inicialização"
  - "matrizes [Visual Basic], solucionando problemas"
  - "solucionando problemas de matrizes"
  - "solucionando problemas do Visual Basic, matrizes"
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas de matrizes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.  
  
## Erros de compilação declarar e inicializar uma matriz  
 Erros de compilação podem surgir de mal\-entendido das regras para declarar, criação e inicialização de matrizes.  As causas mais comuns de erros são as seguintes:  
  
-   Fornecendo um [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md) cláusula depois de especificar os comprimentos de dimensão na declaração da variável de matriz.  As linhas de código a seguir mostram declarações inválidas desse tipo.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   A especificação de comprimentos de dimensão por mais do que a matriz de nível superior de uma matriz denteada.  A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Omitindo o `New` palavra\-chave ao especificar os valores de elemento.  A linha de código a seguir mostra uma declaração inválida desse tipo.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Fornecendo um `New` cláusula sem chaves \(`{}`\).  As linhas de código a seguir mostram declarações inválidas desse tipo.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## Acessando uma matriz fora dos limites  
 O processo de inicialização de uma matriz atribui um limite superior e um limite inferior para cada dimensão.  Cada acesso a um elemento da matriz deve especificar um índice válido ou subscrito, para cada dimensão.  Se qualquer índice for abaixo seu limite inferior ou acima de seu limite superior, um <xref:System.IndexOutOfRangeException> resultados de exceção.  O compilador não pode detectar o erro, portanto, ocorrerá um erro em tempo de execução.  
  
### Determinação de limites  
 Se outro componente passar uma matriz em seu código, por exemplo como um argumento de procedimento, você não souber o tamanho dessa matriz ou comprimentos de suas dimensões.  Você sempre deve determinar o limite superior de cada dimensão de uma matriz, antes de tentar acessar quaisquer elementos.  Se a matriz foi criada por algum meio diferente de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`New` cláusula, o limite inferior pode ser algo diferente de 0 e é mais seguro determinar esse limite inferior também.  
  
### Especificando a dimensão  
 Ao determinar os limites de uma matriz multidimensional, tome cuidado como especificar a dimensão.  O `dimension` parâmetros da <xref:System.Array.GetLowerBound%2A> e <xref:System.Array.GetUpperBound%2A> métodos são baseados em 0, enquanto o `Rank` parâmetros da [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Information.LBound%2A> e <xref:Microsoft.VisualBasic.Information.UBound%2A> funções são baseados em 1.  
  
## Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)