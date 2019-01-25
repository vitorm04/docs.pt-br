---
title: Adicionando colunas a um DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538255"
---
# <a name="adding-columns-to-a-datatable"></a>Adicionando colunas a um DataTable
Um <xref:System.Data.DataTable> contém uma coleção de <xref:System.Data.DataColumn> objetos referenciados pela **colunas** propriedade da tabela. Esta coleção de colunas, junto com quaisquer restrições, define o esquema, ou a estrutura, da tabela.  
  
 Você cria **DataColumn** objetos dentro de uma tabela usando o **DataColumn** construtor, ou chamando o **Add** método do **colunas**propriedade de tabela, que é um <xref:System.Data.DataColumnCollection>. O **Add** método aceita opcional **ColumnName**, **DataType**, e **expressão** argumentos e cria um novo  **DataColumn** como um membro da coleção. Ele também aceita um existente **DataColumn** do objeto e adiciona-o à coleção e retorna uma referência ao adicionado **DataColumn** se solicitado. Porque **DataTable** objetos não são específicos para qualquer fonte de dados, tipos do .NET Framework são usados ao especificar o tipo de dados de uma **DataColumn**.  
  
 O exemplo a seguir adiciona quatro colunas para um **DataTable**.  
  
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
  
 No exemplo, observe que as propriedades para o **CustID** coluna estão configuradas para não permitir **DBNull** valores e para restringir os valores sejam exclusivos. No entanto, se você definir a **CustID** coluna como a coluna de chave primária da tabela, o **AllowDBNull** propriedade será definida automaticamente como **false** e o **Unique** propriedade será definida automaticamente como **verdadeira**. Para obter mais informações, consulte [definindo chaves primárias](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Se um nome de coluna não for fornecido para uma coluna, a coluna recebe um nome padrão incremental de coluna*N,* começando com "Column1", quando ele é adicionado para o **DataColumnCollection**. É recomendável que você evite a convenção de nomenclatura de "coluna*N*" quando você fornece um nome de coluna, porque o nome fornecido pode entrar em conflito com um nome de coluna padrão existente na **DataColumnCollection**. Se o nome fornecido já existir, será gerada uma exceção.  
  
 Se você estiver usando <xref:System.Xml.Linq.XElement> como <xref:System.Data.DataColumn.DataType%2A> de um <xref:System.Data.DataColumn> no <xref:System.Data.DataTable>, a serialização XML não funcionará quando você ler dados. Por exemplo, se você escreve um <xref:System.Xml.XmlDocument> usando o método `DataTable.WriteXml`, na serialização para XML há um nó pai adicional no <xref:System.Xml.Linq.XElement>. Para resolver esse problema, use o tipo <xref:System.Data.SqlTypes.SqlXml> em vez de <xref:System.Xml.Linq.XElement>. `ReadXml` e `WriteXml` funcionam corretamente com <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
