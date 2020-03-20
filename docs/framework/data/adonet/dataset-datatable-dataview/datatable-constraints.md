---
title: Restrições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151280"
---
# <a name="datatable-constraints"></a>Restrições de DataTable
Você pode usar restrições para impor restrições nos dados em um <xref:System.Data.DataTable>, para manter a integridade dos dados. Uma restrição é uma regra automática, aplicada a uma coluna ou colunas relacionadas, que determina o curso de ação quando o valor de uma linha é modificado de alguma maneira. As restrições são `System.Data.DataSet.EnforceConstraints` impostas <xref:System.Data.DataSet> quando a propriedade do é **verdadeiro.** Para um exemplo de código que mostra como definir a propriedade `EnforceConstraints`, consulte o tópico de referência <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Há dois tipos de restrições no ADO.NET: o <xref:System.Data.ForeignKeyConstraint> e o <xref:System.Data.UniqueConstraint>. Por padrão, ambas as restrições são criadas automaticamente quando você cria <xref:System.Data.DataRelation> uma relação entre duas ou mais tabelas adicionando a ao **Conjunto de dados**. No entanto, você pode desativar esse comportamento especificando **createRestrições** = **falsas** ao criar a relação.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 Uma **Restrição de Tecla Estrangeira** impõe regras sobre como as atualizações e exclusões em tabelas relacionadas são propagadas. Por exemplo, se um valor em uma linha de uma tabela for atualizado ou excluído, e esse mesmo valor também for usado em uma ou mais tabelas relacionadas, uma **ForeignKeyRestrição** determina o que acontece nas tabelas relacionadas.  
  
 As <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriedades da **ForeignKeyConstraint** definem a ação a ser tomada quando o usuário tenta excluir ou atualizar uma linha em uma tabela relacionada. A tabela a seguir descreve as diferentes configurações disponíveis para as propriedades **DeleteRule** e **UpdateRule** da **ForeignKeyConstraint**.  
  
|Configuração de regra|Descrição|  
|------------------|-----------------|  
|**Cascata**|Excluir ou atualizar linhas relacionadas.|  
|**SetNull**|Defina valores em linhas relacionadas a **DBNull**.|  
|**SetDefault**|Definir valores em linhas relacionadas para o valor padrão.|  
|**Nenhum**|Nenhuma ação em linhas relacionadas. Esse é o padrão.|  
  
 Uma **Restrição de Tecla Estrangeira** pode restringir, bem como propagar, alterações em colunas relacionadas. Dependendo das propriedades definidas para a **Configuração de Chave Estrangeira** de uma coluna, se a propriedade **EnforceConstraints** do **DataSet for** **verdadeira,** a realização de certas operações na linha pai resultará em uma exceção. Por exemplo, se a propriedade **DeleteRule** da **ForeignKeyConstraint** for **None**, uma linha pai não poderá ser excluída se tiver alguma linha de filho.  
  
 Você pode criar uma restrição de chave estrangeira entre colunas únicas ou entre uma matriz de colunas usando o construtor **ForeignKeyConstraint.** Passe o objeto **ForeignKeyConstraint** resultante para o método **Add** da propriedade **Restrições** da tabela, que é uma Coleção de **Restrições**. Você também pode passar argumentos de construtor para várias sobrecargas do método **Add** de uma **ConstraintCollection** para criar uma **Restrição de Teceladeria estrangeira**.  
  
 Ao criar uma **Configuração de Chave Estrangeira,** você pode passar os valores **DeleteRule** e **UpdateRule** para o construtor como argumentos, ou você pode defini-los como propriedades como no exemplo a seguir (quando o valor **DeleteRule** é definido como **Nenhum**).  
  
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
 Alterações nas linhas podem ser aceitas usando o método **AcceptChanges** ou canceladas usando o método **RejectChanges** do **DataSet,** **DataTable**ou **DataRow**. Quando um **Conjunto de Dados** contém **Restrições de Tecelanderna,** invocar os métodos **AcceptChanges** ou **RejectChanges** impõe a **Regra de Aceitação**. A propriedade **AcceptRejectRule** da **ForeignKeyConstraint** determina qual ação será tomada nas linhas de filho quando **As alterações aceitas** ou **rejeições** são chamadas na linha pai.  
  
 A tabela a seguir lista as configurações disponíveis para **a AcceptRejectRule**.  
  
|Configuração de regra|Descrição|  
|------------------|-----------------|  
|**Cascata**|Aceitar ou rejeitar alterações em linhas filho.|  
|**Nenhum**|Nenhuma ação em linhas filho. Esse é o padrão.|  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Data.ForeignKeyConstraint>, define várias das suas propriedades, incluindo <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> e adiciona-os ao <xref:System.Data.ConstraintCollection> de um objeto <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 O objeto **UniqueConstraint,** que pode ser atribuído a uma única coluna ou a uma matriz de colunas em uma Tabela de **Dados,** garante que todos os dados na coluna ou colunas especificadas sejam únicos por linha. Você pode criar uma restrição única para uma coluna ou matriz de colunas usando o construtor **UniqueConstraint.** Passe o objeto **UniqueConstraint** resultante para o método **Add** da propriedade **Restrições** da tabela, que é uma Coleção de **Restrições**. Você também pode passar argumentos de construtor para várias sobrecargas do método **Add** de uma **ConstraintCollection** para criar uma **UniqueConstraint**. Ao criar uma **Restrição Única** para uma coluna ou colunas, você pode especificar opcionalmente se a coluna ou as colunas são uma chave principal.  
  
 Você também pode criar uma restrição única para uma coluna definindo a propriedade **Unique** da coluna como **verdadeira**. Alternativamente, definir a propriedade **Unique** de uma única coluna para **falsa** remove qualquer restrição única que possa existir. Definir uma coluna ou colunas como uma chave primária para uma tabela criará automaticamente uma restrição exclusiva para a coluna ou colunas especificadas. Se você remover uma coluna da propriedade **PrimaryKey** de uma Tabela de **Dados,** a **'Restrições únicas'** será removida.  
  
 O exemplo a seguir cria uma **Restrição Única** para duas colunas de uma Tabela de **Dados**.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Definição de esquema de DataTable](datatable-schema-definition.md)
- [DataSets, DataTables e DataViews](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
