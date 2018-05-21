---
title: Agrupar resultados de consultas
description: Como agrupar resultados.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: cb7808bfdd86dd23882d0722b87b1e013a84141e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="group-query-results"></a><span data-ttu-id="c39f1-103">Agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="c39f1-103">Group query results</span></span>

<span data-ttu-id="c39f1-104">O agrupamento é um dos recursos mais poderosos do LINQ.</span><span class="sxs-lookup"><span data-stu-id="c39f1-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="c39f1-105">Os exemplos a seguir mostram como agrupar dados de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="c39f1-105">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="c39f1-106">Por uma única propriedade.</span><span class="sxs-lookup"><span data-stu-id="c39f1-106">By a single property.</span></span>  
  
-   <span data-ttu-id="c39f1-107">Pela primeira letra de uma propriedade de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c39f1-107">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="c39f1-108">Por um intervalo numérico calculado.</span><span class="sxs-lookup"><span data-stu-id="c39f1-108">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="c39f1-109">Por predicado booliano ou outra expressão.</span><span class="sxs-lookup"><span data-stu-id="c39f1-109">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="c39f1-110">Por uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="c39f1-110">By a compound key.</span></span>  
  
 <span data-ttu-id="c39f1-111">Além disso, as duas últimas consultas projetam seus resultados em um novo tipo anônimo que contém somente o primeiro nome e sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c39f1-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="c39f1-112">Para obter mais informações, consulte a [cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c39f1-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c39f1-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-113">Example</span></span>  
 <span data-ttu-id="c39f1-114">Todos os exemplos neste tópico usam as seguintes fontes de dados e classes auxiliares.</span><span class="sxs-lookup"><span data-stu-id="c39f1-114">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c39f1-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-115">Example</span></span>  
 <span data-ttu-id="c39f1-116">O exemplo a seguir mostra como agrupar elementos de origem usando uma única propriedade do elemento como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c39f1-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="c39f1-117">Nesse caso, a chave é uma `string`, o sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c39f1-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="c39f1-118">Também é possível usar uma subcadeia para a chave.</span><span class="sxs-lookup"><span data-stu-id="c39f1-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="c39f1-119">A operação de agrupamento usa o comparador de igualdade padrão para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c39f1-119">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="c39f1-120">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c39f1-121">Altere a instrução de chamada no método `Main` para `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="c39f1-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-122">Example</span></span>  
 <span data-ttu-id="c39f1-123">O exemplo a seguir mostra como agrupar elementos de origem usando algo diferente de uma propriedade do objeto para a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c39f1-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="c39f1-124">Neste exemplo, a chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c39f1-124">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="c39f1-125">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c39f1-126">Altere a instrução de chamada no método `Main` para `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="c39f1-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-127">Example</span></span>  
 <span data-ttu-id="c39f1-128">O exemplo a seguir mostra como agrupar elementos de origem usando um intervalo numérico como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="c39f1-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="c39f1-129">Em seguida, a consulta, projeta os resultados em um tipo anônimo que contém apenas o nome e o sobrenome e o intervalo de percentil ao qual o aluno pertence.</span><span class="sxs-lookup"><span data-stu-id="c39f1-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="c39f1-130">Um tipo anônimo é usado porque não é necessário usar o objeto `Student` completo para exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="c39f1-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="c39f1-131">`GetPercentile` é uma função auxiliar que calcula um percentil com base na pontuação média do aluno.</span><span class="sxs-lookup"><span data-stu-id="c39f1-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="c39f1-132">O método retorna um número inteiro entre 0 e 10.</span><span class="sxs-lookup"><span data-stu-id="c39f1-132">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="c39f1-133">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c39f1-134">Altere a instrução de chamada no método `Main` para `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="c39f1-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-135">Example</span></span>  
 <span data-ttu-id="c39f1-136">O exemplo a seguir mostra como agrupar elementos de origem usando uma expressão de comparação booliana.</span><span class="sxs-lookup"><span data-stu-id="c39f1-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="c39f1-137">Neste exemplo, a expressão booliana testa se a pontuação média de provas do aluno é maior que 75.</span><span class="sxs-lookup"><span data-stu-id="c39f1-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="c39f1-138">Como nos exemplos anteriores, os resultados são projetados em um tipo anônimo porque o elemento de origem completo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="c39f1-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="c39f1-139">Observe que as propriedades no tipo anônimo se tornam propriedades no membro `Key` e podem ser acessadas pelo nome quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="c39f1-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="c39f1-140">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c39f1-141">Altere a instrução de chamada no método `Main` para `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="c39f1-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c39f1-142">Example</span></span>  
 <span data-ttu-id="c39f1-143">O exemplo a seguir mostra como usar um tipo anônimo para encapsular uma chave que contém vários valores.</span><span class="sxs-lookup"><span data-stu-id="c39f1-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="c39f1-144">Neste exemplo, o primeiro valor da chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="c39f1-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="c39f1-145">O segundo valor da chave é um booliano que especifica se o aluno tirou mais que 85 na primeira prova.</span><span class="sxs-lookup"><span data-stu-id="c39f1-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="c39f1-146">Você pode ordenar os grupos por qualquer propriedade na chave.</span><span class="sxs-lookup"><span data-stu-id="c39f1-146">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="c39f1-147">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c39f1-148">Altere a instrução de chamada no método `Main` para `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="c39f1-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c39f1-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c39f1-149">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="c39f1-150">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="c39f1-150">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="c39f1-151">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="c39f1-151">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="c39f1-152">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="c39f1-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="c39f1-153">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="c39f1-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="c39f1-154">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="c39f1-154">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="c39f1-155">Agrupando Dados</span><span class="sxs-lookup"><span data-stu-id="c39f1-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
