---
title: DataSets tipados
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 4648d49b1d7419d61a3a000404f42e0d02d25786
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198438"
---
# <a name="typed-datasets"></a><span data-ttu-id="daa42-102">DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="daa42-102">Typed DataSets</span></span>

<span data-ttu-id="daa42-103">Juntamente com acesso de associação tardia por meio de valores com variáveis fracamente tipadas, o <xref:System.Data.DataSet> fornece acesso a dados por meio de uma metáfora fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="daa42-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="daa42-104">Tabelas e colunas que fazem parte do **conjunto** de um podem ser acessadas usando nomes amigáveis de usuário e variáveis com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="daa42-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="daa42-105">Um **DataSet** tipado é uma classe derivada de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="daa42-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="daa42-106">Como tal, ele herda todos os métodos, eventos e propriedades de um **conjunto**de uma.</span><span class="sxs-lookup"><span data-stu-id="daa42-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="daa42-107">Além disso, um **DataSet** tipado fornece métodos, eventos e propriedades com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="daa42-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="daa42-108">Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção.</span><span class="sxs-lookup"><span data-stu-id="daa42-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="daa42-109">Além da melhor legibilidade do código, um **DataSet** tipado também permite que o editor de código do Visual Studio .net preencha automaticamente as linhas conforme você digita.</span><span class="sxs-lookup"><span data-stu-id="daa42-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="daa42-110">Além disso, o **conjunto** de texto com rigidez de tipos fornece acesso a valores como o tipo correto no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="daa42-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="daa42-111">Com um **conjunto**de texto com rigidez de tipos, erros de tipo incompatíveis são capturados quando o código é compilado em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="daa42-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="daa42-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="daa42-112">In This Section</span></span>  

 [<span data-ttu-id="daa42-113">Gerando DataSets fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="daa42-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="daa42-114">Descreve como criar e usar um conjunto de um **DataSet**com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="daa42-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="daa42-115">Anotando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="daa42-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="daa42-116">Descreve como anotar o esquema XSD (linguagem de definição de esquema XML) usado para gerar um **conjunto**de dado com rigidez de tipos, para dar aos elementos do **conjunto** de dado nomes amigáveis sem alterar o esquema subjacente.</span><span class="sxs-lookup"><span data-stu-id="daa42-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa42-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="daa42-117">See also</span></span>

- [<span data-ttu-id="daa42-118">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="daa42-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="daa42-119">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="daa42-119">ADO.NET Overview</span></span>](../ado-net-overview.md)
