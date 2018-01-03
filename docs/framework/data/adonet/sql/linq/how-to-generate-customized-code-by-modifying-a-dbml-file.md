---
title: "Como gerar código personalizado modificando um arquivo DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: efff585cff127e71e2dedd8abf2f502ca28e8df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="95cea-102">Como gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="95cea-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="95cea-103">Você pode gerar [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou código-fonte c# de um arquivo de metadados do banco de dados markup language (. dbml).</span><span class="sxs-lookup"><span data-stu-id="95cea-103">You can generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="95cea-104">Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95cea-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="95cea-105">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="95cea-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="95cea-106">As etapas nesse processo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="95cea-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="95cea-107">Gere um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="95cea-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="95cea-108">Use um editor para modificar o arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="95cea-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="95cea-109">Observe que o arquivo dbml deve validar o arquivo de definição (. xsd) de esquema para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivos dbml.</span><span class="sxs-lookup"><span data-stu-id="95cea-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="95cea-110">Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="95cea-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="95cea-111">Gere o código-fonte de [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C#.</span><span class="sxs-lookup"><span data-stu-id="95cea-111">Generate the [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code.</span></span>  
  
 <span data-ttu-id="95cea-112">Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="95cea-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="95cea-113">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="95cea-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95cea-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95cea-114">Example</span></span>  
 <span data-ttu-id="95cea-115">O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="95cea-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="95cea-116">Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.</span><span class="sxs-lookup"><span data-stu-id="95cea-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="95cea-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95cea-117">Example</span></span>  
 <span data-ttu-id="95cea-118">O código a seguir gera arquivo de código-fonte do [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C# de um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="95cea-118">The following code generates [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="95cea-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95cea-119">See Also</span></span>  
 [<span data-ttu-id="95cea-120">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="95cea-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="95cea-121">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="95cea-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="95cea-122">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="95cea-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
