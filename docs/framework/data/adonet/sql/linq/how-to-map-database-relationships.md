---
title: Como mapear relações de banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148368"
---
# <a name="how-to-map-database-relationships"></a>Como mapear relações de banco de dados
Você pode codificar como referências de propriedade em sua classe de entidade todas as relações de dados que serão sempre as mesmas. No banco de dados de exemplo Northwind, por exemplo, como os clientes geralmente fazem os pedidos, há sempre uma relação no modelo entre os clientes e seus pedidos.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]define um <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo para ajudar a representar tais relações. Esse atributo é <xref:System.Data.Linq.EntitySet%601> usado <xref:System.Data.Linq.EntityRef%601> em conjunto com os e tipos para representar o que seria uma relação-chave estrangeira em um banco de dados. Para obter mais informações, consulte a seção Atributo de associação de [mapeamento baseado em atributos](attribute-based-mapping.md).  
  
> [!NOTE]
> Os valores de propriedade de armazenamento AssociationAttribute e ColumnAttribute diferenciam maiúsculas de minúsculas. Por exemplo, verifique se os valores usados no atributo para a propriedade AssociationAttribute.Storage coincidem maiúsculas e minúsculas para os nomes de propriedades correspondentes usados em outro lugar no código. Isso se aplica a todas as linguagens de programação .NET, mesmo aquelas que normalmente não são sensíveis a casos, incluindo o Visual Basic. Para obter mais informações sobre a propriedade Storage, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 A maioria da relações são um-para-muitos, como no exemplo mais adiante neste tópico. Você também pode representar relações um-para-um e muitos-para-muitos da seguinte maneira:  
  
- Um-para-um: representa esse tipo de relação incluindo <xref:System.Data.Linq.EntitySet%601> em ambos os lados.  
  
     Por exemplo, `Customer` - `SecurityCode` considere um relacionamento, criado para que o código de `Customer` segurança do cliente não seja encontrado na tabela e possa ser acessado apenas por pessoas autorizadas.  
  
- Muitos para muitos: Em muitos relacionamentos, a chave principal da tabela de link (também chamada de tabela *de junção)* é frequentemente formada por um composto das teclas estrangeiras das outras duas tabelas.  
  
     Por exemplo, `Employee` - `Project` considere uma relação de muitos a `EmployeeProject`muitos formados usando tabela de link . O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige que essa relação seja modelada por meio de três classes: `Employee`, `Project` e `EmployeeProject`. Nesse caso, alterar a relação entre um `Employee` e um `Project` pode parecer exigir uma atualização da chave primária `EmployeeProject`. No entanto, essa situação é melhor modelada como excluindo um `EmployeeProject` existente e criando um novo `EmployeeProject`.  
  
    > [!NOTE]
    > As relações em bancos de dados relacionais são normalmente modeladas como os valores de chave estrangeira que referenciam as chaves primárias em outras tabelas. Para navegar entre elas, você associa explicitamente as duas tabelas usando uma operação de *adesão* relacional.  
    >
    >  Objetos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]em , por outro lado, referem-se uns aos outros usando referências de propriedade ou coleções de referências que você navega usando notação *de ponto.*  
  
## <a name="example"></a>Exemplo  
 No exemplo de um-para-muitos a seguir, a classe `Customer` tem uma propriedade que declara a relação entre os clientes e seus pedidos.  A propriedade `Orders` é do tipo <xref:System.Data.Linq.EntitySet%601>. Este tipo significa que essa relação é de um-para-muitos (um cliente para vários pedidos). A propriedade <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> é usada para descrever como essa associação é realizada, a saber, especificando o nome da propriedade na classe relacionada a ser comparada com essa. Neste exemplo, `CustomerID` a propriedade é comparada, assim como uma *adesão ao* banco de dados compararia esse valor de coluna.  
  
> [!NOTE]
> Se você estiver usando o Visual Studio, você pode usar o Object Relational Designer para criar uma associação entre classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Você também pode reverter a situação. Em vez de usar a classe `Customer` para descrever a associação entre clientes e pedidos, você pode usar a classe `Order`. A classe `Order` usa o tipo <xref:System.Data.Linq.EntityRef%601> para descrever a relação de volta para o cliente, como no exemplo de código a seguir.  
  
> [!NOTE]
> A <xref:System.Data.Linq.EntityRef%601> classe suporta *carregamento adiado.* Para obter mais informações, *consulte* [Deferred versus Carga Imediata](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Confira também

- [Como personalizar classes de entidade usando o Editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [O modelo de objeto LINQ para SQL](the-linq-to-sql-object-model.md)
