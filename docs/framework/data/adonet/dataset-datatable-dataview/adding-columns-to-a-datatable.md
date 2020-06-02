---
title: Adicionando colunas a um DataTable
description: Uma DataTable contém objetos DataColumn referenciados pela propriedade Columns da tabela. Use este código de exemplo para adicionar colunas a uma tabela no ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286941"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="3c4ac-104">Adicionando colunas a um DataTable</span><span class="sxs-lookup"><span data-stu-id="3c4ac-104">Adding Columns to a DataTable</span></span>
<span data-ttu-id="3c4ac-105">Um <xref:System.Data.DataTable> contém uma coleção de <xref:System.Data.DataColumn> objetos referenciados pela propriedade **Columns** da tabela.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-105">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="3c4ac-106">Esta coleção de colunas, junto com quaisquer restrições, define o esquema, ou a estrutura, da tabela.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-106">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="3c4ac-107">Você cria objetos **DataColumn** em uma tabela usando o construtor **DataColumn** ou chamando o método **Add** da propriedade **Columns** da tabela, que é um <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="3c4ac-107">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="3c4ac-108">O método **Add** aceita argumentos de expressão **ColumnName**, **DataType**e **expression** opcionais e cria uma nova **DataColumn** como um membro da coleção.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-108">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="3c4ac-109">Ele também aceita um objeto **DataColumn** existente e o adiciona à coleção e retorna uma referência para a **DataColumn** adicionada, se solicitado.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-109">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="3c4ac-110">Como os objetos **DataTable** não são específicos de nenhuma fonte de dados, .NET Framework tipos são usados ao especificar o tipo de dados de uma **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-110">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="3c4ac-111">O exemplo a seguir adiciona quatro colunas a uma **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-111">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="3c4ac-112">No exemplo, observe que as propriedades da coluna **CustID** estão definidas para não permitir valores **DBNull** e para restringir valores a serem exclusivos.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-112">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="3c4ac-113">No entanto, se você definir a coluna **CustID** como a coluna de chave primária da tabela, a propriedade **AllowDBNull** será automaticamente definida como **false** e a propriedade **Unique** será definida automaticamente como **true**.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-113">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="3c4ac-114">Para obter mais informações, consulte [definindo chaves primárias](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="3c4ac-114">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3c4ac-115">Se um nome de coluna não for fornecido para uma coluna, a coluna receberá um nome padrão incremental da coluna*N,* começando com "Column1", quando ela for adicionada ao **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-115">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="3c4ac-116">Recomendamos que você evite a Convenção de nomenclatura de "coluna*N*" ao fornecer um nome de coluna, pois o nome que você fornece pode entrar em conflito com um nome de coluna padrão existente no **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-116">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="3c4ac-117">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-117">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="3c4ac-118">Se você estiver usando <xref:System.Xml.Linq.XElement> como <xref:System.Data.DataColumn.DataType%2A> de um <xref:System.Data.DataColumn> no <xref:System.Data.DataTable>, a serialização XML não funcionará quando você ler dados.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-118">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="3c4ac-119">Por exemplo, se você escreve um <xref:System.Xml.XmlDocument> usando o método `DataTable.WriteXml`, na serialização para XML há um nó pai adicional no <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-119">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3c4ac-120">Para resolver esse problema, use o tipo <xref:System.Data.SqlTypes.SqlXml> em vez de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-120">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3c4ac-121">`ReadXml` e `WriteXml` funcionam corretamente com <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="3c4ac-121">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c4ac-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="3c4ac-122">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="3c4ac-123">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="3c4ac-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="3c4ac-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="3c4ac-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="3c4ac-125">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c4ac-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
