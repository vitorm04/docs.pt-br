---
title: Adicionando colunas a um DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 8ee47ddce273e564673d96d2b2e276b68879373f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760460"
---
# <a name="adding-columns-to-a-datatable"></a>Adicionando colunas a um DataTable
Um <xref:System.Data.DataTable> contém uma coleção de <xref:System.Data.DataColumn> objetos referenciados pelo **colunas** propriedade da tabela. Esta coleção de colunas, junto com quaisquer restrições, define o esquema, ou a estrutura, da tabela.  
  
 Criar **DataColumn** objetos dentro de uma tabela usando o **DataColumn** construtor, ou chamando o **adicionar** método o **colunas**propriedade da tabela, que é um <xref:System.Data.DataColumnCollection>. O **adicionar** método aceita opcional **ColumnName**, **DataType**, e **expressão** argumentos e cria um novo  **DataColumn** como um membro da coleção. Ele também aceita um existente **DataColumn** do objeto e adiciona-o à coleção e retorna uma referência ao adicionado **DataColumn** se solicitado. Porque **DataTable** objetos não são específicos para qualquer fonte de dados, os tipos do .NET Framework são usados ao especificar o tipo de dados de um **DataColumn**.  
  
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
  
 No exemplo, observe que as propriedades para o **CustID** coluna estão definidas para não permitir **DBNull** valores e para restringir os valores exclusivos. No entanto, se você definir o **CustID** coluna como coluna de chave primária da tabela, o **AllowDBNull** propriedade será definida automaticamente **false** e o **Unique** propriedade será definida automaticamente **true**. Para obter mais informações, consulte [definindo chaves primárias](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Se um nome de coluna não for fornecido para uma coluna, a coluna recebe um nome padrão incremental da coluna*N,* começando com "Coluna1", quando ele é adicionado para o **DataColumnCollection**. É recomendável que você evite a convenção de nomenclatura de "coluna*N*" quando você fornece um nome de coluna, porque o nome que você fornecer pode entrar em conflito com um nome de coluna padrão existente no **DataColumnCollection**. Se o nome fornecido já existir, será gerada uma exceção.  
  
 Se você estiver usando <xref:System.Xml.Linq.XElement> como <xref:System.Data.DataColumn.DataType%2A> de um <xref:System.Data.DataColumn> no <xref:System.Data.DataTable>, a serialização XML não funcionará quando você ler dados. Por exemplo, se você escreve um <xref:System.Xml.XmlDocument> usando o método `DataTable.WriteXml`, na serialização para XML há um nó pai adicional no <xref:System.Xml.Linq.XElement>. Para resolver esse problema, use o tipo <xref:System.Data.SqlTypes.SqlXml> em vez de <xref:System.Xml.Linq.XElement>. `ReadXml` e `WriteXml` funcionam corretamente com <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
