---
title: 'Como: combinar dados com LINQ usando junções'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344997"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="c7d22-102">Como combinar dados a LINQ com junções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7d22-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="c7d22-103">Visual Basic fornece as cláusulas de consulta `Join` e `Group Join` para permitir que você combine o conteúdo de várias coleções com base em valores comuns entre as coleções.</span><span class="sxs-lookup"><span data-stu-id="c7d22-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="c7d22-104">Esses valores são conhecidos como valores de *chave* .</span><span class="sxs-lookup"><span data-stu-id="c7d22-104">These values are known as *key* values.</span></span> <span data-ttu-id="c7d22-105">Os desenvolvedores familiarizados com conceitos de banco de dados relacional reconhecerão a cláusula `Join` como uma junção interna e a cláusula `Group Join` como, efetivamente, uma junção externa esquerda.</span><span class="sxs-lookup"><span data-stu-id="c7d22-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="c7d22-106">Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando as cláusulas de consulta `Join` e `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="c7d22-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="c7d22-107">Criar um projeto e adicionar dados de exemplo</span><span class="sxs-lookup"><span data-stu-id="c7d22-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="c7d22-108">Para criar um projeto que contém dados de exemplo e tipos</span><span class="sxs-lookup"><span data-stu-id="c7d22-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="c7d22-109">Para executar os exemplos neste tópico, abra o Visual Studio e adicione um novo projeto de aplicativo de console Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7d22-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="c7d22-110">Clique duas vezes no arquivo Module1. vb criado por Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7d22-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="c7d22-111">Os exemplos neste tópico usam os tipos `Person` e `Pet` e dados do exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7d22-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="c7d22-112">Copie esse código para o módulo de `Module1` padrão criado por Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c7d22-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="c7d22-113">Executar uma junção interna usando a cláusula JOIN</span><span class="sxs-lookup"><span data-stu-id="c7d22-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="c7d22-114">Uma junção interna combina dados de duas coleções.</span><span class="sxs-lookup"><span data-stu-id="c7d22-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="c7d22-115">Os itens para os quais os valores de chave especificados correspondem são incluídos.</span><span class="sxs-lookup"><span data-stu-id="c7d22-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="c7d22-116">Todos os itens de uma das coleções que não têm um item correspondente na outra coleção são excluídos.</span><span class="sxs-lookup"><span data-stu-id="c7d22-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="c7d22-117">No Visual Basic, o LINQ fornece duas opções para executar uma junção interna: uma junção implícita e uma junção explícita.</span><span class="sxs-lookup"><span data-stu-id="c7d22-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="c7d22-118">Uma junção implícita especifica as coleções a serem unidas em uma cláusula `From` e identifica os campos de chave correspondentes em uma cláusula `Where`.</span><span class="sxs-lookup"><span data-stu-id="c7d22-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="c7d22-119">Visual Basic une implicitamente as duas coleções com base nos campos de chave especificados.</span><span class="sxs-lookup"><span data-stu-id="c7d22-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="c7d22-120">Você pode especificar uma junção explícita usando a cláusula `Join` quando quiser ser específico sobre quais campos de chave usar na junção.</span><span class="sxs-lookup"><span data-stu-id="c7d22-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="c7d22-121">Nesse caso, uma cláusula `Where` ainda pode ser usada para filtrar os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="c7d22-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="c7d22-122">Para executar uma junção interna usando a cláusula JOIN</span><span class="sxs-lookup"><span data-stu-id="c7d22-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="c7d22-123">Adicione o código a seguir ao módulo `Module1` em seu projeto para ver exemplos de uma junção interna implícita e explícita.</span><span class="sxs-lookup"><span data-stu-id="c7d22-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="c7d22-124">Executar uma junção externa esquerda usando a cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="c7d22-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="c7d22-125">Uma junção externa esquerda inclui todos os itens da coleção do lado esquerdo da junção e apenas valores correspondentes da coleção do lado direito da junção.</span><span class="sxs-lookup"><span data-stu-id="c7d22-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="c7d22-126">Todos os itens da coleção do lado direito da junção que não têm um item correspondente na coleção do lado esquerdo são excluídos do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="c7d22-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="c7d22-127">A cláusula `Group Join` executa, na verdade, uma junção externa esquerda.</span><span class="sxs-lookup"><span data-stu-id="c7d22-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="c7d22-128">A diferença entre o que normalmente é conhecido como uma junção externa esquerda e o que a cláusula `Group Join` retorna é que a cláusula `Group Join` agrupa os resultados da coleção do lado direito da junção para cada item na coleção do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="c7d22-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="c7d22-129">Em um banco de dados relacional, uma junção externa esquerda retorna um resultado não agrupado no qual cada item no resultado da consulta contém itens correspondentes de ambas as coleções na junção.</span><span class="sxs-lookup"><span data-stu-id="c7d22-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="c7d22-130">Nesse caso, os itens da coleção do lado esquerdo da junção são repetidos para cada item correspondente da coleção do lado direito.</span><span class="sxs-lookup"><span data-stu-id="c7d22-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="c7d22-131">Você verá como isso se parece quando você conclui o próximo procedimento.</span><span class="sxs-lookup"><span data-stu-id="c7d22-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="c7d22-132">Você pode recuperar os resultados de uma consulta `Group Join` como um resultado não agrupado estendendo sua consulta para retornar um item para cada resultado de consulta agrupado.</span><span class="sxs-lookup"><span data-stu-id="c7d22-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="c7d22-133">Para fazer isso, você precisa garantir que você consulte o método `DefaultIfEmpty` da coleção agrupada.</span><span class="sxs-lookup"><span data-stu-id="c7d22-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="c7d22-134">Isso garante que os itens da coleção do lado esquerdo da junção ainda estejam incluídos no resultado da consulta, mesmo que não tenham resultados correspondentes da coleção do lado direito.</span><span class="sxs-lookup"><span data-stu-id="c7d22-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="c7d22-135">Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não houver nenhum valor correspondente da coleção do lado direito da junção.</span><span class="sxs-lookup"><span data-stu-id="c7d22-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="c7d22-136">Para executar uma junção externa esquerda usando a cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="c7d22-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="c7d22-137">Adicione o seguinte código ao módulo `Module1` em seu projeto para ver exemplos de uma junção externa agrupada à esquerda e uma junção externa esquerda desagrupada.</span><span class="sxs-lookup"><span data-stu-id="c7d22-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="c7d22-138">Executar uma junção usando uma chave composta</span><span class="sxs-lookup"><span data-stu-id="c7d22-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="c7d22-139">Você pode usar a palavra-chave `And` em uma cláusula `Join` ou `Group Join` para identificar vários campos de chave a serem usados ao corresponder valores das coleções que estão sendo Unidas.</span><span class="sxs-lookup"><span data-stu-id="c7d22-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="c7d22-140">A palavra-chave `And` especifica que todos os campos de chave especificados devem corresponder aos itens a serem ingressados.</span><span class="sxs-lookup"><span data-stu-id="c7d22-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="c7d22-141">Para executar uma junção usando uma chave composta</span><span class="sxs-lookup"><span data-stu-id="c7d22-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="c7d22-142">Adicione o código a seguir ao módulo `Module1` em seu projeto para ver exemplos de uma junção que usa uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="c7d22-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="c7d22-143">Executar o código</span><span class="sxs-lookup"><span data-stu-id="c7d22-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="c7d22-144">Para adicionar código para executar os exemplos</span><span class="sxs-lookup"><span data-stu-id="c7d22-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="c7d22-145">Substitua o `Sub Main` no módulo `Module1` em seu projeto pelo código a seguir para executar os exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="c7d22-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="c7d22-146">Pressione F5 para executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="c7d22-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d22-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7d22-147">See also</span></span>

- [<span data-ttu-id="c7d22-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="c7d22-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="c7d22-149">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7d22-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c7d22-150">Cláusula Join</span><span class="sxs-lookup"><span data-stu-id="c7d22-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="c7d22-151">Cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="c7d22-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="c7d22-152">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="c7d22-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c7d22-153">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="c7d22-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="c7d22-154">Consultas</span><span class="sxs-lookup"><span data-stu-id="c7d22-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c7d22-155">Transformações de dados com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="c7d22-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
