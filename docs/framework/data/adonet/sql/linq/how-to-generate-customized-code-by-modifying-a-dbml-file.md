---
title: 'Como: gerar código personalizado modificando um arquivo DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 6619f4b8c0a47b36a0b84fa21bab4109d26ef895
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002950"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="cae84-102">Como: gerar código personalizado modificando um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="cae84-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="cae84-103">Você pode gerar Visual Basic ou C# código-fonte de um arquivo de metadados de linguagem de marcação de banco de dados (. dbml).</span><span class="sxs-lookup"><span data-stu-id="cae84-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="cae84-104">Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cae84-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="cae84-105">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="cae84-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="cae84-106">As etapas nesse processo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="cae84-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="cae84-107">Gere um arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="cae84-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="cae84-108">Use um editor para modificar o arquivo .dbml.</span><span class="sxs-lookup"><span data-stu-id="cae84-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="cae84-109">Observe que o arquivo. dbml deve validar em relação ao arquivo de definição de esquema (. xsd) para arquivos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. dbml.</span><span class="sxs-lookup"><span data-stu-id="cae84-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="cae84-110">Para obter mais informações, consulte [geração de código em LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cae84-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="cae84-111">Gere o Visual Basic ou C# o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="cae84-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="cae84-112">Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="cae84-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="cae84-113">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cae84-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae84-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cae84-114">Example</span></span>  
 <span data-ttu-id="cae84-115">O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="cae84-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="cae84-116">Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.</span><span class="sxs-lookup"><span data-stu-id="cae84-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="cae84-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cae84-117">Example</span></span>  
 <span data-ttu-id="cae84-118">O código a seguir gera Visual Basic C# ou arquivo de código-fonte de um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="cae84-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="cae84-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cae84-119">See also</span></span>

- [<span data-ttu-id="cae84-120">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cae84-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="cae84-121">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="cae84-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="cae84-122">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="cae84-122">Creating the Object Model</span></span>](creating-the-object-model.md)
