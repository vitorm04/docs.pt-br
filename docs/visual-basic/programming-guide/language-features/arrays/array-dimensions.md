---
title: Dimensões de matriz no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: bbc9e523e9b74cf380c65135e7416f1feba01a2e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512889"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="423f1-102">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="423f1-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="423f1-103">Uma *dimensão* é uma direção na qual você pode variar a especificação dos elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="423f1-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="423f1-104">Uma matriz que contém o total de vendas para cada dia do mês tem uma dimensão (o dia do mês).</span><span class="sxs-lookup"><span data-stu-id="423f1-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="423f1-105">Uma matriz que contém o total de vendas por departamento para cada dia do mês tem duas dimensões (o número do departamento e o dia do mês).</span><span class="sxs-lookup"><span data-stu-id="423f1-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="423f1-106">O número de dimensões que uma matriz tem é chamado de sua *classificação*.</span><span class="sxs-lookup"><span data-stu-id="423f1-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="423f1-107">Você pode usar a <xref:System.Array.Rank%2A> propriedade para determinar quantas dimensões uma matriz tem.</span><span class="sxs-lookup"><span data-stu-id="423f1-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="423f1-108">Trabalhando com dimensões</span><span class="sxs-lookup"><span data-stu-id="423f1-108">Working with Dimensions</span></span>

