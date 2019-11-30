---
title: Provedor de reflexão (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: 0eeb223093d709cfe2722c2ad7cf622164eab32f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568869"
---
# <a name="reflection-provider-wcf-data-services"></a>Provedor de reflexão (WCF Data Services)

Além de expor dados de um modelo de dados por meio do Entity Framework, WCF Data Services pode expor dados que não são estritamente definidos em um modelo baseado em entidade. O provedor de reflexão expõe dados em classes que retornam tipos que implementam a interface <xref:System.Linq.IQueryable%601>. WCF Data Services usa reflexão para inferir um modelo de dados para essas classes e pode converter consultas baseadas em endereço em recursos em consultas baseadas em LINQ (consulta integrada de linguagem) em relação aos tipos de <xref:System.Linq.IQueryable%601> expostos.

> [!NOTE]
> Você pode usar o método <xref:System.Linq.Queryable.AsQueryable%2A> para retornar uma interface <xref:System.Linq.IQueryable%601> de qualquer classe que implemente a interface <xref:System.Collections.Generic.IEnumerable%601>. Isso permite que a maioria dos tipos de coleção genérica seja usada como uma fonte de dados para o serviço de dados.

O provedor de reflexão dá suporte a hierarquias de tipo. Para obter mais informações, consulte [como: criar um serviço de dados usando o provedor de reflexão](create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Inferindo o modelo de dados

Quando você cria o serviço de dados, o provedor infere o modelo de dados usando reflexão. A lista a seguir mostra como o provedor de reflexo infere o modelo de dados:

- Contêiner de entidade-a classe que expõe os dados como propriedades que retornam uma instância de <xref:System.Linq.IQueryable%601>. Quando você endereça um modelo de dados baseado em reflexão, o contêiner de entidade representa a raiz do serviço. Há suporte apenas para uma classe de contêiner de entidade para um namespace específico.

- Conjuntos de entidades – propriedades que retornam <xref:System.Linq.IQueryable%601> instâncias são tratadas como conjuntos de entidades. Os conjuntos de entidades são tratados diretamente como recursos na consulta. Somente uma propriedade no contêiner de entidade pode retornar uma instância de <xref:System.Linq.IQueryable%601> de um determinado tipo.

- Tipos de entidade – o tipo `T` do <xref:System.Linq.IQueryable%601> que o conjunto de entidades retorna. As classes que fazem parte de uma hierarquia de herança são convertidas pelo provedor de reflexão em uma hierarquia de tipo de entidade equivalente.

- Chaves de entidade: cada classe de dados que é um tipo de entidade deve ter uma propriedade de chave. Essa propriedade é atribuída com o atributo <xref:System.Data.Services.Common.DataServiceKeyAttribute> (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Você só deve aplicar o atributo <xref:System.Data.Services.Common.DataServiceKeyAttribute> a uma propriedade que possa ser usada para identificar exclusivamente uma instância do tipo de entidade. Esse atributo é ignorado quando aplicado a uma propriedade de navegação.

- Propriedades de tipo de entidade-além da chave de entidade, o provedor de reflexão trata as propriedades acessíveis e não indexadoras de uma classe que é um tipo de entidade da seguinte maneira:

  - Se a propriedade retornar um tipo primitivo, a propriedade será considerada uma propriedade de um tipo de entidade.

  - Se a propriedade retornar um tipo que também seja um tipo de entidade, a propriedade será considerada uma propriedade de navegação que representa a extremidade "One" de uma relação muitos para um ou um-para-um.

  - Se a propriedade retornar um <xref:System.Collections.Generic.IEnumerable%601> de um tipo de entidade, a propriedade será considerada uma propriedade de navegação que representa a extremidade "many" de uma relação um-para-muitos ou muitos para muitos.

  - Se o tipo de retorno da propriedade for um tipo de valor, a propriedade representará um tipo complexo.

> [!NOTE]
> Ao contrário de um modelo de dados baseado no modelo relacional de entidade, os modelos baseados no provedor de reflexão não entendem dados relacionais. Você deve usar a Entity Framework para expor dados relacionais por meio de WCF Data Services.

## <a name="data-type-mapping"></a>Mapeamento de tipo de dados

Quando um modelo de dados é inferido de classes .NET Framework, os tipos primitivos no modelo de dados são mapeados para .NET Framework tipos de dados da seguinte maneira:

|Tipo de dados do .NET Framework|Tipo do modelo de dados|
|------------------------------|---------------------|
|<xref:System.Byte> `[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> .NET Framework tipos de valores anuláveis são mapeados para os mesmos tipos de modelo de dados que os tipos de valores correspondentes que não podem ser atribuídos a um valor nulo.

## <a name="enabling-updates-in-the-data-model"></a>Habilitando atualizações no modelo de dados

Para permitir atualizações de dados que são expostas por meio desse tipo de modelo de dados, o provedor de reflexão define uma interface <xref:System.Data.Services.IUpdatable>. Essa interface instrui o serviço de dados sobre como manter as atualizações para os tipos expostos. Para habilitar atualizações para recursos que são definidos pelo modelo de dados, a classe de contêiner de entidade deve implementar a interface <xref:System.Data.Services.IUpdatable>. Para obter um exemplo de uma implementação da interface <xref:System.Data.Services.IUpdatable>, consulte [como criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).

A interface <xref:System.Data.Services.IUpdatable> requer que os seguintes membros sejam implementados para que as atualizações possam ser propagadas para a fonte de dados usando o provedor de reflexão:

|{1&gt;Membro&lt;1}|Descrição|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Fornece a funcionalidade para adicionar um objeto a uma coleção de objetos relacionados que são acessados de uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Fornece a funcionalidade que cancela as alterações pendentes nos dados.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Fornece a funcionalidade para criar um novo recurso no contêiner especificado.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Fornece a funcionalidade para excluir um recurso.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Fornece a funcionalidade para recuperar um recurso que é identificado por uma consulta específica e um nome de tipo.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Fornece a funcionalidade para retornar o valor de uma propriedade de um recurso.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Fornece a funcionalidade para remover um objeto para uma coleção de objetos relacionados acessados de uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Fornece a funcionalidade para atualizar um recurso especificado.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Fornece a funcionalidade para retornar o recurso que é representado por uma instância de objeto específica.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Fornece a funcionalidade para salvar todas as alterações pendentes.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Fornece a funcionalidade para definir uma referência de objeto relacionada usando uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Fornece a funcionalidade para definir o valor da propriedade de um recurso.|

## <a name="handling-concurrency"></a>Tratamento de simultaneidade

O WCF Data Services dá suporte a um modelo de simultaneidade otimista, permitindo que você defina um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. O <xref:System.Data.Services.ETagAttribute> é aplicado a um tipo de entidade para definir um token de simultaneidade no provedor de reflexão. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualizando o serviço de dados](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Usando LINQ to SQL com o provedor de reflexão

Como o Entity Framework é nativamente suportado por padrão, ele é o provedor de dados recomendado para usar dados relacionais com WCF Data Services. No entanto, você pode usar o provedor de reflexão para usar LINQ to SQL classes com um serviço de dados. Os conjuntos de resultados <xref:System.Data.Linq.Table%601> que são retornados por métodos na <xref:System.Data.Linq.DataContext> gerada pelo Object Relational Designer de LINQ to SQL (o/R Designer) implementam a interface <xref:System.Linq.IQueryable%601>. Isso permite que o provedor de reflexão Acesse esses métodos e retorne dados de entidade de SQL Server usando as classes de LINQ to SQL geradas. No entanto, como LINQ to SQL não implementa a interface <xref:System.Data.Services.IUpdatable>, você precisa adicionar uma classe parcial que estenda a classe existente <xref:System.Data.Linq.DataContext> parcial para adicionar a implementação de <xref:System.Data.Services.IUpdatable>. Para obter mais informações, consulte [como: criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
