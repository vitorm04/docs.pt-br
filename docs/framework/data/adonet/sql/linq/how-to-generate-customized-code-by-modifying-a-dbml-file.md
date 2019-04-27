---
title: 'Como: gerar código personalizado modificando um arquivo DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877338"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="18feb-102">Como: gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="18feb-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="18feb-103">Você pode gerar o Visual Basic ou C# código-fonte de um arquivo de metadados do banco de dados markup language (. dbml).</span><span class="sxs-lookup"><span data-stu-id="18feb-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="18feb-104">Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18feb-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="18feb-105">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="18feb-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="18feb-106">As etapas nesse processo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="18feb-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="18feb-107">Gere um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="18feb-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="18feb-108">Use um editor para modificar o arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="18feb-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="18feb-109">Observe que o arquivo. dbml deve validar o arquivo de definição (. xsd) de esquema para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivos. dbml.</span><span class="sxs-lookup"><span data-stu-id="18feb-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="18feb-110">Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="18feb-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="18feb-111">Gerar o Visual Basic ou C# código-fonte.</span><span class="sxs-lookup"><span data-stu-id="18feb-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="18feb-112">Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="18feb-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="18feb-113">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="18feb-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18feb-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18feb-114">Example</span></span>  
 <span data-ttu-id="18feb-115">O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="18feb-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="18feb-116">Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.</span><span class="sxs-lookup"><span data-stu-id="18feb-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="18feb-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18feb-117">Example</span></span>  
 <span data-ttu-id="18feb-118">O código a seguir gera o Visual Basic ou C# arquivo de código-fonte de um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="18feb-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="18feb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18feb-119">See also</span></span>

- [<span data-ttu-id="18feb-120">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="18feb-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="18feb-121">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="18feb-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="18feb-122">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="18feb-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
