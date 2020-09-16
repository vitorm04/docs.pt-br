---
title: 'Passo a passo: Escrevendo consultas em C# (LINQ)'
description: Este tutorial mostra como os recursos da linguagem C# são usados em expressões de consulta LINQ. Este artigo usa o Visual Studio como um ambiente de desenvolvimento.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: cfd2917d330a9229338790c35911502be5cd9391
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559142"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="6e1ce-104">Passo a passo: Escrevendo consultas em C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6e1ce-104">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="6e1ce-105">Essas instruções passo a passo demonstram os recursos de linguagem C# que são usados para gravar expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-105">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="6e1ce-106">Criar um Projeto C#</span><span class="sxs-lookup"><span data-stu-id="6e1ce-106">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e1ce-107">As instruções a seguir são para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-107">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="6e1ce-108">Se você estiver usando um ambiente de desenvolvimento diferente, crie um projeto de console com uma referência a System.Core.dll e uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-108">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="6e1ce-109">Para criar um projeto no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e1ce-109">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="6e1ce-110">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-110">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="6e1ce-111">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-111">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="6e1ce-112">A caixa de diálogo **Novo Projeto** será aberta.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-112">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="6e1ce-113">Expanda **Instalado**, expanda **Modelos**, expanda **Visual C#** e, em seguida, escolha **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-113">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="6e1ce-114">Na caixa de texto **Nome**, insira um nome diferente ou aceite o nome padrão e escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-114">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="6e1ce-115">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-115">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="6e1ce-116">Observe que o projeto tem uma referência a System.Core.dll e a uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-116">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="6e1ce-117">Criar uma Fonte de Dados na Memória</span><span class="sxs-lookup"><span data-stu-id="6e1ce-117">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="6e1ce-118">A fonte de dados para as consultas é uma lista simples de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-118">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="6e1ce-119">Cada registro `Student` tem um nome, sobrenome e uma matriz de inteiros que representa seus resultados de testes na classe.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-119">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="6e1ce-120">Copie este código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-120">Copy this code into your project.</span></span> <span data-ttu-id="6e1ce-121">Observe as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-121">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="6e1ce-122">A classe `Student` consiste em propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-122">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="6e1ce-123">Cada aluno na lista é inicializado com um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-123">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="6e1ce-124">A lista em si é inicializada com um inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-124">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="6e1ce-125">Essa estrutura de dados inteira será inicializada e instanciada sem chamadas explícitas para nenhum construtor ou acesso de membro explícito.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-125">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="6e1ce-126">Para obter mais informações sobre esses novos recursos, consulte [Propriedades autoimplementadas](../../classes-and-structs/auto-implemented-properties.md) e [Inicializadores de objeto e coleção](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-126">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="6e1ce-127">Para adicionar a fonte de dados</span><span class="sxs-lookup"><span data-stu-id="6e1ce-127">To add the data source</span></span>  
  
- <span data-ttu-id="6e1ce-128">Adicione a classe `Student` e a lista inicializada de alunos à classe `Program` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-128">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="6e1ce-129">Para adicionar um novo Aluno à lista de Alunos</span><span class="sxs-lookup"><span data-stu-id="6e1ce-129">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="6e1ce-130">Adicione um novo `Student` à lista `Students` e use um nome e pontuações de teste de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-130">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="6e1ce-131">Tente digitar as informações do novo aluno para aprender melhor a sintaxe do inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-131">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="6e1ce-132">Criar a Consulta</span><span class="sxs-lookup"><span data-stu-id="6e1ce-132">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="6e1ce-133">Para criar uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="6e1ce-133">To create a simple query</span></span>  
  
- <span data-ttu-id="6e1ce-134">No método `Main` do aplicativo, crie uma consulta simples que, quando for executada, produzirá uma lista de todos os alunos cuja pontuação no primeiro teste foi superior a 90.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-134">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="6e1ce-135">Observe que como o objeto `Student` todo está selecionado, o tipo da consulta é `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-135">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="6e1ce-136">Embora o código também possa usar a tipagem implícita usando a palavra-chave [var](../../../language-reference/keywords/var.md), a tipagem explícita é usada para ilustrar claramente os resultados.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-136">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="6e1ce-137">(Para obter mais informações sobre `var` , consulte [variáveis de local digitadas implicitamente](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="6e1ce-137">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="6e1ce-138">Observe também que a variável de intervalo da consulta, `student`, também funciona como uma referência para cada `Student` na fonte, fornecendo acesso ao membro para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-138">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="6e1ce-139">Executar a Consulta</span><span class="sxs-lookup"><span data-stu-id="6e1ce-139">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="6e1ce-140">Para executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-140">To execute the query</span></span>  
  
