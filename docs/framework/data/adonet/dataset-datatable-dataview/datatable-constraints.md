---
title: "Restrições de DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a>Restrições de DataTable
Você pode usar restrições para impor restrições nos dados em um <xref:System.Data.DataTable>, para manter a integridade dos dados. Uma restrição é uma regra automática, aplicada a uma coluna ou colunas relacionadas, que determina o curso de ação quando o valor de uma linha é modificado de alguma maneira. As restrições são aplicadas quando o `System.Data.DataSet.EnforceConstraints` propriedade o <xref:System.Data.DataSet> é **true**. Para um exemplo de código que mostra como definir a propriedade `EnforceConstraints`, consulte o tópico de referência <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Há dois tipos de restrições no ADO.NET: o <xref:System.Data.ForeignKeyConstraint> e o <xref:System.Data.UniqueConstraint>. Por padrão, ambas as restrições são criadas automaticamente quando você criar uma relação entre duas ou mais tabelas adicionando um <xref:System.Data.DataRelation> para o **conjunto de dados**. No entanto, você pode desativar esse comportamento especificando **createConstraints** = **false** ao criar a relação.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 Um **ForeignKeyConstraint** impõe regras sobre como as atualizações e exclusões para tabelas relacionadas são propagadas. Por exemplo, se um valor em uma linha de uma tabela é atualizado ou excluído e mesmo valor também é usado em uma ou mais tabelas relacionadas, uma **ForeignKeyConstraint** determina o que acontece nas tabelas relacionadas.  
  
 O <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> e <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriedades do **ForeignKeyConstraint** definir a ação a ser tomada quando o usuário tenta excluir ou atualizar uma linha em uma tabela relacionada. A tabela a seguir descreve as diferentes configurações disponíveis para o **DeleteRule** e **UpdateRule** propriedades do **ForeignKeyConstraint**.  
  
|Configuração de regra|Descrição|  
|------------------|-----------------|  
|**Em cascata**|Excluir ou atualizar linhas relacionadas.|  
|**SetNull**|Defina os valores nas linhas relacionadas para **DBNull**.|  
|**SetDefault**|Definir valores em linhas relacionadas para o valor padrão.|  
|**Nenhum**|Nenhuma ação em linhas relacionadas. Esse é o padrão.|  
  
 Um **ForeignKeyConstraint** pode restringir, bem como propagar, alterações de colunas relacionadas. Dependendo das propriedades definidas para o **ForeignKeyConstraint** de uma coluna, se o **EnforceConstraints** propriedade o **conjunto de dados** é **true**, executar determinadas operações na linha pai resultará em uma exceção. Por exemplo, se o **DeleteRule** propriedade o **ForeignKeyConstraint** é **nenhum**, uma linha pai não pode ser excluída se tiver linhas filho.  
  
 Você pode criar uma restrição de chave estrangeira entre colunas únicas ou uma matriz de colunas usando o **ForeignKeyConstraint** construtor. Passar resultante **ForeignKeyConstraint** o objeto para o **adicionar** método da tabela de **restrições** propriedade, que é um **ConstraintCollection**. Você também pode passar argumentos de construtor para várias sobrecargas do **adicionar** método de um **ConstraintCollection** para criar um **ForeignKeyConstraint**.  
  
 Ao criar um **ForeignKeyConstraint**, você pode passar o **DeleteRule** e **UpdateRule** valores para o construtor como argumentos, ou você podem defini-las como propriedades como o exemplo a seguir (onde o **DeleteRule** valor é definido como **nenhum**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 Alterações em linhas podem ser aceitos usando o **AcceptChanges** método ou cancelada usando o **RejectChanges** método o **DataSet**, **DataTable**, ou **DataRow**. Quando um **DataSet** contém **ForeignKeyConstraints**, invocando o **AcceptChanges** ou **RejectChanges** métodos impõe o  **AcceptRejectRule**. O **AcceptRejectRule** propriedade o **ForeignKeyConstraint** determina qual ação será tomada no filho linhas quando **AcceptChanges** ou  **RejectChanges** é chamado em linha pai.  
  
 A tabela a seguir lista as configurações disponíveis para o **AcceptRejectRule**.  
  
|Configuração de regra|Descrição|  
|------------------|-----------------|  
|**Em cascata**|Aceitar ou rejeitar alterações em linhas filho.|  
|**Nenhum**|Nenhuma ação em linhas filho. Esse é o padrão.|  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Data.ForeignKeyConstraint>, define várias das suas propriedades, incluindo <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> e adiciona-os ao <xref:System.Data.ConstraintCollection> de um objeto <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 O **UniqueConstraint** objeto, que pode ser atribuído a uma única coluna ou em uma matriz de colunas em um **DataTable**, garante que todos os dados de coluna ou colunas especificadas é exclusivo por linha. Você pode criar uma restrição exclusiva para uma coluna ou uma matriz de colunas usando o **UniqueConstraint** construtor. Passar resultante **UniqueConstraint** o objeto para o **adicionar** método da tabela de **restrições** propriedade, que é um **ConstraintCollection**. Você também pode passar argumentos de construtor para várias sobrecargas do **adicionar** método de um **ConstraintCollection** para criar um **UniqueConstraint**. Ao criar um **UniqueConstraint** para uma coluna ou colunas, opcionalmente, você pode especificar se a coluna ou colunas são uma chave primária.  
  
 Você também pode criar uma restrição exclusiva para uma coluna, definindo o **Unique** propriedade da coluna a ser **true**. Como alternativa, definindo o **Unique** propriedade de uma única coluna para **false** remove qualquer restrição exclusiva que possam existir. Definir uma coluna ou colunas como uma chave primária para uma tabela criará automaticamente uma restrição exclusiva para a coluna ou colunas especificadas. Se você remover uma coluna do **PrimaryKey** propriedade de um **DataTable**, o **UniqueConstraint** é removido.  
  
 O exemplo a seguir cria um **UniqueConstraint** para duas colunas de uma **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
