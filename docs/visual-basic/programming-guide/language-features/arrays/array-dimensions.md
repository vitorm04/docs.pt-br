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
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="3838f-102">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3838f-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="3838f-103">Um *dimensão* é uma direção na qual você pode variar a especificação de elementos uma matriz de.</span><span class="sxs-lookup"><span data-stu-id="3838f-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="3838f-104">Uma matriz que contém as vendas total para cada dia do mês tem uma dimensão (o dia do mês).</span><span class="sxs-lookup"><span data-stu-id="3838f-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="3838f-105">Uma matriz que contém as total de vendas por departamento para cada dia do mês tem duas dimensões (o número do departamento e o dia do mês).</span><span class="sxs-lookup"><span data-stu-id="3838f-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="3838f-106">O número de dimensões que tem uma matriz é chamado seu *classificação*.</span><span class="sxs-lookup"><span data-stu-id="3838f-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3838f-107">Você pode usar o <xref:System.Array.Rank%2A> propriedade para determinar quantas dimensões tem de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="3838f-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="3838f-108">Trabalhando com dimensões</span><span class="sxs-lookup"><span data-stu-id="3838f-108">Working with Dimensions</span></span>  
 <span data-ttu-id="3838f-109">Você especifica um elemento de uma matriz, fornecendo um *índice* ou *subscrito* para cada uma das suas dimensões.</span><span class="sxs-lookup"><span data-stu-id="3838f-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="3838f-110">Os elementos são contíguos ao longo de cada dimensão de índice 0 até o índice mais alto para essa dimensão.</span><span class="sxs-lookup"><span data-stu-id="3838f-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="3838f-111">As ilustrações a seguir mostram a estrutura conceitual de matrizes com diferentes classificações.</span><span class="sxs-lookup"><span data-stu-id="3838f-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="3838f-112">Cada elemento nas ilustrações mostra os valores de índice que acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="3838f-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="3838f-113">Por exemplo, você pode acessar o primeiro elemento da segunda linha da matriz bidimensional especificando índices `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="3838f-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="3838f-114">![Diagrama de gráfico de um &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="3838f-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="3838f-115">Matriz unidimensional</span><span class="sxs-lookup"><span data-stu-id="3838f-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="3838f-116">![Diagrama de gráfico de duas &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="3838f-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="3838f-117">matriz bidimensional</span><span class="sxs-lookup"><span data-stu-id="3838f-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="3838f-118">![Diagrama de gráfico de três &#45; matriz dimensional](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="3838f-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="3838f-119">matriz tridimensional</span><span class="sxs-lookup"><span data-stu-id="3838f-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="3838f-120">Uma dimensão</span><span class="sxs-lookup"><span data-stu-id="3838f-120">One Dimension</span></span>  
 <span data-ttu-id="3838f-121">Muitas matrizes possuem apenas uma dimensão, como o número de pessoas de cada idade.</span><span class="sxs-lookup"><span data-stu-id="3838f-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="3838f-122">O único requisito para especificar um elemento é a idade para a qual o elemento contém a contagem.</span><span class="sxs-lookup"><span data-stu-id="3838f-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="3838f-123">Portanto, essa matriz usa apenas um índice.</span><span class="sxs-lookup"><span data-stu-id="3838f-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="3838f-124">O exemplo a seguir declara uma variável para manter uma *matriz unidimensional* contagens de idade para idades de 0 a 120.</span><span class="sxs-lookup"><span data-stu-id="3838f-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="3838f-125">Duas dimensões</span><span class="sxs-lookup"><span data-stu-id="3838f-125">Two Dimensions</span></span>  
 <span data-ttu-id="3838f-126">Algumas matrizes possuem duas dimensões, como o número de escritórios em cada andar de cada prédio em um campus.</span><span class="sxs-lookup"><span data-stu-id="3838f-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="3838f-127">A especificação de um elemento requer o número de construção e o andar, e cada elemento contém a contagem para essa combinação de edifício e andar.</span><span class="sxs-lookup"><span data-stu-id="3838f-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="3838f-128">Portanto, essa matriz usa dois índices.</span><span class="sxs-lookup"><span data-stu-id="3838f-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="3838f-129">O exemplo a seguir declara uma variável para manter uma *matriz bidimensional* contagem de escritórios, de edifícios de 0 até 40 e Pisos de 0 a 5.</span><span class="sxs-lookup"><span data-stu-id="3838f-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="3838f-130">Uma matriz bidimensional também é chamada um *matriz retangular*.</span><span class="sxs-lookup"><span data-stu-id="3838f-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="3838f-131">Três dimensões</span><span class="sxs-lookup"><span data-stu-id="3838f-131">Three Dimensions</span></span>  
 <span data-ttu-id="3838f-132">Algumas matrizes possuem três dimensões, como valores em espaço tridimensional.</span><span class="sxs-lookup"><span data-stu-id="3838f-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="3838f-133">Essa matriz usa três índices, que nesse caso representam as coordenadas de z de espaço físico, x e y.</span><span class="sxs-lookup"><span data-stu-id="3838f-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="3838f-134">O exemplo a seguir declara uma variável para manter uma *matriz tridimensional* temperaturas do ar em vários pontos em um volume tridimensional.</span><span class="sxs-lookup"><span data-stu-id="3838f-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="3838f-135">Mais de três dimensões</span><span class="sxs-lookup"><span data-stu-id="3838f-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="3838f-136">Embora uma matriz pode ter até 32 dimensões, é raro ter mais de três.</span><span class="sxs-lookup"><span data-stu-id="3838f-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3838f-137">Quando você adiciona dimensões para uma matriz, o armazenamento total necessário para a matriz aumenta consideravelmente, então use matrizes multidimensionais com cuidado.</span><span class="sxs-lookup"><span data-stu-id="3838f-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="3838f-138">Usando dimensões diferentes</span><span class="sxs-lookup"><span data-stu-id="3838f-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="3838f-139">Suponha que você deseja controlar quantidades de vendas para cada dia do mês atual.</span><span class="sxs-lookup"><span data-stu-id="3838f-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="3838f-140">Você pode declarar uma matriz unidimensional com 31 elementos, um para cada dia do mês, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="3838f-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="3838f-141">Agora suponha que você deseja controlar as mesmas informações não só para cada dia do mês, mas também para cada mês do ano.</span><span class="sxs-lookup"><span data-stu-id="3838f-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="3838f-142">Você pode declarar uma matriz bidimensional com 12 linhas (meses) e 31 colunas (para os dias), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3838f-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="3838f-143">Agora suponha que você optar por ter sua matriz armazenar informações para mais de um ano.</span><span class="sxs-lookup"><span data-stu-id="3838f-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="3838f-144">Se você quiser controlar quantidades de vendas por cinco anos, você pode declarar uma matriz tridimensional com 5 camadas, 12 linhas e 31 colunas, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3838f-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="3838f-145">Observe que, como cada índice varia de 0 até seu máximo, cada dimensão de `salesAmounts` é declarada como menor que o comprimento necessário para a dimensão.</span><span class="sxs-lookup"><span data-stu-id="3838f-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="3838f-146">Observe também que o tamanho da matriz aumenta com cada nova dimensão.</span><span class="sxs-lookup"><span data-stu-id="3838f-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="3838f-147">Os três tamanhos nos exemplos anteriores são 31, 372 e 1,860 elementos respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3838f-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3838f-148">Você pode criar uma matriz sem usar o `Dim` instrução ou o `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="3838f-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="3838f-149">Por exemplo, você pode chamar o <xref:System.Array.CreateInstance%2A> método ou outro componente pode passar ao seu código uma matriz criada dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="3838f-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="3838f-150">Essa matriz pode ter um limite inferior diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="3838f-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="3838f-151">Você sempre pode testar o limite inferior de uma dimensão usando o <xref:System.Array.GetLowerBound%2A> método ou o `LBound` função.</span><span class="sxs-lookup"><span data-stu-id="3838f-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3838f-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3838f-152">See Also</span></span>  
 [<span data-ttu-id="3838f-153">Matrizes</span><span class="sxs-lookup"><span data-stu-id="3838f-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="3838f-154">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="3838f-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
