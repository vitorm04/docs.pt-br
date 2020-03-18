---
title: Especificar dinamicamente filtros predicados em runtime (LINQ em C#)
description: Saiba como especificar dinamicamente filtros predicados em runtime usando o LINQ em C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659937"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="d8b7d-103">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="d8b7d-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="d8b7d-104">Em alguns casos, você não sabe até o tempo de execução quantos predicados precisa aplicar aos elementos de origem na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="d8b7d-105">Uma maneira de especificar dinamicamente vários filtros de predicados é usar o método <xref:System.Linq.Enumerable.Contains%2A>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="d8b7d-106">O exemplo é construído de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-106">The example is constructed in two ways.</span></span> <span data-ttu-id="d8b7d-107">Primeiro, o projeto é executado filtrando valores que são fornecidos no programa.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="d8b7d-108">Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="d8b7d-109">Para filtrar usando o método Contains</span><span class="sxs-lookup"><span data-stu-id="d8b7d-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="d8b7d-110">Abra um novo aplicativo de console e nomeie-o como `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="d8b7d-111">Copie a classe `StudentClass` de [Consultar uma coleção de objetos](query-a-collection-of-objects.md) e cole-a no namespace `PredicateFilters` sob a classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="d8b7d-112">`StudentClass` fornece uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="d8b7d-113">Comente o método `Main` em `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="d8b7d-114">Substitua a classe `Program` pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d8b7d-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="d8b7d-115">Adicione a seguinte linha ao método `Main` na classe `DynamicPredicates`, sob a declaração de `ids`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="d8b7d-116">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-116">Run the project.</span></span>

7. <span data-ttu-id="d8b7d-117">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="d8b7d-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="d8b7d-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="d8b7d-118">Garcia: 114</span></span>

     <span data-ttu-id="d8b7d-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="d8b7d-119">O'Donnell: 112</span></span>

     <span data-ttu-id="d8b7d-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="d8b7d-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="d8b7d-121">A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserida em tempo de execução em vez da matriz `ids`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="d8b7d-122">Altere `QueryByID(ids)` para `QueryByID(args)` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="d8b7d-123">Execute o projeto com os argumentos de linha de comando `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="d8b7d-124">Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="d8b7d-125">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="d8b7d-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="d8b7d-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="d8b7d-126">Adams: 120</span></span>

     <span data-ttu-id="d8b7d-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="d8b7d-127">Feng: 117</span></span>

     <span data-ttu-id="d8b7d-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="d8b7d-128">Garcia: 115</span></span>

     <span data-ttu-id="d8b7d-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="d8b7d-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="d8b7d-130">Para filtrar usando uma instrução switch</span><span class="sxs-lookup"><span data-stu-id="d8b7d-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="d8b7d-131">Você pode usar uma instrução `switch` para selecionar entre consultas alternativas predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="d8b7d-132">No exemplo a seguir, `studentQuery` usa uma cláusula `where` diferente dependendo de qual nível de ensino ou ano, é especificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="d8b7d-133">Copie o método a seguir e cole-o na classe `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="d8b7d-134">No método `Main`, substitua a chamada para `QueryByID` pela chamada a seguir, que envia o primeiro elemento da matriz `args` como seu argumento: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="d8b7d-135">Execute o projeto com um argumento de linha de comando de um valor inteiro entre 1 e 4.</span><span class="sxs-lookup"><span data-stu-id="d8b7d-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8b7d-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8b7d-136">See also</span></span>

- [<span data-ttu-id="d8b7d-137">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d8b7d-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d8b7d-138">onde cláusula</span><span class="sxs-lookup"><span data-stu-id="d8b7d-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
