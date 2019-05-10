---
title: 'Como: mapear relações de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 5a20253e7164dabc22529d2238e9e85610d83706
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624707"
---
# <a name="how-to-map-database-relationships"></a>Como: mapear relações de banco de dados
Você pode codificar como referências de propriedade em sua classe de entidade todas as relações de dados que serão sempre as mesmas. No banco de dados de exemplo Northwind, por exemplo, como os clientes geralmente fazem os pedidos, há sempre uma relação no modelo entre os clientes e seus pedidos.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] define um <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo para ajudar a representar essas relações. Esse atributo é usado junto com o <xref:System.Data.Linq.EntitySet%601> e <xref:System.Data.Linq.EntityRef%601> tipos para representar o que seria uma relação de chave estrangeira em um banco de dados. Para obter mais informações, consulte a seção atributo de associação [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Os valores de propriedade de armazenamento AssociationAttribute e ColumnAttribute diferenciam maiúsculas de minúsculas. Por exemplo, verifique se os valores usados no atributo para a propriedade AssociationAttribute.Storage coincidem maiúsculas e minúsculas para os nomes de propriedades correspondentes usados em outro lugar no código. Isso se aplica a todas as linguagens de programação .NET, mesmo aqueles que não são normalmente diferencia maiusculas de minúsculas, incluindo o Visual Basic. Para obter mais informações sobre a propriedade Storage, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 A maioria da relações são um-para-muitos, como no exemplo mais adiante neste tópico. Você também pode representar relações um-para-um e muitos-para-muitos da seguinte maneira:  
  
- -Para-um: Representa esse tipo de relação incluindo <xref:System.Data.Linq.EntitySet%601> em ambos os lados.  
  
     Por exemplo, considere uma `Customer` - `SecurityCode` relação, criada para que o código de segurança do cliente não será encontrado no `Customer` de tabela e pode ser acessado somente por pessoas autorizadas.  
  
- Muitos-para-muitos: Em relações muitos-para-muitos, a chave primária da tabela de link (também chamado de *junção* tabela) é formada geralmente por uma composição das chaves estrangeiras das outras duas tabelas.  
  
     Por exemplo, considere uma `Employee` - `Project` formado de relação muitos-para-muitos usando a tabela de link `EmployeeProject`. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige que essa relação seja modelada por meio de três classes: `Employee`, `Project` e `EmployeeProject`. Nesse caso, alterar a relação entre um `Employee` e um `Project` pode parecer exigir uma atualização da chave primária `EmployeeProject`. No entanto, essa situação é melhor modelada como excluindo um `EmployeeProject` existente e criando um novo `EmployeeProject`.  
  
    > [!NOTE]
    >  As relações em bancos de dados relacionais são normalmente modeladas como os valores de chave estrangeira que referenciam as chaves primárias em outras tabelas. Para navegar entre eles você associa explicitamente as duas tabelas usando um relacional *junção* operação.  
    >   
    >  Objetos no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], por outro lado, se referenciam entre si usando referências de propriedade ou coleções de referências que você navega usando *dot* notação.  
  
## <a name="example"></a>Exemplo  
 No exemplo de um-para-muitos a seguir, a classe `Customer` tem uma propriedade que declara a relação entre os clientes e seus pedidos.  A propriedade `Orders` é do tipo <xref:System.Data.Linq.EntitySet%601>. Este tipo significa que essa relação é de um-para-muitos (um cliente para vários pedidos). A propriedade <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> é usada para descrever como essa associação é realizada, a saber, especificando o nome da propriedade na classe relacionada a ser comparada com essa. Neste exemplo, o `CustomerID` propriedade é comparada, assim como um banco de dados *junção* compararia esse valor da coluna.  
  
> [!NOTE]
>  Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar uma associação entre classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Você também pode reverter a situação. Em vez de usar a classe `Customer` para descrever a associação entre clientes e pedidos, você pode usar a classe `Order`. A classe `Order` usa o tipo <xref:System.Data.Linq.EntityRef%601> para descrever a relação de volta para o cliente, como no exemplo de código a seguir.  
  
> [!NOTE]
>  O <xref:System.Data.Linq.EntityRef%601> classe oferece suporte *carregamento adiado*. Para obter mais informações, *ver* [adiada versus imediata Carregando](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
