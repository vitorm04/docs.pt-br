---
title: Criando uma DataTable
description: Aprenda a criar uma DataTable em ADO.NET, que representa uma tabela de dados relacionais na memória, para uso de forma independente ou por outros objetos .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 335137eeef02e590539c6d83e46cb39901a1e03f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286915"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="d5a94-103">Criando uma DataTable</span><span class="sxs-lookup"><span data-stu-id="d5a94-103">Creating a DataTable</span></span>
<span data-ttu-id="d5a94-104">Uma <xref:System.Data.DataTable>, que representa uma tabela de dados relacionais de memória, pode ser criada e usada independentemente ou pode ser usada por outros objetos do .NET Framework, mais comumente como membro de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d5a94-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="d5a94-105">Você pode criar um objeto **DataTable** usando o construtor **DataTable** apropriado.</span><span class="sxs-lookup"><span data-stu-id="d5a94-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="d5a94-106">Você pode adicioná-lo ao **DataSet** usando o método **Add** para adicioná-lo à coleção **Tables** do objeto **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="d5a94-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="d5a94-107">Você também pode criar **objetos DataTable** dentro de um **DataSet** usando os métodos **Fill** ou **FillSchema** do objeto **DataAdapter** , ou de um esquema XML predefinido ou inferido usando os métodos **ReadXml**, **ReadXmlSchema**ou **InferXmlSchema** do **conjunto**de objetos.</span><span class="sxs-lookup"><span data-stu-id="d5a94-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="d5a94-108">Observe que depois de ter adicionado uma **DataTable** como um membro da coleção **Tables** de um **conjunto**de um DataSet, você não pode adicioná-lo à coleção de tabelas de qualquer outro **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="d5a94-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="d5a94-109">Quando você cria uma **DataTable**pela primeira vez, ela não tem um esquema (ou seja, uma estrutura).</span><span class="sxs-lookup"><span data-stu-id="d5a94-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="d5a94-110">Para definir o esquema da tabela, você deve criar e adicionar <xref:System.Data.DataColumn> objetos à coleção de **colunas** da tabela.</span><span class="sxs-lookup"><span data-stu-id="d5a94-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="d5a94-111">Você também pode definir uma coluna de chave primária para a tabela e criar e adicionar objetos de **restrição** à coleção de **restrições** da tabela.</span><span class="sxs-lookup"><span data-stu-id="d5a94-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="d5a94-112">Depois de definir o esquema para uma **DataTable**, você pode adicionar linhas de dados à tabela adicionando objetos **DataRow** à coleção **Rows** da tabela.</span><span class="sxs-lookup"><span data-stu-id="d5a94-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="d5a94-113">Não é necessário fornecer um valor para a <xref:System.Data.DataTable.TableName%2A> propriedade quando você cria uma **DataTable**; você pode especificar a propriedade em outro momento ou deixá-la vazia.</span><span class="sxs-lookup"><span data-stu-id="d5a94-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="d5a94-114">No entanto, quando você adiciona uma tabela sem um valor de **TableName** a um **conjunto**de dados, a tabela receberá um nome padrão incremental da tabela*N*, começando com "Table" para Table0.</span><span class="sxs-lookup"><span data-stu-id="d5a94-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5a94-115">Recomendamos que você evite a Convenção de nomenclatura "Table*N*" ao fornecer um valor de **TableName** , pois o nome que você fornece pode entrar em conflito com um nome de tabela padrão existente no **conjunto**de valores.</span><span class="sxs-lookup"><span data-stu-id="d5a94-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="d5a94-116">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d5a94-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="d5a94-117">O exemplo a seguir cria uma instância de um objeto **DataTable** e atribui a ele o nome "Customers".</span><span class="sxs-lookup"><span data-stu-id="d5a94-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="d5a94-118">O exemplo a seguir cria uma instância de uma **DataTable** adicionando-a à coleção **Tables** de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d5a94-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5a94-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="d5a94-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="d5a94-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="d5a94-120">DataTables</span></span>](datatables.md)
- <span data-ttu-id="d5a94-121">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)</span><span class="sxs-lookup"><span data-stu-id="d5a94-121">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md)</span></span>
- [<span data-ttu-id="d5a94-122">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="d5a94-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="d5a94-123">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="d5a94-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="d5a94-124">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d5a94-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
