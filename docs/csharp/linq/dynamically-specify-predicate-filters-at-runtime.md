---
title: "Especificar filtros predicados dinamicamente em tempo de execução"
description: "Como especificar filtros predicados dinamicamente em tempo de execução."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="a7c1b-104">Especificar filtros predicados dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a7c1b-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="a7c1b-105">Em alguns casos você não sabe até o tempo de execução quantos predicados você precisa aplicar aos elementos de origem na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="a7c1b-106">Uma maneira de especificar dinamicamente vários filtros de predicados é usar o método <xref:System.Linq.Enumerable.Contains%2A>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="a7c1b-107">O exemplo é construído de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-107">The example is constructed in two ways.</span></span> <span data-ttu-id="a7c1b-108">Primeiro, o projeto é executado filtrando valores que são fornecidos no programa.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="a7c1b-109">Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="a7c1b-110">Para filtrar usando o método Contains</span><span class="sxs-lookup"><span data-stu-id="a7c1b-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="a7c1b-111">Abra um novo aplicativo de console e nomeie-o como `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="a7c1b-112">Copie a classe `StudentClass` de [Consultar uma coleção de objetos](query-a-collection-of-objects.md) e cole-a no namespace `PredicateFilters` sob a classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="a7c1b-113">`StudentClass` fornece uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="a7c1b-114">Comente o método `Main` em `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="a7c1b-115">Substitua a classe `Program` pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-115">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="a7c1b-116">Adicione a seguinte linha ao método `Main` na classe `DynamicPredicates`, sob a declaração de `ids`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-116">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="a7c1b-117">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-117">Run the project.</span></span>  
  
7.  <span data-ttu-id="a7c1b-118">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="a7c1b-118">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="a7c1b-119">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="a7c1b-119">Garcia: 114</span></span>  
  
     <span data-ttu-id="a7c1b-120">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="a7c1b-120">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="a7c1b-121">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="a7c1b-121">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="a7c1b-122">A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserida em tempo de execução em vez da matriz `ids`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-122">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="a7c1b-123">Altere `QueryByID(ids)` para `QueryByID(args)` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-123">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="a7c1b-124">Execute o projeto com os argumentos de linha de comando `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-124">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="a7c1b-125">Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro do método `Main`...</span><span class="sxs-lookup"><span data-stu-id="a7c1b-125">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="a7c1b-126">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="a7c1b-126">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="a7c1b-127">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="a7c1b-127">Adams: 120</span></span>  
  
     <span data-ttu-id="a7c1b-128">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="a7c1b-128">Feng: 117</span></span>  
  
     <span data-ttu-id="a7c1b-129">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="a7c1b-129">Garcia: 115</span></span>  
  
     <span data-ttu-id="a7c1b-130">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="a7c1b-130">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="a7c1b-131">Para filtrar usando uma instrução switch</span><span class="sxs-lookup"><span data-stu-id="a7c1b-131">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="a7c1b-132">Você pode usar uma instrução `switch` para selecionar entre consultas alternativas predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-132">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="a7c1b-133">No exemplo a seguir, `studentQuery` usa uma cláusula `where` diferente dependendo de qual nível de ensino ou ano, é especificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-133">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="a7c1b-134">Copie o método a seguir e cole-o na classe `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-134">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="a7c1b-135">No método `Main`, substitua a chamada para `QueryByID` pela chamada a seguir, que envia o primeiro elemento da matriz `args` como seu argumento: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-135">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="a7c1b-136">Execute o projeto com um argumento de linha de comando de um valor inteiro entre 1 e 4.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-136">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="a7c1b-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7c1b-137">See Also</span></span>  
 [<span data-ttu-id="a7c1b-138">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="a7c1b-138">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="a7c1b-139">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="a7c1b-139">where clause</span></span>](../language-reference/keywords/where-clause.md)
