---
title: "Especificar filtros predicados dinamicamente em tempo de execução"
description: "Como especificar filtros predicados dinamicamente em tempo de execução."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e724428bce09e2b2fa20b9391ad131424e16413
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="b6112-104">Especificar filtros predicados dinamicamente em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b6112-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="b6112-105">Em alguns casos você não sabe até o tempo de execução quantos predicados você precisa aplicar aos elementos de origem na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="b6112-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="b6112-106">Uma maneira de especificar dinamicamente vários filtros de predicados é usar o método <xref:System.Linq.Enumerable.Contains%2A>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6112-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="b6112-107">O exemplo é construído de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="b6112-107">The example is constructed in two ways.</span></span> <span data-ttu-id="b6112-108">Primeiro, o projeto é executado filtrando valores que são fornecidos no programa.</span><span class="sxs-lookup"><span data-stu-id="b6112-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="b6112-109">Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b6112-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="b6112-110">Para filtrar usando o método Contains</span><span class="sxs-lookup"><span data-stu-id="b6112-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="b6112-111">Abra um novo aplicativo de console e nomeie-o como `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="b6112-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="b6112-112">Copie a classe `StudentClass` de [Consultar uma coleção de objetos](query-a-collection-of-objects.md) e cole-a no namespace `PredicateFilters` sob a classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="b6112-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="b6112-113">`StudentClass` fornece uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="b6112-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="b6112-114">Comente o método `Main` em `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="b6112-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="b6112-115">Substitua a classe `Program` pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6112-115">Replace class `Program` with the following code.</span></span>  
  
     <span data-ttu-id="b6112-116">[!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6112-116">[!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]</span></span>  
  
5.  <span data-ttu-id="b6112-117">Adicione a seguinte linha ao método `Main` na classe `DynamicPredicates`, sob a declaração de `ids`.</span><span class="sxs-lookup"><span data-stu-id="b6112-117">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="b6112-118">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="b6112-118">Run the project.</span></span>  
  
7.  <span data-ttu-id="b6112-119">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="b6112-119">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="b6112-120">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="b6112-120">Garcia: 114</span></span>  
  
     <span data-ttu-id="b6112-121">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="b6112-121">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="b6112-122">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="b6112-122">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="b6112-123">A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserida em tempo de execução em vez da matriz `ids`.</span><span class="sxs-lookup"><span data-stu-id="b6112-123">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="b6112-124">Altere `QueryByID(ids)` para `QueryByID(args)` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="b6112-124">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="b6112-125">Execute o projeto com os argumentos de linha de comando `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="b6112-125">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="b6112-126">Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro do método `Main`...</span><span class="sxs-lookup"><span data-stu-id="b6112-126">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="b6112-127">A saída a seguir é exibida em uma janela do console:</span><span class="sxs-lookup"><span data-stu-id="b6112-127">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="b6112-128">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="b6112-128">Adams: 120</span></span>  
  
     <span data-ttu-id="b6112-129">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="b6112-129">Feng: 117</span></span>  
  
     <span data-ttu-id="b6112-130">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="b6112-130">Garcia: 115</span></span>  
  
     <span data-ttu-id="b6112-131">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="b6112-131">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="b6112-132">Para filtrar usando uma instrução switch</span><span class="sxs-lookup"><span data-stu-id="b6112-132">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="b6112-133">Você pode usar uma instrução `switch` para selecionar entre consultas alternativas predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="b6112-133">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="b6112-134">No exemplo a seguir, `studentQuery` usa uma cláusula `where` diferente dependendo de qual nível de ensino ou ano, é especificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b6112-134">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="b6112-135">Copie o método a seguir e cole-o na classe `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="b6112-135">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     <span data-ttu-id="b6112-136">[!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6112-136">[!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]</span></span>  
  
3.  <span data-ttu-id="b6112-137">No método `Main`, substitua a chamada para `QueryByID` pela chamada a seguir, que envia o primeiro elemento da matriz `args` como seu argumento: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="b6112-137">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="b6112-138">Execute o projeto com um argumento de linha de comando de um valor inteiro entre 1 e 4.</span><span class="sxs-lookup"><span data-stu-id="b6112-138">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="b6112-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6112-139">See Also</span></span>  
 <span data-ttu-id="b6112-140">[Expressões de Consulta LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="b6112-140">[LINQ Query Expressions](index.md) </span></span>  
 [<span data-ttu-id="b6112-141">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="b6112-141">where clause</span></span>](../language-reference/keywords/where-clause.md)

