---
title: "Como: combinar dados com LINQ com junções (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fa63f7f1a0c5e2c77cb6a195082e1ade9e69c1f0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="01297-102">Como combinar dados a LINQ com junções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01297-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="01297-103">O Visual Basic fornece o `Join` e `Group Join` cláusulas para que você possa combinar o conteúdo de várias coleções com base em valores comuns entre as coleções de consulta.</span><span class="sxs-lookup"><span data-stu-id="01297-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="01297-104">Esses valores são conhecidos como *chave* valores.</span><span class="sxs-lookup"><span data-stu-id="01297-104">These values are known as *key* values.</span></span> <span data-ttu-id="01297-105">Os desenvolvedores familiarizados com os conceitos de banco de dados relacional reconhecerá o `Join` cláusula como um INNER JOIN e o `Group Join` cláusula como efetivamente, um LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="01297-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="01297-106">Os exemplos neste tópico demonstram algumas maneiras de combinar dados usando o `Join` e `Group Join` cláusulas de consulta.</span><span class="sxs-lookup"><span data-stu-id="01297-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="01297-107">Criar um projeto e adicione dados de exemplo</span><span class="sxs-lookup"><span data-stu-id="01297-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="01297-108">Para criar um projeto que contém dados de exemplo e tipos</span><span class="sxs-lookup"><span data-stu-id="01297-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="01297-109">Para executar os exemplos neste tópico, abra o Visual Studio e adicione um novo projeto de aplicativo de Console do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01297-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="01297-110">Clique duas vezes no arquivo Module1 vb criado pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01297-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="01297-111">Os exemplos neste tópico usam o `Person` e `Pet` tipos e dados do exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01297-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="01297-112">Copie este código para o padrão `Module1` módulo criado pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01297-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     <span data-ttu-id="01297-113">[!code-vb[VbLINQHowTos n º&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-113">[!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]</span></span>  
    <span data-ttu-id="01297-114">[!code-vb[VbLINQHowTos n º&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-114">[!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]</span></span>  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="01297-115">Faça uma Inner Join usando a cláusula Join.</span><span class="sxs-lookup"><span data-stu-id="01297-115">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="01297-116">Uma INNER JOIN combina dados de duas coleções.</span><span class="sxs-lookup"><span data-stu-id="01297-116">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="01297-117">Itens para os quais correspondem aos valores de chave especificados estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="01297-117">Items for which the specified key values match are included.</span></span> <span data-ttu-id="01297-118">Todos os itens de qualquer coleção que não têm um item correspondente na outra coleção são excluídos.</span><span class="sxs-lookup"><span data-stu-id="01297-118">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="01297-119">No Visual Basic, LINQ fornece duas opções para executar uma INNER JOIN: um join implícito e um join explícito.</span><span class="sxs-lookup"><span data-stu-id="01297-119">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="01297-120">Um join implícito especifica as coleções a serem unidas um `From` cláusula e identifica os campos-chave correspondentes em uma `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="01297-120">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="01297-121">Visual Basic junta implicitamente as duas coleções baseadas nos campos de chave especificados.</span><span class="sxs-lookup"><span data-stu-id="01297-121">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="01297-122">Você pode especificar um join explícito usando o `Join` cláusula quando desejar ser específico sobre quais campos-chave para usar na join.</span><span class="sxs-lookup"><span data-stu-id="01297-122">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="01297-123">Nesse caso, um `Where` cláusula ainda pode ser usada para filtrar os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="01297-123">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="01297-124">Para executar uma Inner Join usando a cláusula Join.</span><span class="sxs-lookup"><span data-stu-id="01297-124">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="01297-125">Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de ambos os implícita e explícita associação interna.</span><span class="sxs-lookup"><span data-stu-id="01297-125">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     <span data-ttu-id="01297-126">[!code-vb[VbLINQHowTos n º&4;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-126">[!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]</span></span>  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="01297-127">Executar uma junção externa esquerda usando a cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="01297-127">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="01297-128">LEFT OUTER JOIN inclui todos os itens da coleção do lado esquerdo do join e apenas valores correspondentes da coleção do lado direito da associação.</span><span class="sxs-lookup"><span data-stu-id="01297-128">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="01297-129">Todos os itens da coleção do lado direito do join que não têm um item correspondente na coleção do lado esquerdo são excluídos do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="01297-129">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="01297-130">O `Group Join` cláusula executa, efetivamente, um LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="01297-130">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="01297-131">A diferença entre o que é tipicamente conhecido como LEFT OUTER JOIN e o que o `Group Join` cláusula retorna é que o `Group Join` resultados de grupos de cláusula da coleção do lado direito do join para cada item da coleção do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="01297-131">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="01297-132">Em um banco de dados relacional, um LEFT OUTER JOIN retorna um resultado desagrupado no qual cada item na consulta resultar contém itens correspondentes de ambos os conjuntos na junção.</span><span class="sxs-lookup"><span data-stu-id="01297-132">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="01297-133">Nesse caso, os itens da coleção do lado esquerdo do join são repetidos para cada item correspondente da coleção do lado direito.</span><span class="sxs-lookup"><span data-stu-id="01297-133">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="01297-134">Você verá sua aparência quando você concluir o procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="01297-134">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="01297-135">Você pode recuperar os resultados de uma `Group Join` consulta como um resultado desagrupado estendendo sua consulta para retornar um item para cada resultado de consulta agrupada.</span><span class="sxs-lookup"><span data-stu-id="01297-135">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="01297-136">Para fazer isso, você precisa garantir que você consulte o `DefaultIfEmpty` método da coleção agrupada.</span><span class="sxs-lookup"><span data-stu-id="01297-136">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="01297-137">Isso assegura que os itens da coleção do lado esquerdo do join ainda são incluídos no resultado da consulta mesmo se eles não têm resultados correspondentes da coleção do lado direito.</span><span class="sxs-lookup"><span data-stu-id="01297-137">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="01297-138">Você pode adicionar código à sua consulta para fornecer um valor de resultado padrão quando não há nenhum valor correspondente da coleção do lado direito da associação.</span><span class="sxs-lookup"><span data-stu-id="01297-138">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="01297-139">Para executar um Left Outer Join usando a cláusula Group Join</span><span class="sxs-lookup"><span data-stu-id="01297-139">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="01297-140">Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma junção externa esquerda agrupada e uma junção externa esquerda desagrupada.</span><span class="sxs-lookup"><span data-stu-id="01297-140">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     <span data-ttu-id="01297-141">[!code-vb[VbLINQHowTos n º&3;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-141">[!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]</span></span>  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="01297-142">Executar uma junção usando uma chave composta</span><span class="sxs-lookup"><span data-stu-id="01297-142">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="01297-143">Você pode usar o `And` palavra-chave em uma `Join` ou `Group Join` cláusula para identificar vários campos de chave para usar ao combinar valores das coleções que estão sendo combinadas.</span><span class="sxs-lookup"><span data-stu-id="01297-143">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="01297-144">O `And` palavra-chave especifica que todos os especificados campos-chave devem corresponder para os itens a serem unidas.</span><span class="sxs-lookup"><span data-stu-id="01297-144">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="01297-145">Para executar uma associação usando uma chave composta</span><span class="sxs-lookup"><span data-stu-id="01297-145">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="01297-146">Adicione o seguinte código para o `Module1` módulo em seu projeto para ver exemplos de uma associação que usa uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="01297-146">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     <span data-ttu-id="01297-147">[!code-vb[VbLINQHowTos n º&5;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-147">[!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]</span></span>  
  
## <a name="run-the-code"></a><span data-ttu-id="01297-148">Executar o código</span><span class="sxs-lookup"><span data-stu-id="01297-148">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="01297-149">Para adicionar código para executar os exemplos</span><span class="sxs-lookup"><span data-stu-id="01297-149">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="01297-150">Substitua o `Sub Main` no `Module1` módulo em seu projeto com o código a seguir para executar os exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="01297-150">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     <span data-ttu-id="01297-151">[!code-vb[VbLINQHowTos n º&6;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="01297-151">[!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]</span></span>  
  
2.  <span data-ttu-id="01297-152">Pressione F5 para executar os exemplos.</span><span class="sxs-lookup"><span data-stu-id="01297-152">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01297-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01297-153">See Also</span></span>  
 <span data-ttu-id="01297-154">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="01297-154">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="01297-155"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="01297-155"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="01297-156"> [Cláusula JOIN](../../../../visual-basic/language-reference/queries/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="01297-156"> [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) </span></span>  
<span data-ttu-id="01297-157"> [Cláusula Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="01297-157"> [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) </span></span>  
<span data-ttu-id="01297-158"> [Cláusula FROM](../../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="01297-158"> [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="01297-159"> [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="01297-159"> [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="01297-160"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="01297-160"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="01297-161"> [Transformações de dados com LINQ (c#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="01297-161"> [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)</span></span>
