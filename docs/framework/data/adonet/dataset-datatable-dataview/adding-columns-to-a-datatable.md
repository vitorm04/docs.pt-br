---
title: Adicionando colunas a um DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 77bf117b8835623d768f8b8b0ec3e4195174cad7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043944"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="b5be3-102">Adicionando colunas a um DataTable</span><span class="sxs-lookup"><span data-stu-id="b5be3-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="b5be3-103">Um <xref:System.Data.DataTable> contém uma coleção de <xref:System.Data.DataColumn> objetos referenciados pela propriedade **Columns** da tabela.</span><span class="sxs-lookup"><span data-stu-id="b5be3-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="b5be3-104">Esta coleção de colunas, junto com quaisquer restrições, define o esquema, ou a estrutura, da tabela.</span><span class="sxs-lookup"><span data-stu-id="b5be3-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="b5be3-105">Você cria objetos **DataColumn** em uma tabela usando o construtor **DataColumn** ou chamando o método **Add** da propriedade **Columns** da tabela, que é um <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="b5be3-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="b5be3-106">O método **Add** aceita argumentos de expressão **ColumnName**, **DataType**e **expression** opcionais e cria uma nova **DataColumn** como um membro da coleção.</span><span class="sxs-lookup"><span data-stu-id="b5be3-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="b5be3-107">Ele também aceita um objeto **DataColumn** existente e o adiciona à coleção e retorna uma referência para a **DataColumn** adicionada, se solicitado.</span><span class="sxs-lookup"><span data-stu-id="b5be3-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="b5be3-108">Como os objetos **DataTable** não são específicos de nenhuma fonte de dados, .NET Framework tipos são usados ao especificar o tipo de dados de uma **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="b5be3-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="b5be3-109">O exemplo a seguir adiciona quatro colunas a uma **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b5be3-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="b5be3-110">No exemplo, observe que as propriedades da coluna **CustID** estão definidas para não permitir valores **DBNull** e para restringir valores a serem exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b5be3-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="b5be3-111">No entanto, se você definir a coluna CustID como a coluna de chave primária da tabela, a propriedade **AllowDBNull** será automaticamente definida **como false** e a propriedade **Unique** será definida automaticamente como **true**.</span><span class="sxs-lookup"><span data-stu-id="b5be3-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="b5be3-112">Para obter mais informações, consulte [definindo chaves primárias](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b5be3-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b5be3-113">Se um nome de coluna não for fornecido para uma coluna, a coluna receberá um nome padrão incremental da coluna*N,* começando com "Column1", quando ela for adicionada aoDataColumnCollection.</span><span class="sxs-lookup"><span data-stu-id="b5be3-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="b5be3-114">Recomendamos que você evite a Convenção de nomenclatura de "coluna*N*" ao fornecer um nome de coluna, pois o nome que você fornece pode entrar em conflito com um nome de coluna padrão existente no DataColumnCollection.</span><span class="sxs-lookup"><span data-stu-id="b5be3-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="b5be3-115">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b5be3-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b5be3-116">Se você estiver usando <xref:System.Xml.Linq.XElement> como <xref:System.Data.DataColumn.DataType%2A> de um <xref:System.Data.DataColumn> no <xref:System.Data.DataTable>, a serialização XML não funcionará quando você ler dados.</span><span class="sxs-lookup"><span data-stu-id="b5be3-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="b5be3-117">Por exemplo, se você escreve um <xref:System.Xml.XmlDocument> usando o método `DataTable.WriteXml`, na serialização para XML há um nó pai adicional no <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b5be3-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b5be3-118">Para resolver esse problema, use o tipo <xref:System.Data.SqlTypes.SqlXml> em vez de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b5be3-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b5be3-119">`ReadXml` e `WriteXml` funcionam corretamente com <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="b5be3-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5be3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5be3-120">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="b5be3-121">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="b5be3-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="b5be3-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="b5be3-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- <span data-ttu-id="b5be3-123">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b5be3-123">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
