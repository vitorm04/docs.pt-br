---
title: "Como mapear relações de banco de dados"
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
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: aa771fbde889febb269f49603f7d2a2ac5c67784
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-map-database-relationships"></a>Como mapear relações de banco de dados
Você pode codificar como referências de propriedade em sua classe de entidade todas as relações de dados que serão sempre as mesmas. No banco de dados de exemplo Northwind, por exemplo, como os clientes geralmente fazem os pedidos, há sempre uma relação no modelo entre os clientes e seus pedidos.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]define um <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo para representar essas relações. Este atributo é usado junto com o <xref:System.Data.Linq.EntitySet%601> e <xref:System.Data.Linq.EntityRef%601> tipos para representar o que seria uma relação de chave estrangeira em um banco de dados. Para obter mais informações, consulte a seção de atributo de associação de [mapeamento baseado no atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Os valores de propriedade de armazenamento AssociationAttribute e ColumnAttribute diferenciam maiúsculas de minúsculas. Por exemplo, verifique se os valores usados no atributo para a propriedade AssociationAttribute.Storage coincidem maiúsculas e minúsculas para os nomes de propriedades correspondentes usados em outro lugar no código. Isso se aplica a todas as linguagens de programação .NET, mesmo as que normalmente não diferenciam maiúsculas de minúsculas, incluindo [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Para obter mais informações sobre a propriedade Storage, consulte <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 A maioria da relações são um-para-muitos, como no exemplo mais adiante neste tópico. Você também pode representar relações um-para-um e muitos-para-muitos da seguinte maneira:  
  
-   Um-para-um: representa esse tipo de relação incluindo <xref:System.Data.Linq.EntitySet%601> em ambos os lados.  
  
     Por exemplo, considere um `Customer` - `SecurityCode` relação, criada para que o código de segurança do cliente não será localizado no `Customer` da tabela e pode ser acessado somente por pessoas autorizadas tenham acesso.  
  
-   Muitos-para-muitos: em relações muitos-para-muitos, a chave primária da tabela de link (também chamado de *junção* tabela) geralmente é formada por uma combinação de chaves estrangeiras de outras duas tabelas.  
  
     Por exemplo, considere um `Employee` - `Project` relação muitos-para-muitos formado usando a tabela de link `EmployeeProject`. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige que essa relação seja modelada por meio de três classes: `Employee`, `Project` e `EmployeeProject`. Nesse caso, alterar a relação entre um `Employee` e um `Project` pode parecer exigir uma atualização da chave primária `EmployeeProject`. No entanto, essa situação é melhor modelada como excluindo um `EmployeeProject` existente e criando um novo `EmployeeProject`.  
  
    > [!NOTE]
    >  As relações em bancos de dados relacionais são normalmente modeladas como os valores de chave estrangeira que referenciam as chaves primárias em outras tabelas. Para navegar entre eles você associar explicitamente as duas tabelas usando um relacional *junção* operação.  
    >   
    >  Objetos no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], no outro lado, referem-se entre si usando referências de propriedade ou coleções de referências que você navegue usando *ponto* notação.  
  
## <a name="example"></a>Exemplo  
 No exemplo de um-para-muitos a seguir, a classe `Customer` tem uma propriedade que declara a relação entre os clientes e seus pedidos.  A propriedade `Orders` é do tipo <xref:System.Data.Linq.EntitySet%601>. Este tipo significa que essa relação é de um-para-muitos (um cliente para vários pedidos). A propriedade <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> é usada para descrever como essa associação é realizada, a saber, especificando o nome da propriedade na classe relacionada a ser comparada com essa. Neste exemplo, o `CustomerID` propriedade é comparada, assim como um banco de dados *junção* compara esse valor da coluna.  
  
> [!NOTE]
>  Se você estiver usando o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], poderá usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar uma associação entre classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Você também pode reverter a situação. Em vez de usar a classe `Customer` para descrever a associação entre clientes e pedidos, você pode usar a classe `Order`. A classe `Order` usa o tipo <xref:System.Data.Linq.EntityRef%601> para descrever a relação de volta para o cliente, como no exemplo de código a seguir.  
  
> [!NOTE]
>  O <xref:System.Data.Linq.EntityRef%601> classe oferece suporte *carregamento diferido*. Para obter mais informações, *consulte* [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [O LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
