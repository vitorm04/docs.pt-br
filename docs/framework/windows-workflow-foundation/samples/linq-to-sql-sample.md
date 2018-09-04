---
title: LINQ to SQL de exemplo
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515362"
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="94c3b-102">LINQ to SQL de exemplo</span><span class="sxs-lookup"><span data-stu-id="94c3b-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="94c3b-103">Este exemplo demonstra como criar uma atividade para usar entidades de consulta LINQ to SQL das tabelas em bases de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="94c3b-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94c3b-104">Os exemplos do WCF podem já estar instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="94c3b-104">The WCF samples may already be installed on your machine.</span></span> <span data-ttu-id="94c3b-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="94c3b-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="94c3b-106">Se este diretório não existe, clique no link de exemplo de download na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="94c3b-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="94c3b-107">Observe que este link baixa e instala todos os [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, e [!INCLUDE[infocard](../../../../includes/infocard-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="94c3b-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="94c3b-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="94c3b-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="94c3b-109">Detalhes de atividade para FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="94c3b-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="94c3b-110">Esta atividade permite que os usuários vejam entidades das tabelas em uma base de dados usando LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="94c3b-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="94c3b-111">Os usuários de atividade também podem fornecer um predicado LINQ na forma de uma expressão lambda para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="94c3b-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="94c3b-112">Se nenhum predicado é fornecido, a tabela inteira é retornada.</span><span class="sxs-lookup"><span data-stu-id="94c3b-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="94c3b-113">A tabela a seguir detalha a propriedade e valores de retorno para atividades.</span><span class="sxs-lookup"><span data-stu-id="94c3b-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="94c3b-114">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="94c3b-114">Property or Return Value</span></span>|<span data-ttu-id="94c3b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c3b-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="94c3b-116">Propriedade `Collection`</span><span class="sxs-lookup"><span data-stu-id="94c3b-116">`Collection` property</span></span>|<span data-ttu-id="94c3b-117">Uma propriedade necessário que especifica a coleção fonte.</span><span class="sxs-lookup"><span data-stu-id="94c3b-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="94c3b-118">Propriedade `Predicate`</span><span class="sxs-lookup"><span data-stu-id="94c3b-118">`Predicate` property</span></span>|<span data-ttu-id="94c3b-119">Uma propriedade necessário que especifica o filtro para a coleção na forma de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="94c3b-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="94c3b-120">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="94c3b-120">Return Value</span></span>|<span data-ttu-id="94c3b-121">A coleção filtrada.</span><span class="sxs-lookup"><span data-stu-id="94c3b-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="94c3b-122">Exemplo de código que usa a atividade personalizado</span><span class="sxs-lookup"><span data-stu-id="94c3b-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="94c3b-123">O exemplo de código usa a atividade personalizado de `FindInSqlTable` para localizar todas as linhas em uma tabela SQL Server denominado `Employee` onde a coluna de `Role` é igual a `SDE`.</span><span class="sxs-lookup"><span data-stu-id="94c3b-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="94c3b-124">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="94c3b-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="94c3b-125">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="94c3b-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="94c3b-126">Navegue até a pasta que contém esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="94c3b-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="94c3b-127">Execute o arquivo de comando de Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="94c3b-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94c3b-128">O script de Setup.cmd tentar instalar o base de dados de exemplo em seu computador local SQL Server Express edition.</span><span class="sxs-lookup"><span data-stu-id="94c3b-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="94c3b-129">Se você deseja instalá-lo em outra instância do SQL server, editar Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="94c3b-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="94c3b-130">O script de Setup.cmd faz as seguintes medidas.:</span><span class="sxs-lookup"><span data-stu-id="94c3b-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="94c3b-131">Cria um base de dados chamado LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="94c3b-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="94c3b-132">Cria funções da tabela.</span><span class="sxs-lookup"><span data-stu-id="94c3b-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="94c3b-133">Cria uma tabela employees.</span><span class="sxs-lookup"><span data-stu-id="94c3b-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="94c3b-134">Insere 3 registros nas funções da tabela.</span><span class="sxs-lookup"><span data-stu-id="94c3b-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="94c3b-135">Insere 12 registros na tabela employees.</span><span class="sxs-lookup"><span data-stu-id="94c3b-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="94c3b-136">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="94c3b-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="94c3b-137">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="94c3b-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="94c3b-138">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="94c3b-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="94c3b-139">Para desinstalar o base de dados de exemplo LinqToSql</span><span class="sxs-lookup"><span data-stu-id="94c3b-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="94c3b-140">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="94c3b-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="94c3b-141">Navegue até a pasta que contém esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="94c3b-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="94c3b-142">Execute o arquivo de comando de Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="94c3b-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94c3b-143">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="94c3b-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94c3b-144">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="94c3b-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94c3b-145">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="94c3b-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94c3b-146">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="94c3b-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="94c3b-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94c3b-147">See Also</span></span>  
 [<span data-ttu-id="94c3b-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="94c3b-148">LINQ to SQL</span></span>](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="94c3b-149">Guia de Introdução (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="94c3b-149">Getting Started (LINQ to SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150377)