<span data-ttu-id="423f1-109">Você especifica um elemento de uma matriz fornecendo um *índice* ou *subscrito* para cada uma de suas dimensões.</span><span class="sxs-lookup"><span data-stu-id="423f1-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="423f1-110">Os elementos são contíguos ao longo de cada dimensão do índice 0 por meio do índice mais alto para essa dimensão.</span><span class="sxs-lookup"><span data-stu-id="423f1-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="423f1-111">As ilustrações a seguir mostram a estrutura conceitual de matrizes com classificações diferentes.</span><span class="sxs-lookup"><span data-stu-id="423f1-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="423f1-112">Cada elemento nas ilustrações mostra os valores de índice que o acessam.</span><span class="sxs-lookup"><span data-stu-id="423f1-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="423f1-113">Por exemplo, você pode acessar o primeiro elemento da segunda linha da matriz bidimensional especificando índices `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="423f1-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Diagrama que mostra uma matriz unidimensional.](./media/array-dimensions/one-dimensional-array.gif)

![Diagrama que mostra uma matriz bidimensional.](./media/array-dimensions/two-dimensional-array.gif)

![Diagrama que mostra uma matriz tridimensional.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="423f1-117">Uma dimensão</span><span class="sxs-lookup"><span data-stu-id="423f1-117">One Dimension</span></span>

<span data-ttu-id="423f1-118">Muitas matrizes têm apenas uma dimensão, como o número de pessoas de cada idade.</span><span class="sxs-lookup"><span data-stu-id="423f1-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="423f1-119">O único requisito para especificar um elemento é a idade para a qual o elemento contém a contagem.</span><span class="sxs-lookup"><span data-stu-id="423f1-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="423f1-120">Portanto, essa matriz usa apenas um índice.</span><span class="sxs-lookup"><span data-stu-id="423f1-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="423f1-121">O exemplo a seguir declara uma variável para manter uma *matriz* unidimensional de contagens de idade para idades de 0 a 120.</span><span class="sxs-lookup"><span data-stu-id="423f1-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="423f1-122">Duas dimensões</span><span class="sxs-lookup"><span data-stu-id="423f1-122">Two Dimensions</span></span>

<span data-ttu-id="423f1-123">Algumas matrizes têm duas dimensões, como o número de escritórios em cada andar de cada prédio em um campus.</span><span class="sxs-lookup"><span data-stu-id="423f1-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="423f1-124">A especificação de um elemento requer o número de edifício e o chão, e cada elemento contém a contagem para essa combinação de edifício e andar.</span><span class="sxs-lookup"><span data-stu-id="423f1-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="423f1-125">Portanto, tal matriz usa dois índices.</span><span class="sxs-lookup"><span data-stu-id="423f1-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="423f1-126">O exemplo a seguir declara uma variável para conter uma *matriz* bidimensional de contagens de escritórios, para edifícios de 0 a 40 e andares de 0 a 5.</span><span class="sxs-lookup"><span data-stu-id="423f1-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="423f1-127">Uma matriz bidimensional também é chamada de *matriz retangular*.</span><span class="sxs-lookup"><span data-stu-id="423f1-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="423f1-128">Três dimensões</span><span class="sxs-lookup"><span data-stu-id="423f1-128">Three Dimensions</span></span>

<span data-ttu-id="423f1-129">Algumas matrizes têm três dimensões, como valores em espaço tridimensional.</span><span class="sxs-lookup"><span data-stu-id="423f1-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="423f1-130">Essa matriz usa três índices, que, nesse caso, representam as coordenadas x, y e z do espaço físico.</span><span class="sxs-lookup"><span data-stu-id="423f1-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="423f1-131">O exemplo a seguir declara uma variável para conter uma *matriz* tridimensional de temperaturas de ar em vários pontos em um volume tridimensional.</span><span class="sxs-lookup"><span data-stu-id="423f1-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="423f1-132">Mais de três dimensões</span><span class="sxs-lookup"><span data-stu-id="423f1-132">More than Three Dimensions</span></span>

<span data-ttu-id="423f1-133">Embora uma matriz possa ter até 32 dimensões, é raro ter mais de três.</span><span class="sxs-lookup"><span data-stu-id="423f1-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="423f1-134">Quando você adiciona dimensões a uma matriz, o armazenamento total necessário para a matriz aumenta consideravelmente, portanto, use matrizes multidimensionais com cuidado.</span><span class="sxs-lookup"><span data-stu-id="423f1-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="423f1-135">Usando dimensões diferentes</span><span class="sxs-lookup"><span data-stu-id="423f1-135">Using Different Dimensions</span></span>

<span data-ttu-id="423f1-136">Suponha que você deseja acompanhar os valores de vendas de cada dia do mês atual.</span><span class="sxs-lookup"><span data-stu-id="423f1-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="423f1-137">Você pode declarar uma matriz unidimensional com 31 elementos, uma para cada dia do mês, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="423f1-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="423f1-138">Agora suponha que você deseja controlar as mesmas informações não apenas para todos os dias de um mês, mas também para todos os meses do ano.</span><span class="sxs-lookup"><span data-stu-id="423f1-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="423f1-139">Você pode declarar uma matriz bidimensional com 12 linhas (para os meses) e 31 colunas (por dias), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="423f1-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="423f1-140">Agora suponha que você decida que sua matriz contém informações por mais de um ano.</span><span class="sxs-lookup"><span data-stu-id="423f1-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="423f1-141">Se você quiser acompanhar os valores de vendas por 5 anos, poderá declarar uma matriz tridimensional com 5 camadas, 12 linhas e 31 colunas, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="423f1-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="423f1-142">Observe que, como cada índice varia de 0 até seu máximo, cada dimensão de `salesAmounts` é declarada como um valor menor que o comprimento necessário para essa dimensão.</span><span class="sxs-lookup"><span data-stu-id="423f1-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="423f1-143">Observe também que o tamanho da matriz aumenta com cada nova dimensão.</span><span class="sxs-lookup"><span data-stu-id="423f1-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="423f1-144">Os três tamanhos nos exemplos anteriores são 31, 372 e 1.860 elementos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="423f1-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="423f1-145">Você pode criar uma matriz sem usar a `Dim` instrução ou a `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="423f1-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="423f1-146">Por exemplo, você pode chamar o <xref:System.Array.CreateInstance%2A> método ou outro componente pode passar seu código uma matriz criada dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="423f1-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="423f1-147">Tal matriz pode ter um limite inferior diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="423f1-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="423f1-148">Você sempre pode testar o limite inferior de uma dimensão usando o <xref:System.Array.GetLowerBound%2A> método ou a `LBound` função.</span><span class="sxs-lookup"><span data-stu-id="423f1-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="423f1-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="423f1-149">See also</span></span>

- [<span data-ttu-id="423f1-150">Matrizes</span><span class="sxs-lookup"><span data-stu-id="423f1-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="423f1-151">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="423f1-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
