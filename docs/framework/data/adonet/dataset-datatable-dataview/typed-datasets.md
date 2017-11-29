---
title: DataSets tipados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3d5edc4f469b59ff787e500ad447fe0076c332c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="typed-datasets"></a><span data-ttu-id="d76c9-102">DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="d76c9-102">Typed DataSets</span></span>
<span data-ttu-id="d76c9-103">Juntamente com acesso de associação tardia por meio de valores com variáveis fracamente tipadas, o <xref:System.Data.DataSet> fornece acesso a dados por meio de uma metáfora fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="d76c9-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="d76c9-104">Tabelas e colunas que fazem parte do **DataSet** podem ser acessados usando nomes amigáveis e fortemente tipadas variáveis.</span><span class="sxs-lookup"><span data-stu-id="d76c9-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="d76c9-105">Um tipo **DataSet** é uma classe que deriva de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d76c9-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="d76c9-106">Como tal, ele herda todos os eventos, métodos e propriedades de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d76c9-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="d76c9-107">Além disso, um tipo **DataSet** fornece métodos com rigidez de tipos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="d76c9-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="d76c9-108">Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção.</span><span class="sxs-lookup"><span data-stu-id="d76c9-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="d76c9-109">Além de melhor legibilidade do código, com um tipo **DataSet** também permite que o código do Visual Studio .NET editor preencher linhas automaticamente conforme você digita.</span><span class="sxs-lookup"><span data-stu-id="d76c9-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="d76c9-110">Além disso, fortemente tipada **DataSet** fornece acesso a valores como o tipo correto em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="d76c9-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="d76c9-111">Com um fortemente tipada **conjunto de dados**, erros de incompatibilidade de tipo são detectados quando o código é compilado em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76c9-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d76c9-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d76c9-112">In This Section</span></span>  
 [<span data-ttu-id="d76c9-113">Gerando DataSets fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="d76c9-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="d76c9-114">Descreve como criar e usar um fortemente tipada **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d76c9-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="d76c9-115">Anotando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="d76c9-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="d76c9-116">Descreve como anotar o esquema de linguagem XSD de definição de esquema XML usado para gerar um fortemente tipada **DataSet**, fornecer **DataSet** nomes amigáveis de elementos sem alterar o esquema subjacente.</span><span class="sxs-lookup"><span data-stu-id="d76c9-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76c9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d76c9-117">See Also</span></span>  
 <span data-ttu-id="d76c9-118">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="d76c9-118">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="d76c9-119">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d76c9-119">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
