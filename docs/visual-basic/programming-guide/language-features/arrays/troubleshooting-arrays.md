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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 571731ae7066ba7ec52d4a2413b4d948f3f35bfe
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="96209-102">Solucionando problemas de matrizes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96209-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="96209-103">Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.</span><span class="sxs-lookup"><span data-stu-id="96209-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="96209-104">Erros de compilação declarar e inicializar uma matriz</span><span class="sxs-lookup"><span data-stu-id="96209-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="96209-105">Erros de compilação podem surgir de compreensão das regras para declarar, criando e inicializando matrizes.</span><span class="sxs-lookup"><span data-stu-id="96209-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="96209-106">As causas mais comuns de erros são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="96209-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="96209-107">Fornecendo uma [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) cláusula após especificar os comprimentos de dimensão na declaração da variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="96209-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="96209-108">As seguintes linhas de código mostram inválidas declarações desse tipo.</span><span class="sxs-lookup"><span data-stu-id="96209-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="96209-109">Especificar tamanhos de dimensão para mais do que a matriz de nível superior de uma matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="96209-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="96209-110">A linha de código a seguir mostra uma declaração inválida desse tipo.</span><span class="sxs-lookup"><span data-stu-id="96209-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="96209-111">Omitindo o `New` palavra-chave ao especificar os valores de elemento.</span><span class="sxs-lookup"><span data-stu-id="96209-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="96209-112">A linha de código a seguir mostra uma declaração inválida desse tipo.</span><span class="sxs-lookup"><span data-stu-id="96209-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="96209-113">Fornecendo uma `New` cláusula sem chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="96209-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="96209-114">As seguintes linhas de código mostram inválidas declarações desse tipo.</span><span class="sxs-lookup"><span data-stu-id="96209-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="96209-115">Acessar uma matriz fora dos limites</span><span class="sxs-lookup"><span data-stu-id="96209-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="96209-116">O processo de inicializar uma matriz atribui um limite superior e um limite inferior de cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="96209-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="96209-117">Cada acesso a um elemento da matriz deve especificar um índice válido ou subscrição, para cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="96209-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="96209-118">Se qualquer índice estiver abaixo de seu limite inferior ou acima de seu limite superior, um <xref:System.IndexOutOfRangeException>resultados de exceção.</xref:System.IndexOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="96209-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="96209-119">O compilador não pode detectar um erro, para que ocorra um erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="96209-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="96209-120">Determinando limites</span><span class="sxs-lookup"><span data-stu-id="96209-120">Determining Bounds</span></span>  
 <span data-ttu-id="96209-121">Se outro componente passar uma matriz para o seu código, por exemplo como um argumento de procedimento, você não souber o tamanho da matriz ou os comprimentos das suas dimensões.</span><span class="sxs-lookup"><span data-stu-id="96209-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="96209-122">Você sempre deve determinar o limite superior de cada dimensão de uma matriz antes de tentar acessar quaisquer elementos.</span><span class="sxs-lookup"><span data-stu-id="96209-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="96209-123">Se a matriz foi criada por alguns meios diferente de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` cláusula, o limite inferior pode ser algo diferente de 0, e é mais seguro determinar esse limite inferior também.</span><span class="sxs-lookup"><span data-stu-id="96209-123">If the array has been created by some means other than a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="96209-124">Especificar a dimensão</span><span class="sxs-lookup"><span data-stu-id="96209-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="96209-125">Ao determinar os limites de uma matriz multidimensional, tome cuidado como especificar a dimensão.</span><span class="sxs-lookup"><span data-stu-id="96209-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="96209-126">O `dimension` parâmetros da <xref:System.Array.GetLowerBound%2A>e <xref:System.Array.GetUpperBound%2A>métodos são baseadas em 0, enquanto o `Rank` parâmetros do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>e <xref:Microsoft.VisualBasic.Information.UBound%2A>funções são baseados em 1.</xref:Microsoft.VisualBasic.Information.UBound%2A> </xref:Microsoft.VisualBasic.Information.LBound%2A> </xref:System.Array.GetUpperBound%2A> </xref:System.Array.GetLowerBound%2A></span><span class="sxs-lookup"><span data-stu-id="96209-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96209-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96209-127">See Also</span></span>  
 <span data-ttu-id="96209-128">[Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="96209-128">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="96209-129"> [Como: inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="96209-129"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
