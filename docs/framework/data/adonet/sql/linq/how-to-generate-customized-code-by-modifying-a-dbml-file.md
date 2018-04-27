---
title: Como gerar código personalizado modificando um arquivo DBML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: dccef2af3d13099b71d3ea8418242e5a5cc16ae5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="a2b4b-102">Como gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="a2b4b-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="a2b4b-103">Você pode gerar o código de origem do Visual Basic ou c# de um arquivo de metadados do banco de dados markup language (. dbml).</span><span class="sxs-lookup"><span data-stu-id="a2b4b-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="a2b4b-104">Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="a2b4b-105">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="a2b4b-106">As etapas nesse processo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="a2b4b-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="a2b4b-107">Gere um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="a2b4b-108">Use um editor para modificar o arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="a2b4b-109">Observe que o arquivo dbml deve validar o arquivo de definição (. xsd) de esquema para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivos dbml.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="a2b4b-110">Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a2b4b-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="a2b4b-111">Gere código-fonte do Visual Basic ou c#.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="a2b4b-112">Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="a2b4b-113">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a2b4b-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b4b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2b4b-114">Example</span></span>  
 <span data-ttu-id="a2b4b-115">O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="a2b4b-116">Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="a2b4b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2b4b-117">Example</span></span>  
 <span data-ttu-id="a2b4b-118">O código a seguir gera um arquivo de código Visual Basic ou c# fonte de um arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="a2b4b-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2b4b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2b4b-119">See Also</span></span>  
 [<span data-ttu-id="a2b4b-120">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a2b4b-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="a2b4b-121">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="a2b4b-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="a2b4b-122">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="a2b4b-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
