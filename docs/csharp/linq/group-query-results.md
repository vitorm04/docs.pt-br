---
title: Agrupar resultados de consultas
description: Como agrupar resultados.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="f30d4-104">Agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="f30d4-104">Group query results</span></span>

<span data-ttu-id="f30d4-105">O agrupamento é um dos recursos mais poderosos do LINQ.</span><span class="sxs-lookup"><span data-stu-id="f30d4-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="f30d4-106">Os exemplos a seguir mostram como agrupar dados de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="f30d4-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="f30d4-107">Por uma única propriedade.</span><span class="sxs-lookup"><span data-stu-id="f30d4-107">By a single property.</span></span>  
  
-   <span data-ttu-id="f30d4-108">Pela primeira letra de uma propriedade de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f30d4-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="f30d4-109">Por um intervalo numérico calculado.</span><span class="sxs-lookup"><span data-stu-id="f30d4-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="f30d4-110">Por predicado booliano ou outra expressão.</span><span class="sxs-lookup"><span data-stu-id="f30d4-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="f30d4-111">Por uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="f30d4-111">By a compound key.</span></span>  
  
 <span data-ttu-id="f30d4-112">Além disso, as duas últimas consultas projetam seus resultados em um novo tipo anônimo que contém somente o primeiro nome e sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="f30d4-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="f30d4-113">Para obter mais informações, consulte a [cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f30d4-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f30d4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-114">Example</span></span>  
 <span data-ttu-id="f30d4-115">Todos os exemplos neste tópico usam as seguintes fontes de dados e classes auxiliares.</span><span class="sxs-lookup"><span data-stu-id="f30d4-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30d4-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-116">Example</span></span>  
 <span data-ttu-id="f30d4-117">O exemplo a seguir mostra como agrupar elementos de origem usando uma única propriedade do elemento como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="f30d4-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="f30d4-118">Nesse caso, a chave é uma `string`, o sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="f30d4-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="f30d4-119">Também é possível usar uma subcadeia para a chave.</span><span class="sxs-lookup"><span data-stu-id="f30d4-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="f30d4-120">A operação de agrupamento usa o comparador de igualdade padrão para o tipo.</span><span class="sxs-lookup"><span data-stu-id="f30d4-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="f30d4-121">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="f30d4-122">Altere a instrução de chamada no método `Main` para `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30d4-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-123">Example</span></span>  
 <span data-ttu-id="f30d4-124">O exemplo a seguir mostra como agrupar elementos de origem usando algo diferente de uma propriedade do objeto para a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="f30d4-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="f30d4-125">Neste exemplo, a chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="f30d4-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="f30d4-126">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="f30d4-127">Altere a instrução de chamada no método `Main` para `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30d4-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-128">Example</span></span>  
 <span data-ttu-id="f30d4-129">O exemplo a seguir mostra como agrupar elementos de origem usando um intervalo numérico como a chave de grupo.</span><span class="sxs-lookup"><span data-stu-id="f30d4-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="f30d4-130">Em seguida, a consulta, projeta os resultados em um tipo anônimo que contém apenas o nome e o sobrenome e o intervalo de percentil ao qual o aluno pertence.</span><span class="sxs-lookup"><span data-stu-id="f30d4-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="f30d4-131">Um tipo anônimo é usado porque não é necessário usar o objeto `Student` completo para exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="f30d4-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="f30d4-132">`GetPercentile` é uma função auxiliar que calcula um percentil com base na pontuação média do aluno.</span><span class="sxs-lookup"><span data-stu-id="f30d4-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="f30d4-133">O método retorna um número inteiro entre 0 e 10.</span><span class="sxs-lookup"><span data-stu-id="f30d4-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="f30d4-134">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="f30d4-135">Altere a instrução de chamada no método `Main` para `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30d4-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-136">Example</span></span>  
 <span data-ttu-id="f30d4-137">O exemplo a seguir mostra como agrupar elementos de origem usando uma expressão de comparação booliana.</span><span class="sxs-lookup"><span data-stu-id="f30d4-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="f30d4-138">Neste exemplo, a expressão booliana testa se a pontuação média de provas do aluno é maior que 75.</span><span class="sxs-lookup"><span data-stu-id="f30d4-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="f30d4-139">Como nos exemplos anteriores, os resultados são projetados em um tipo anônimo porque o elemento de origem completo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="f30d4-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="f30d4-140">Observe que as propriedades no tipo anônimo se tornam propriedades no membro `Key` e podem ser acessadas pelo nome quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="f30d4-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="f30d4-141">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="f30d4-142">Altere a instrução de chamada no método `Main` para `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30d4-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f30d4-143">Example</span></span>  
 <span data-ttu-id="f30d4-144">O exemplo a seguir mostra como usar um tipo anônimo para encapsular uma chave que contém vários valores.</span><span class="sxs-lookup"><span data-stu-id="f30d4-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="f30d4-145">Neste exemplo, o primeiro valor da chave é a primeira letra do sobrenome do aluno.</span><span class="sxs-lookup"><span data-stu-id="f30d4-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="f30d4-146">O segundo valor da chave é um booliano que especifica se o aluno tirou mais que 85 na primeira prova.</span><span class="sxs-lookup"><span data-stu-id="f30d4-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="f30d4-147">Você pode ordenar os grupos por qualquer propriedade na chave.</span><span class="sxs-lookup"><span data-stu-id="f30d4-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="f30d4-148">Cole o seguinte método na classe `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="f30d4-149">Altere a instrução de chamada no método `Main` para `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="f30d4-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f30d4-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f30d4-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="f30d4-151">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="f30d4-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="f30d4-152">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="f30d4-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="f30d4-153">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="f30d4-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="f30d4-154">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="f30d4-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="f30d4-155">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="f30d4-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="f30d4-156">Agrupando Dados</span><span class="sxs-lookup"><span data-stu-id="f30d4-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
