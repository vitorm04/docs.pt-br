---
title: 'Instruções passo a passo: escrevendo consultas em C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: ffff8317e6524acc877b7d0851e5a1b37967b1f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154067"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="26bf7-102">Instruções passo a passo: escrevendo consultas em C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="26bf7-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="26bf7-103">Essas instruções passo a passo demonstram os recursos de linguagem C# que são usados para gravar expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="26bf7-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="26bf7-104">Criar um Projeto C#</span><span class="sxs-lookup"><span data-stu-id="26bf7-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26bf7-105">As instruções a seguir são para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26bf7-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="26bf7-106">Se você estiver usando um ambiente de desenvolvimento diferente, crie um projeto de console com uma referência a System.Core.dll e uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26bf7-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="26bf7-107">Para criar um projeto no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26bf7-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="26bf7-108">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26bf7-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="26bf7-109">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="26bf7-110">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="26bf7-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="26bf7-111">Expanda **Instalado**, expanda **Modelos**, expanda **Visual C#** e, em seguida, escolha **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="26bf7-112">Na caixa de texto **Nome**, insira um nome diferente ou aceite o nome padrão e escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="26bf7-113">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="26bf7-114">Observe que o projeto tem uma referência a System.Core.dll e a uma diretiva `using` para o namespace <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26bf7-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="26bf7-115">Criar uma Fonte de Dados na Memória</span><span class="sxs-lookup"><span data-stu-id="26bf7-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="26bf7-116">A fonte de dados para as consultas é uma lista simples de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="26bf7-117">Cada registro `Student` tem um nome, sobrenome e uma matriz de inteiros que representa seus resultados de testes na classe.</span><span class="sxs-lookup"><span data-stu-id="26bf7-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="26bf7-118">Copie este código no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="26bf7-118">Copy this code into your project.</span></span> <span data-ttu-id="26bf7-119">Observe as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="26bf7-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="26bf7-120">A classe `Student` consiste em propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="26bf7-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="26bf7-121">Cada aluno na lista é inicializado com um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="26bf7-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="26bf7-122">A lista em si é inicializada com um inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="26bf7-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="26bf7-123">Essa estrutura de dados inteira será inicializada e instanciada sem chamadas explícitas para nenhum construtor ou acesso de membro explícito.</span><span class="sxs-lookup"><span data-stu-id="26bf7-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="26bf7-124">Para obter mais informações sobre esses novos recursos, consulte [Propriedades autoimplementadas](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="26bf7-125">Para adicionar a fonte de dados</span><span class="sxs-lookup"><span data-stu-id="26bf7-125">To add the data source</span></span>  
  
