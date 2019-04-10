---
title: 'Como: gerar código personalizado modificando um arquivo DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338417"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="63162-102">Como: gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="63162-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="63162-103">Você pode gerar o Visual Basic ou C# código-fonte de um arquivo de metadados do banco de dados markup language (. dbml).</span><span class="sxs-lookup"><span data-stu-id="63162-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="63162-104">Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63162-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="63162-105">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="63162-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="63162-106">As etapas nesse processo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="63162-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="63162-107">Gere um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="63162-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="63162-108">Use um editor para modificar o arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="63162-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="63162-109">Observe que o arquivo. dbml deve validar o arquivo de definição (. xsd) de esquema para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivos. dbml.</span><span class="sxs-lookup"><span data-stu-id="63162-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="63162-110">Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="63162-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="63162-111">Gerar o Visual Basic ou C# código-fonte.</span><span class="sxs-lookup"><span data-stu-id="63162-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="63162-112">Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="63162-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="63162-113">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="63162-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63162-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63162-114">Example</span></span>  
 <span data-ttu-id="63162-115">O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="63162-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="63162-116">Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.</span><span class="sxs-lookup"><span data-stu-id="63162-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="63162-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63162-117">Example</span></span>  
 <span data-ttu-id="63162-118">O código a seguir gera o Visual Basic ou C# arquivo de código-fonte de um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="63162-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="63162-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63162-119">See also</span></span>

- [<span data-ttu-id="63162-120">Geração de código em LINQ para SQL</span><span class="sxs-lookup"><span data-stu-id="63162-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="63162-121">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="63162-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="63162-122">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="63162-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
