---
title: Modelo de objeto LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 7a424f289bb4ffba102d1023909b139ac2a70c33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503736"
---
# <a name="the-linq-to-sql-object-model"></a>Modelo de objeto LINQ to SQL
No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], um modelo de objeto expressado na linguagem de programação do desenvolvedor é mapeado para o modelo de dados de um banco de dados relacional. Assim, as operações de dados são conduzidas de acordo com o modelo de objeto.  
  
 Neste cenário, você não emite comandos de banco de dados (por exemplo, `INSERT`) para o banco de dados. Em vez disso, você altera valores e executa métodos em seu modelo de objeto. Se você quiser consultar o banco de dados ou enviar alterações para ele, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converterá suas solicitações em comandos SQL corretos e enviará esses comandos para o banco de dados.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Os elementos mais fundamentais no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto e sua relação com elementos no modelo de dados relacional estão resumidos na tabela a seguir:  
  
|Modelo de objeto LINQ to SQL|Modelo de dados relacional|  
|------------------------------|---------------------------|  
|Classe de entidade|Tabela|  
|Membro de classe|Column|  
|Associação|Relação de chave estrangeira|  
|Método|Função ou procedimento armazenado|  
  
> [!NOTE]
>  As descrições a seguir supõem que você tenha noções básicas sobre o modelo de dados relacionais e de suas regras.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>Classes de entidade e tabelas de banco de dados LINK to SQL  
 Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uma tabela de banco de dados é representada por um *classe de entidade*. Uma classe de entidade é como qualquer outra classe que você pode criar, exceto pelo fato de que você anota a classe usando informações especiais que associam a classe a uma tabela de banco de dados. Para fazer essa anotação, adicione um atributo personalizado (<xref:System.Data.Linq.Mapping.TableAttribute>) à sua declaração de classe, como no exemplo a seguir:  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Somente as instâncias de classes declaradas como tabelas (ou seja, classes de entidade) podem ser salvas no banco de dados.  
  
 Para obter mais informações, consulte a seção atributo de tabela [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Membros de classe e colunas de banco de dados LINK to SQL  
 Além de associar classes a tabelas, atribua campos ou propriedades para representar colunas de banco de dados. Para essa finalidade, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] define o atributo <xref:System.Data.Linq.Mapping.ColumnAttribute>, como no exemplo a seguir:  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Somente campos e propriedades mapeados para colunas são persistidos no banco de dados ou recuperados dele. Aqueles não declarados como colunas são considerados partes transitórias da lógica do aplicativo.  
  
 O atributo <xref:System.Data.Linq.Mapping.ColumnAttribute> tem uma variedade de propriedades que é possível usar para personalizar esses membros que representam colunas (por exemplo, designando um membro como representante de uma coluna de chave primária). Para obter mais informações, consulte a seção atributo de coluna [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>Associações e relações de chave estrangeira de banco de dados LINK to SQL  
 Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], representam as associações de banco de dados (como chave estrangeira para relações de chave primária) aplicando o <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo. No seguinte segmento de código, o `Order` classe contém uma `Customer` propriedade que tem um <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo. Essa propriedade e seu atributo fornecem a classe `Order` que tem uma relação com a classe `Customer`.  
  
 O exemplo de código a seguir mostra a propriedade `Customer` da classe `Order`.  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Para obter mais informações, consulte a seção atributo de associação [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Métodos e procedimentos armazenados de banco de dados LINQ to SQL  
 O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte a procedimentos armazenados e a funções definidas pelo usuário. No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você mapeia essas abstrações definidas pelo banco de dados para objetos de cliente para que você pode acessá-los de maneira fortemente tipada do código do cliente. As assinaturas de método são a mais possível similares às assinaturas dos procedimentos e das funções definidas no banco de dados. É possível usar o IntelliSense para descobrir esses métodos.  
  
 Um conjunto de resultados que é retornado por uma chamada a um procedimento mapeado é uma coleção fortemente tipada.  
  
 O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeia procedimentos armazenados e funções para métodos usando os atributos <xref:System.Data.Linq.Mapping.FunctionAttribute> e <xref:System.Data.Linq.Mapping.ParameterAttribute>. Os métodos que representam procedimentos armazenados são diferentes daqueles que representam funções definidas pelo usuário pela propriedade <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>. Se essa propriedade for definida como `false` (padrão), o método representará um procedimento armazenado. Se ela for definida como `true`, o método representará uma função de banco de dados.  
  
> [!NOTE]
>  Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar métodos mapeados para procedimentos armazenados e funções definidas pelo usuário.  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Para obter mais informações, consulte as seções de atributo de função, o atributo de procedimento armazenado e atributo de parâmetro de [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) e [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Consulte também
- [Mapeamento baseado em atributos](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