1. <span data-ttu-id="6e1ce-141">Agora escreva o loop `foreach` que fará com que a consulta seja executada.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-141">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="6e1ce-142">Observe o seguinte sobre o código:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-142">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="6e1ce-143">Cada elemento na sequência retornada é acessado pela variável de iteração no loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-143">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="6e1ce-144">O tipo dessa variável é `Student` e o tipo da variável de consulta é compatível, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-144">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="6e1ce-145">Após você ter adicionado esse código, compile e execute o aplicativo para ver os resultados na janela **Console**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-145">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="6e1ce-146">Para adicionar outra condição de filtro</span><span class="sxs-lookup"><span data-stu-id="6e1ce-146">To add another filter condition</span></span>  
  
1. <span data-ttu-id="6e1ce-147">Você pode combinar várias condições boolianas na cláusula `where` para refinar ainda mais uma consulta.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-147">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="6e1ce-148">O código a seguir adiciona uma condição de forma que a consulta retorna os alunos cuja primeira pontuação foi superior a 90 e cuja última pontuação foi inferior a 80.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-148">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="6e1ce-149">A cláusula `where` deve parecer com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-149">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="6e1ce-150">Para obter mais informações, consulte a [cláusula WHERE](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-150">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="6e1ce-151">Modificar a Consulta</span><span class="sxs-lookup"><span data-stu-id="6e1ce-151">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="6e1ce-152">Para ordenar os resultados</span><span class="sxs-lookup"><span data-stu-id="6e1ce-152">To order the results</span></span>  
  
