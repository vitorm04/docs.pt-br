---
title: Solução de problemas de matrizes
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: e633c5a00693f188270b1610abaf2decb656b00a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414589"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="78800-102">Solucionando problemas de matrizes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78800-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="78800-103">Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com matrizes.</span><span class="sxs-lookup"><span data-stu-id="78800-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="78800-104">Erros de compilação declarando e inicializando uma matriz</span><span class="sxs-lookup"><span data-stu-id="78800-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="78800-105">Os erros de compilação podem surgir de mal-entendido das regras para declarar, criar e inicializar matrizes.</span><span class="sxs-lookup"><span data-stu-id="78800-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="78800-106">As causas mais comuns de erros são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="78800-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="78800-107">Fornecendo uma [nova cláusula Operator](../../../language-reference/operators/new-operator.md) depois de especificar comprimentos de dimensão na declaração de variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="78800-107">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="78800-108">As linhas de código a seguir mostram declarações inválidas desse tipo.</span><span class="sxs-lookup"><span data-stu-id="78800-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="78800-109">Especificando comprimentos de dimensão para mais do que a matriz de nível superior de uma matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="78800-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="78800-110">A linha de código a seguir mostra uma declaração inválida desse tipo.</span><span class="sxs-lookup"><span data-stu-id="78800-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="78800-111">Omitindo a `New` palavra-chave ao especificar os valores do elemento.</span><span class="sxs-lookup"><span data-stu-id="78800-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="78800-112">A linha de código a seguir mostra uma declaração inválida desse tipo.</span><span class="sxs-lookup"><span data-stu-id="78800-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="78800-113">Fornecendo uma `New` cláusula sem chaves ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="78800-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="78800-114">As linhas de código a seguir mostram declarações inválidas desse tipo.</span><span class="sxs-lookup"><span data-stu-id="78800-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="78800-115">Acessando uma matriz fora dos limites</span><span class="sxs-lookup"><span data-stu-id="78800-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="78800-116">O processo de inicializar uma matriz atribui um limite superior e um limite inferior a cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="78800-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="78800-117">Cada acesso a um elemento da matriz deve especificar um índice válido, ou subscrito, para cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="78800-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="78800-118">Se qualquer índice estiver abaixo de seu limite inferior ou acima de seu limite superior, <xref:System.IndexOutOfRangeException> ocorrerá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="78800-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="78800-119">O compilador não pode detectar esse erro, portanto, um erro ocorre em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="78800-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="78800-120">Determinando limites</span><span class="sxs-lookup"><span data-stu-id="78800-120">Determining Bounds</span></span>  
 <span data-ttu-id="78800-121">Se outro componente passar uma matriz para seu código, por exemplo, como um argumento de procedimento, você não saberá o tamanho dessa matriz ou os comprimentos de suas dimensões.</span><span class="sxs-lookup"><span data-stu-id="78800-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="78800-122">Você sempre deve determinar o limite superior para cada dimensão de uma matriz antes de tentar acessar quaisquer elementos.</span><span class="sxs-lookup"><span data-stu-id="78800-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="78800-123">Se a matriz tiver sido criada por alguns meios diferentes de uma `New` cláusula Visual Basic, o limite inferior poderá ser algo diferente de 0, e será mais seguro determinar o limite inferior também.</span><span class="sxs-lookup"><span data-stu-id="78800-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="78800-124">Especificando a dimensão</span><span class="sxs-lookup"><span data-stu-id="78800-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="78800-125">Ao determinar os limites de uma matriz multidimensional, tome cuidado com o modo de especificar a dimensão.</span><span class="sxs-lookup"><span data-stu-id="78800-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="78800-126">Os `dimension` parâmetros dos <xref:System.Array.GetLowerBound%2A> métodos e <xref:System.Array.GetUpperBound%2A> são baseados em 0, enquanto os `Rank` parâmetros da Visual Basic e das <xref:Microsoft.VisualBasic.Information.LBound%2A> <xref:Microsoft.VisualBasic.Information.UBound%2A> funções são baseados em 1.</span><span class="sxs-lookup"><span data-stu-id="78800-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78800-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="78800-127">See also</span></span>

- [<span data-ttu-id="78800-128">Matrizes</span><span class="sxs-lookup"><span data-stu-id="78800-128">Arrays</span></span>](index.md)
- [<span data-ttu-id="78800-129">Como inicializar uma variável de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78800-129">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)