-   <span data-ttu-id="26bf7-126">Adicione a classe `Student` e a lista inicializada de alunos à classe `Program` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="26bf7-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="26bf7-127">Para adicionar um novo Aluno à lista de Alunos</span><span class="sxs-lookup"><span data-stu-id="26bf7-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="26bf7-128">Adicione um novo `Student` à lista `Students` e use um nome e pontuações de teste de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="26bf7-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="26bf7-129">Tente digitar as informações do novo aluno para aprender melhor a sintaxe do inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="26bf7-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="26bf7-130">Criar a Consulta</span><span class="sxs-lookup"><span data-stu-id="26bf7-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="26bf7-131">Para criar uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="26bf7-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="26bf7-132">No método `Main` do aplicativo, crie uma consulta simples que, quando for executada, produzirá uma lista de todos os alunos cuja pontuação no primeiro teste foi superior a 90.</span><span class="sxs-lookup"><span data-stu-id="26bf7-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="26bf7-133">Observe que como o objeto `Student` todo está selecionado, o tipo da consulta é `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="26bf7-134">Embora o código também possa usar a tipagem implícita usando a palavra-chave [var](../../../../csharp/language-reference/keywords/var.md), a tipagem explícita é usada para ilustrar claramente os resultados.</span><span class="sxs-lookup"><span data-stu-id="26bf7-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="26bf7-135">(Para obter mais informações sobre `var`, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="26bf7-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="26bf7-136">Observe também que a variável de intervalo da consulta, `student`, também funciona como uma referência para cada `Student` na fonte, fornecendo acesso ao membro para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="26bf7-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="26bf7-137">Executar a Consulta</span><span class="sxs-lookup"><span data-stu-id="26bf7-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="26bf7-138">Para executar a consulta</span><span class="sxs-lookup"><span data-stu-id="26bf7-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="26bf7-139">Agora escreva o loop `foreach` que fará com que a consulta seja executada.</span><span class="sxs-lookup"><span data-stu-id="26bf7-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="26bf7-140">Observe o seguinte sobre o código:</span><span class="sxs-lookup"><span data-stu-id="26bf7-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="26bf7-141">Cada elemento na sequência retornada é acessado pela variável de iteração no loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="26bf7-142">O tipo dessa variável é `Student` e o tipo da variável de consulta é compatível, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="26bf7-143">Após você ter adicionado esse código, compile e execute o aplicativo para ver os resultados na janela **Console**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="26bf7-144">Para adicionar outra condição de filtro</span><span class="sxs-lookup"><span data-stu-id="26bf7-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="26bf7-145">Você pode combinar várias condições boolianas na cláusula `where` para refinar ainda mais uma consulta.</span><span class="sxs-lookup"><span data-stu-id="26bf7-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="26bf7-146">O código a seguir adiciona uma condição de forma que a consulta retorna os alunos cuja primeira pontuação foi superior a 90 e cuja última pontuação foi inferior a 80.</span><span class="sxs-lookup"><span data-stu-id="26bf7-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="26bf7-147">A cláusula `where` deve parecer com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="26bf7-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="26bf7-148">Para obter mais informações, consulte [Cláusula where](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="26bf7-149">Modificar a Consulta</span><span class="sxs-lookup"><span data-stu-id="26bf7-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="26bf7-150">Para ordenar os resultados</span><span class="sxs-lookup"><span data-stu-id="26bf7-150">To order the results</span></span>  
  
1.  <span data-ttu-id="26bf7-151">Será mais fácil verificar os resultados se eles estiverem em algum tipo de ordem.</span><span class="sxs-lookup"><span data-stu-id="26bf7-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="26bf7-152">Você pode ordenar a sequência retornada por qualquer campo acessível nos elementos de origem.</span><span class="sxs-lookup"><span data-stu-id="26bf7-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="26bf7-153">Por exemplo, a cláusula `orderby` a seguir ordena os resultados em ordem alfabética de A a Z de acordo com o sobrenome de cada aluno.</span><span class="sxs-lookup"><span data-stu-id="26bf7-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="26bf7-154">Adicione a cláusula `orderby` a seguir à consulta, logo após a instrução `where` e antes da instrução `select`:</span><span class="sxs-lookup"><span data-stu-id="26bf7-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="26bf7-155">Agora, altere a cláusula `orderby` para que ela ordene os resultados em ordem inversa de acordo com a pontuação no primeiro teste, da pontuação mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="26bf7-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="26bf7-156">Altere a cadeia de caracteres de formato `WriteLine` para que você possa ver as pontuações:</span><span class="sxs-lookup"><span data-stu-id="26bf7-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="26bf7-157">Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="26bf7-158">Para agrupar os resultados</span><span class="sxs-lookup"><span data-stu-id="26bf7-158">To group the results</span></span>  
  
1.  <span data-ttu-id="26bf7-159">O agrupamento é uma poderosa funcionalidade em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="26bf7-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="26bf7-160">Uma consulta com uma cláusula group produz uma sequência de grupos e cada grupo em si contém um `Key` e uma sequência que consiste em todos os membros desse grupo.</span><span class="sxs-lookup"><span data-stu-id="26bf7-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="26bf7-161">A nova consulta a seguir agrupa os alunos usando a primeira letra do sobrenome como a chave.</span><span class="sxs-lookup"><span data-stu-id="26bf7-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="26bf7-162">Observe que o tipo da consulta agora mudou.</span><span class="sxs-lookup"><span data-stu-id="26bf7-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="26bf7-163">Ele produz uma sequência de grupos que têm um tipo `char` como uma chave e uma sequência de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="26bf7-164">Como o tipo de consulta foi alterado, o código a seguir altera o loop de execução `foreach` também:</span><span class="sxs-lookup"><span data-stu-id="26bf7-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="26bf7-165">Execute o aplicativo e exiba os resultados na janela **Console**.</span><span class="sxs-lookup"><span data-stu-id="26bf7-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="26bf7-166">Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="26bf7-167">Para deixar as variáveis tipadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="26bf7-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="26bf7-168">A codificação explícita `IEnumerables` de `IGroupings` pode se tornar entediante rapidamente.</span><span class="sxs-lookup"><span data-stu-id="26bf7-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="26bf7-169">Você pode escrever a mesma consulta e o loop `foreach` muito mais convenientemente usado `var`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="26bf7-170">A palavra-chave `var` não altera os tipos de objetos, ela simplesmente instrui o compilador a inferir os tipos.</span><span class="sxs-lookup"><span data-stu-id="26bf7-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="26bf7-171">Altere o tipo de `studentQuery` e a variável de iteração `group` para `var` e execute a consulta novamente.</span><span class="sxs-lookup"><span data-stu-id="26bf7-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="26bf7-172">Observe que no loop `foreach` interno, a variável de iteração ainda tem o tipo `Student` e a consulta funciona exatamente como antes.</span><span class="sxs-lookup"><span data-stu-id="26bf7-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="26bf7-173">Alterar a variável de iteração `s` para `var` e execute a consulta novamente.</span><span class="sxs-lookup"><span data-stu-id="26bf7-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="26bf7-174">Você verá que obtém exatamente os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="26bf7-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="26bf7-175">Para obter mais informações sobre [var](../../../../csharp/language-reference/keywords/var.md), consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="26bf7-176">Para ordenar os grupos pelo valor da chave</span><span class="sxs-lookup"><span data-stu-id="26bf7-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="26bf7-177">Ao executar a consulta anterior, observe que os grupos não estão em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="26bf7-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="26bf7-178">Para alterar isso, você deve fornecer uma cláusula `orderby` após a cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="26bf7-179">Mas, para usar uma cláusula `orderby`, primeiro é necessário um identificador que serve como uma referência para os grupos criados pela cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="26bf7-180">Forneça o identificador usando a palavra-chave `into`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="26bf7-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="26bf7-181">Quando você executa essa consulta, você verá que os grupos agora estão classificados em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="26bf7-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="26bf7-182">Para introduzir um identificador usando let</span><span class="sxs-lookup"><span data-stu-id="26bf7-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="26bf7-183">Você pode usar a palavra-chave `let` para introduzir um identificador para qualquer resultado da expressão na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="26bf7-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="26bf7-184">Esse identificador pode ser uma conveniência, como no exemplo a seguir ou ele pode melhorar o desempenho armazenando os resultados de uma expressão para que ele não precise ser calculado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="26bf7-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="26bf7-185">Para obter mais informações, consulte [Cláusula let](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="26bf7-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="26bf7-186">Para usar a sintaxe do método em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="26bf7-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="26bf7-187">Conforme descrito em [Sintaxe de consulta e sintaxe de método em LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), algumas operações de consulta podem ser expressadas somente usando a sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="26bf7-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="26bf7-188">O código a seguir calcula a pontuação total para cada `Student` na sequência de origem e então chama o método `Average()` nos resultados da consulta para calcular a pontuação média da classe.</span><span class="sxs-lookup"><span data-stu-id="26bf7-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="26bf7-189">Para transformar ou projetar na cláusula select</span><span class="sxs-lookup"><span data-stu-id="26bf7-189">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="26bf7-190">É muito comum para uma consulta produzir uma sequência cujos elementos são diferentes dos elementos nas sequências de origem.</span><span class="sxs-lookup"><span data-stu-id="26bf7-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="26bf7-191">Exclua ou comente o loop de consulta e execução anterior e substitua-o pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="26bf7-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="26bf7-192">Observe que a consulta retorna uma sequência de cadeias de caracteres (não `Students`) e esse fato é refletido no loop `foreach`.</span><span class="sxs-lookup"><span data-stu-id="26bf7-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="26bf7-193">O código anterior neste passo a passo indicou que a pontuação média de classe é de aproximadamente 334.</span><span class="sxs-lookup"><span data-stu-id="26bf7-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="26bf7-194">Para produzir uma sequência de `Students` cuja pontuação total é maior que a média de classe, juntamente com seus `Student ID`, você pode usar um tipo anônimo na instrução `select`:</span><span class="sxs-lookup"><span data-stu-id="26bf7-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="26bf7-195">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="26bf7-195">Next Steps</span></span>  
 <span data-ttu-id="26bf7-196">Depois que estiver familiarizado com os aspectos básicos de como trabalhar com consultas em C#, você estará pronto para ler a documentação e exemplos para o tipo específico de provedor LINQ que lhe interessam:</span><span class="sxs-lookup"><span data-stu-id="26bf7-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="26bf7-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="26bf7-197">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="26bf7-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="26bf7-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="26bf7-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="26bf7-199">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="26bf7-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="26bf7-200">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="26bf7-201">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26bf7-201">See Also</span></span>

- [<span data-ttu-id="26bf7-202">LINQ (consulta integrada à linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="26bf7-202">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="26bf7-203">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="26bf7-203">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [<span data-ttu-id="26bf7-204">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="26bf7-204">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