1. <span data-ttu-id="6e1ce-153">Será mais fácil verificar os resultados se eles estiverem em algum tipo de ordem.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-153">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="6e1ce-154">Você pode ordenar a sequência retornada por qualquer campo acessível nos elementos de origem.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-154">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="6e1ce-155">Por exemplo, a cláusula `orderby` a seguir ordena os resultados em ordem alfabética de A a Z de acordo com o sobrenome de cada aluno.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-155">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="6e1ce-156">Adicione a cláusula `orderby` a seguir à consulta, logo após a instrução `where` e antes da instrução `select`:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-156">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="6e1ce-157">Agora, altere a cláusula `orderby` para que ela ordene os resultados em ordem inversa de acordo com a pontuação no primeiro teste, da pontuação mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-157">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="6e1ce-158">Altere a cadeia de caracteres de formato `WriteLine` para que você possa ver as pontuações:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-158">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="6e1ce-159">Para obter mais informações, consulte [Cláusula orderby](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-159">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="6e1ce-160">Para agrupar os resultados</span><span class="sxs-lookup"><span data-stu-id="6e1ce-160">To group the results</span></span>  
  
1. <span data-ttu-id="6e1ce-161">O agrupamento é uma poderosa funcionalidade em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-161">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="6e1ce-162">Uma consulta com uma cláusula group produz uma sequência de grupos e cada grupo em si contém um `Key` e uma sequência que consiste em todos os membros desse grupo.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-162">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="6e1ce-163">A nova consulta a seguir agrupa os alunos usando a primeira letra do sobrenome como a chave.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-163">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="6e1ce-164">Observe que o tipo da consulta agora mudou.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-164">Note that the type of the query has now changed.</span></span> <span data-ttu-id="6e1ce-165">Ele produz uma sequência de grupos que têm um tipo `char` como uma chave e uma sequência de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-165">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="6e1ce-166">Como o tipo de consulta foi alterado, o código a seguir altera o loop de execução `foreach` também:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-166">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="6e1ce-167">Execute o aplicativo e exiba os resultados na janela **Console**.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-167">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="6e1ce-168">Para obter mais informações, consulte [Cláusula group](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-168">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="6e1ce-169">Para deixar as variáveis tipadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="6e1ce-169">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="6e1ce-170">A codificação explícita `IEnumerables` de `IGroupings` pode se tornar entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-170">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="6e1ce-171">Você pode escrever a mesma consulta e o loop `foreach` muito mais convenientemente usado `var`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-171">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="6e1ce-172">A palavra-chave `var` não altera os tipos de objetos, ela simplesmente instrui o compilador a inferir os tipos.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-172">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="6e1ce-173">Altere o tipo de `studentQuery` e a variável de iteração `group` para `var` e execute a consulta novamente.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-173">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="6e1ce-174">Observe que no loop `foreach` interno, a variável de iteração ainda tem o tipo `Student` e a consulta funciona exatamente como antes.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-174">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="6e1ce-175">Alterar a variável de iteração `s` para `var` e execute a consulta novamente.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-175">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="6e1ce-176">Você verá que obtém exatamente os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-176">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="6e1ce-177">Para obter mais informações sobre [var](../../../language-reference/keywords/var.md), consulte [Variáveis locais de tipo implícito](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-177">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="6e1ce-178">Para ordenar os grupos pelo valor da chave</span><span class="sxs-lookup"><span data-stu-id="6e1ce-178">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="6e1ce-179">Ao executar a consulta anterior, observe que os grupos não estão em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-179">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="6e1ce-180">Para alterar isso, você deve fornecer uma cláusula `orderby` após a cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-180">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="6e1ce-181">Mas, para usar uma cláusula `orderby`, primeiro é necessário um identificador que serve como uma referência para os grupos criados pela cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-181">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="6e1ce-182">Forneça o identificador usando a palavra-chave `into`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-182">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="6e1ce-183">Quando você executa essa consulta, você verá que os grupos agora estão classificados em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-183">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="6e1ce-184">Para introduzir um identificador usando let</span><span class="sxs-lookup"><span data-stu-id="6e1ce-184">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="6e1ce-185">Você pode usar a palavra-chave `let` para introduzir um identificador para qualquer resultado da expressão na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-185">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="6e1ce-186">Esse identificador pode ser uma conveniência, como no exemplo a seguir ou ele pode melhorar o desempenho armazenando os resultados de uma expressão para que ele não precise ser calculado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-186">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="6e1ce-187">Para obter mais informações, consulte [Cláusula let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6e1ce-187">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="6e1ce-188">Para usar a sintaxe do método em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6e1ce-188">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="6e1ce-189">Conforme descrito em [Sintaxe de consulta e sintaxe de método em LINQ](./query-syntax-and-method-syntax-in-linq.md), algumas operações de consulta podem ser expressadas somente usando a sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-189">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="6e1ce-190">O código a seguir calcula a pontuação total para cada `Student` na sequência de origem e então chama o método `Average()` nos resultados da consulta para calcular a pontuação média da classe.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-190">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="6e1ce-191">Para transformar ou projetar na cláusula select</span><span class="sxs-lookup"><span data-stu-id="6e1ce-191">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="6e1ce-192">É muito comum para uma consulta produzir uma sequência cujos elementos são diferentes dos elementos nas sequências de origem.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-192">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="6e1ce-193">Exclua ou comente o loop de consulta e execução anterior e substitua-o pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-193">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="6e1ce-194">Observe que a consulta retorna uma sequência de cadeias de caracteres (não `Students`) e esse fato é refletido no loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-194">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="6e1ce-195">O código anterior neste passo a passo indicou que a pontuação média de classe é de aproximadamente 334.</span><span class="sxs-lookup"><span data-stu-id="6e1ce-195">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="6e1ce-196">Para produzir uma sequência de `Students` cuja pontuação total é maior que a média de classe, juntamente com seus `Student ID`, você pode usar um tipo anônimo na instrução `select`:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-196">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="6e1ce-197">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6e1ce-197">Next Steps</span></span>  
 <span data-ttu-id="6e1ce-198">Depois que estiver familiarizado com os aspectos básicos de como trabalhar com consultas em C#, você estará pronto para ler a documentação e exemplos para o tipo específico de provedor LINQ que lhe interessam:</span><span class="sxs-lookup"><span data-stu-id="6e1ce-198">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="6e1ce-199">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e1ce-199">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="6e1ce-200">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6e1ce-200">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="6e1ce-201">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6e1ce-201">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)  
  
 [<span data-ttu-id="6e1ce-202">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="6e1ce-202">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e1ce-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e1ce-203">See also</span></span>

- [<span data-ttu-id="6e1ce-204">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="6e1ce-204">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="6e1ce-205">Expressões de Consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="6e1ce-205">LINQ Query Expressions</span></span>](../../../linq/index.md)
