---
title: 'Como: Chamar funções personalizadas de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: cc2e25183649f6a95e7862520ccc5719f201277a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311481"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="9907b-102">Como: Chamar funções personalizadas de banco de dados</span><span class="sxs-lookup"><span data-stu-id="9907b-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="9907b-103">Este tópico descreve como chamar funções personalizados que são definidas na base de dados de dentro das consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9907b-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="9907b-104">Funções de base de dados que são chamadas de consultas LINQ to entidades são executadas em base de dados.</span><span class="sxs-lookup"><span data-stu-id="9907b-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="9907b-105">Executar funções na base de dados pode melhorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9907b-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="9907b-106">O procedimento a seguir fornece um contorno de alto nível para chamar uma função de base de dados personalizado.</span><span class="sxs-lookup"><span data-stu-id="9907b-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="9907b-107">O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento.</span><span class="sxs-lookup"><span data-stu-id="9907b-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="9907b-108">Para chamar funções personalizados que são definidas na base de dados</span><span class="sxs-lookup"><span data-stu-id="9907b-108">To call custom functions that are defined in the database</span></span>  
  
1. <span data-ttu-id="9907b-109">Crie uma função personalizada em seu base de dados.</span><span class="sxs-lookup"><span data-stu-id="9907b-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="9907b-110">Para obter mais informações sobre como criar funções personalizadas no SQL Server, consulte [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="9907b-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2. <span data-ttu-id="9907b-111">Declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="9907b-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="9907b-112">O nome da função deve ser o mesmo que o nome da função declarada no base de dados.</span><span class="sxs-lookup"><span data-stu-id="9907b-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="9907b-113">Para obter mais informações, consulte [o elemento de função (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="9907b-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3. <span data-ttu-id="9907b-114">Adicione um método correspondente a uma classe em seu código do aplicativo e aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> a nota de método que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9907b-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="9907b-115">A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9907b-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4. <span data-ttu-id="9907b-116">Chame o método em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9907b-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9907b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9907b-117">Example</span></span>  
 <span data-ttu-id="9907b-118">O exemplo a seguir demonstra como chamar uma função de base de dados personalizado de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9907b-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="9907b-119">O exemplo usa o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="9907b-119">The example uses the School model.</span></span> <span data-ttu-id="9907b-120">Para obter informações sobre o modelo de escola, consulte [criando o banco de dados de exemplo School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) e [gerando a. edmx de escola arquivo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9907b-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9907b-121">O código a seguir adiciona a função de `AvgStudentGrade` a base de dados de exemplo de escola.</span><span class="sxs-lookup"><span data-stu-id="9907b-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9907b-122">As etapas para chamar uma função de base de dados personalizado são as mesmas independentemente do servidor de base de dados.</span><span class="sxs-lookup"><span data-stu-id="9907b-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="9907b-123">No entanto, o código abaixo é específico para criar uma função em uma base de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9907b-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="9907b-124">O código para criar uma função personalizada em outros servidores de base de dados pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="9907b-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="9907b-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9907b-125">Example</span></span>  
 <span data-ttu-id="9907b-126">Em seguida, declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="9907b-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="9907b-127">o código a seguir declara a função de `AvgStudentGrade` em SSDL:</span><span class="sxs-lookup"><span data-stu-id="9907b-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="9907b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9907b-128">Example</span></span>  
 <span data-ttu-id="9907b-129">Agora crie um método e mapear-lo a função declarada em SSDL.</span><span class="sxs-lookup"><span data-stu-id="9907b-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="9907b-130">O método na classe é mapeado para a função definida em SSDL (acima) usando <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9907b-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="9907b-131">Quando esse método é chamado, a função correspondente na base de dados é executada.</span><span class="sxs-lookup"><span data-stu-id="9907b-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9907b-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9907b-132">Example</span></span>  
 <span data-ttu-id="9907b-133">Finalmente, chame o método em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9907b-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="9907b-134">O código a seguir exibe os sobrenomes e as ordens média dos alunos no console:</span><span class="sxs-lookup"><span data-stu-id="9907b-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9907b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9907b-135">See also</span></span>

- <span data-ttu-id="9907b-136">[Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9907b-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="9907b-137">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9907b-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
