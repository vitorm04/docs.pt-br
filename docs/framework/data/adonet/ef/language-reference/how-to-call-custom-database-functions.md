---
title: 'Como: Chamar funções personalizadas de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: b7f483d8dc7c6d0160ec211140726c9d732f0268
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250803"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="c9434-102">Como: Chamar funções personalizadas de banco de dados</span><span class="sxs-lookup"><span data-stu-id="c9434-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="c9434-103">Este tópico descreve como chamar funções personalizados que são definidas na base de dados de dentro das consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c9434-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="c9434-104">Funções de base de dados que são chamadas de consultas LINQ to entidades são executadas em base de dados.</span><span class="sxs-lookup"><span data-stu-id="c9434-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="c9434-105">Executar funções na base de dados pode melhorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c9434-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="c9434-106">O procedimento a seguir fornece um contorno de alto nível para chamar uma função de base de dados personalizado.</span><span class="sxs-lookup"><span data-stu-id="c9434-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="c9434-107">O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento.</span><span class="sxs-lookup"><span data-stu-id="c9434-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="c9434-108">Para chamar funções personalizados que são definidas na base de dados</span><span class="sxs-lookup"><span data-stu-id="c9434-108">To call custom functions that are defined in the database</span></span>  
  
1. <span data-ttu-id="c9434-109">Crie uma função personalizada em seu base de dados.</span><span class="sxs-lookup"><span data-stu-id="c9434-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="c9434-110">Para obter mais informações sobre como criar funções personalizadas no SQL Server, consulte [criar função (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="c9434-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2. <span data-ttu-id="c9434-111">Declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="c9434-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="c9434-112">O nome da função deve ser o mesmo que o nome da função declarada no base de dados.</span><span class="sxs-lookup"><span data-stu-id="c9434-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="c9434-113">Para obter mais informações, consulte [elemento Function (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="c9434-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3. <span data-ttu-id="c9434-114">Adicione um método correspondente a uma classe em seu código do aplicativo e aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> a nota de método que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c9434-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="c9434-115">A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c9434-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4. <span data-ttu-id="c9434-116">Chame o método em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c9434-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9434-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9434-117">Example</span></span>  
 <span data-ttu-id="c9434-118">O exemplo a seguir demonstra como chamar uma função de base de dados personalizado de uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c9434-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="c9434-119">O exemplo usa o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="c9434-119">The example uses the School model.</span></span> <span data-ttu-id="c9434-120">Para obter informações sobre o modelo escolar, consulte [criando o banco de dados de exemplo da escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) e [gerando o arquivo School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c9434-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="c9434-121">O código a seguir adiciona a função de `AvgStudentGrade` a base de dados de exemplo de escola.</span><span class="sxs-lookup"><span data-stu-id="c9434-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9434-122">As etapas para chamar uma função de base de dados personalizado são as mesmas independentemente do servidor de base de dados.</span><span class="sxs-lookup"><span data-stu-id="c9434-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="c9434-123">No entanto, o código abaixo é específico para criar uma função em uma base de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c9434-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="c9434-124">O código para criar uma função personalizada em outros servidores de base de dados pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="c9434-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="c9434-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9434-125">Example</span></span>  
 <span data-ttu-id="c9434-126">Em seguida, declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx.</span><span class="sxs-lookup"><span data-stu-id="c9434-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="c9434-127">o código a seguir declara a função de `AvgStudentGrade` em SSDL:</span><span class="sxs-lookup"><span data-stu-id="c9434-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="c9434-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9434-128">Example</span></span>  
 <span data-ttu-id="c9434-129">Agora crie um método e mapear-lo a função declarada em SSDL.</span><span class="sxs-lookup"><span data-stu-id="c9434-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="c9434-130">O método na classe é mapeado para a função definida em SSDL (acima) usando <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c9434-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="c9434-131">Quando esse método é chamado, a função correspondente na base de dados é executada.</span><span class="sxs-lookup"><span data-stu-id="c9434-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="c9434-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9434-132">Example</span></span>  
 <span data-ttu-id="c9434-133">Finalmente, chame o método em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="c9434-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="c9434-134">O código a seguir exibe os sobrenomes e as ordens média dos alunos no console:</span><span class="sxs-lookup"><span data-stu-id="c9434-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c9434-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9434-135">See also</span></span>

- <span data-ttu-id="c9434-136">[Visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c9434-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="c9434-137">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c9434-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
