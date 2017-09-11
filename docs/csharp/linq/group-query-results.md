---
title: Agrupar resultados de consultas
description: Como agrupar resultados.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1c1639651699afbe5fb768db26b98a9b2d734315
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="group-query-results"></a><span data-ttu-id="c612d-104">Agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="c612d-104">Group query results</span></span>

<span data-ttu-id="c612d-105">O agrupamento é um dos recursos mais poderosos do LINQ.</span><span class="sxs-lookup"><span data-stu-id="c612d-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="c612d-106">Os exemplos a seguir mostram como agrupar dados de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="c612d-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="c612d-107">Por uma única propriedade.</span><span class="sxs-lookup"><span data-stu-id="c612d-107">By a single property.</span></span>  
  
-   <span data-ttu-id="c612d-108">Pela primeira letra de uma propriedade de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c612d-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="c612d-109">Por um intervalo numérico calculado.</span><span class="sxs-lookup"><span data-stu-id="c612d-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="c612d-110">Por predicado booliano ou outra expressão.</span><span class="sxs-lookup"><span data-stu-id="c612d-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="c612d-111">Por uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="c612d-111">By a compound key.</span></span>  
  
 <span data-ttu-id="c612d-112">Além disso, as duas últimas consultas projetam seus resultados em um novo tipo anônimo que contém somente o primeiro nome e sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c612d-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="c612d-113">Para obter mais informações, consulte a [cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c612d-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-114">Example</span></span>  
 <span data-ttu-id="c612d-115">Todos os exemplos neste tópico usam as seguintes fontes de dados e classes auxiliares.</span><span class="sxs-lookup"><span data-stu-id="c612d-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 <span data-ttu-id="c612d-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-116">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-117">Example</span></span>  
 <span data-ttu-id="c612d-118">O exemplo a seguir mostra como agrupar elementos de origem usando uma única propriedade do elemento como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c612d-118">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="c612d-119">Nesse caso, a chave é uma `string`, o sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c612d-119">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="c612d-120">Também é possível usar uma subcadeia para a chave.</span><span class="sxs-lookup"><span data-stu-id="c612d-120">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="c612d-121">A operação de agrupamento usa o comparador de igualdade padrão para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c612d-121">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="c612d-122">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c612d-122">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c612d-123">Altere a instrução de chamada no método `Main` para `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="c612d-123">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 <span data-ttu-id="c612d-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-124">[!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-125">Example</span></span>  
 <span data-ttu-id="c612d-126">O exemplo a seguir mostra como agrupar elementos de origem usando algo diferente de uma propriedade do objeto para a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c612d-126">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="c612d-127">Neste exemplo, a chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c612d-127">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="c612d-128">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c612d-128">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c612d-129">Altere a instrução de chamada no método `Main` para `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="c612d-129">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 <span data-ttu-id="c612d-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-130">[!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-131">Example</span></span>  
 <span data-ttu-id="c612d-132">O exemplo a seguir mostra como agrupar elementos de origem usando um intervalo numérico como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c612d-132">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="c612d-133">Em seguida, a consulta, projeta os resultados em um tipo anônimo que contém apenas o nome e o sobrenome e o intervalo de percentil ao qual o aluno pertence.</span><span class="sxs-lookup"><span data-stu-id="c612d-133">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="c612d-134">Um tipo anônimo é usado porque não é necessário usar o objeto `Student` completo para exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="c612d-134">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="c612d-135">`GetPercentile` é uma função auxiliar que calcula um percentil com base na pontuação média do aluno.</span><span class="sxs-lookup"><span data-stu-id="c612d-135">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="c612d-136">O método retorna um número inteiro entre 0 e 10.</span><span class="sxs-lookup"><span data-stu-id="c612d-136">The method returns an integer between 0 and 10.</span></span>  
  
 <span data-ttu-id="c612d-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-137">[!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]</span></span>  
  
 <span data-ttu-id="c612d-138">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c612d-138">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c612d-139">Altere a instrução de chamada no método `Main` para `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="c612d-139">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 <span data-ttu-id="c612d-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-140">[!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-141">Example</span></span>  
 <span data-ttu-id="c612d-142">O exemplo a seguir mostra como agrupar elementos de origem usando uma expressão de comparação booliana.</span><span class="sxs-lookup"><span data-stu-id="c612d-142">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="c612d-143">Neste exemplo, a expressão booliana testa se a pontuação média de provas do aluno é maior que 75.</span><span class="sxs-lookup"><span data-stu-id="c612d-143">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="c612d-144">Como nos exemplos anteriores, os resultados são projetados em um tipo anônimo porque o elemento de origem completo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="c612d-144">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="c612d-145">Observe que as propriedades no tipo anônimo se tornam propriedades no membro `Key` e podem ser acessadas pelo nome quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="c612d-145">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="c612d-146">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c612d-146">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c612d-147">Altere a instrução de chamada no método `Main` para `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="c612d-147">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 <span data-ttu-id="c612d-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-148">[!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c612d-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c612d-149">Example</span></span>  
 <span data-ttu-id="c612d-150">O exemplo a seguir mostra como usar um tipo anônimo para encapsular uma chave que contém vários valores.</span><span class="sxs-lookup"><span data-stu-id="c612d-150">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="c612d-151">Neste exemplo, o primeiro valor da chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c612d-151">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="c612d-152">O segundo valor da chave é um booliano que especifica se o aluno tirou mais que 85 na primeira prova.</span><span class="sxs-lookup"><span data-stu-id="c612d-152">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="c612d-153">Você pode ordenar os grupos por qualquer propriedade na chave.</span><span class="sxs-lookup"><span data-stu-id="c612d-153">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="c612d-154">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c612d-154">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c612d-155">Altere a instrução de chamada no método `Main` para `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="c612d-155">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 <span data-ttu-id="c612d-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="c612d-156">[!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c612d-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c612d-157">See also</span></span>  
 <span data-ttu-id="c612d-158"><xref:System.Linq.Enumerable.GroupBy%2A></span><span class="sxs-lookup"><span data-stu-id="c612d-158"><xref:System.Linq.Enumerable.GroupBy%2A></span></span>   
 <span data-ttu-id="c612d-159"><xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="c612d-159"><xref:System.Linq.IGrouping%602></span></span>   
 <span data-ttu-id="c612d-160">[Expressões de Consulta LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="c612d-160">[LINQ Query Expressions](index.md) </span></span>  
 <span data-ttu-id="c612d-161">[Cláusula group](../language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c612d-161">[group clause](../language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="c612d-162">[Tipos Anônimos](../programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="c612d-162">[Anonymous Types](../programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="c612d-163">[Executar uma Subconsulta em uma Operação de Agrupamento](perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="c612d-163">[Perform a Subquery on a Grouping Operation](perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 <span data-ttu-id="c612d-164">[Criar um Grupo Aninhado](create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="c612d-164">[Create a Nested Group](create-a-nested-group.md) </span></span>  
 [<span data-ttu-id="c612d-165">Agrupando Dados</span><span class="sxs-lookup"><span data-stu-id="c612d-165">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)

