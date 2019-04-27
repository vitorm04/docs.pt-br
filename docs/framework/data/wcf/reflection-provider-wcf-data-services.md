---
title: Provedor de reflexão (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: 5239117d375ef9c305863ff847c3aff3af91234d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875778"
---
# <a name="reflection-provider-wcf-data-services"></a>Provedor de reflexão (WCF Data Services)

Além de expor dados de um modelo de dados por meio do Entity Framework, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pode expor os dados que não é estritamente definidos em um modelo baseado na entidade. O provedor de reflexão expõe dados nas classes que retornam tipos que implementam o <xref:System.Linq.IQueryable%601> interface. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa a reflexão para inferir um modelo de dados para essas classes e pode traduzir consultas baseadas em endereço, com base nos recursos consulta integrada à linguagem (LINQ)-com base em consultas em relação a exposta <xref:System.Linq.IQueryable%601> tipos.

> [!NOTE]
> Você pode usar o <xref:System.Linq.Queryable.AsQueryable%2A> método para retornar um <xref:System.Linq.IQueryable%601> interface de qualquer classe que implementa o <xref:System.Collections.Generic.IEnumerable%601> interface. Isso permite que os tipos de coleção mais genéricos ser usado como uma fonte de dados para seu serviço de dados.

O provedor de reflexão dá suporte a hierarquias de tipo. Para obter mais informações, confira [Como: Criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Inferindo o modelo de dados

Quando você cria o serviço de dados, o provedor deduz o modelo de dados por meio de reflexão. A lista a seguir mostra como o provedor de reflexão infere o modelo de dados:

- Contêiner de entidade – a classe que expõe os dados como propriedades que retornam um <xref:System.Linq.IQueryable%601> instância. Ao lidar com um modelo de dados com base em reflexão, o contêiner de entidade representa a raiz do serviço. Classe de contêiner de apenas uma entidade tem suporte para um namespace específico.

- Conjuntos de entidades - propriedades que retornam <xref:System.Linq.IQueryable%601> instâncias são tratadas como conjuntos de entidades. Conjuntos de entidades são tratados diretamente como recursos na consulta. Apenas uma propriedade no contêiner de entidade pode retornar um <xref:System.Linq.IQueryable%601> instância de um determinado tipo.

- Tipos de entidade - o tipo `T` do <xref:System.Linq.IQueryable%601> que o conjunto de entidades retorna. Classes que fazem parte de uma hierarquia de herança são convertidas pelo provedor de reflexão em uma hierarquia de tipo de entidade equivalentes.

- Chaves de entidade – cada classe de dados que é um tipo de entidade deve ter uma propriedade de chave. Essa propriedade é atribuída com o <xref:System.Data.Services.Common.DataServiceKeyAttribute> atributo (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > Você deve se aplicar somente a <xref:System.Data.Services.Common.DataServiceKeyAttribute> do atributo a uma propriedade que pode ser usada para identificar exclusivamente uma instância do tipo de entidade. Esse atributo é ignorado quando aplicado a uma propriedade de navegação.

- Propriedades do tipo de entidade - diferente da chave de entidade, o provedor de reflexão trata as propriedades acessíveis, não são do indexador de uma classe que é um tipo de entidade da seguinte maneira:

  - Se a propriedade retorna um tipo primitivo, em seguida, a propriedade deve para ser uma propriedade de um tipo de entidade.

  - Se a propriedade retorna um tipo que também é um tipo de entidade, em seguida, a propriedade deve para ser uma propriedade de navegação que representa o lado "um" de uma relação muitos-para-um ou um.

  - Se a propriedade retorna um <xref:System.Collections.Generic.IEnumerable%601> de um tipo de entidade, em seguida, a propriedade será considerada como uma propriedade de navegação que representa o final "muitos" de uma relação um-para-muitos ou muitos-para-muitos.

  - Se o tipo de retorno da propriedade for um tipo de valor, a propriedade representa um tipo complexo.

> [!NOTE]
> Ao contrário de um modelo de dados com base no modelo de entidade relacional, modelos com base no provedor de reflexão não entendem dados relacionais. Você deve usar o Entity Framework para expor dados relacionais por meio de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].

## <a name="data-type-mapping"></a>Mapeamento de tipo de dados

Quando um modelo de dados é inferido de classes do .NET Framework, os tipos primitivos no modelo de dados são mapeados para tipos de dados do .NET Framework da seguinte maneira:

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
> Tipos de valor anuláveis do .NET framework são mapeados para os mesmos tipos de modelo de dados que os tipos de valor correspondente que não não possível atribuir um valor nulo.

## <a name="enabling-updates-in-the-data-model"></a>Habilitando atualizações no modelo de dados

Para permitir atualizações aos dados que são expostas por meio desse tipo de modelo de dados, o provedor de reflexão define um <xref:System.Data.Services.IUpdatable> interface. Essa interface instrui o serviço de dados sobre como manter atualizações para os tipos expostos. Para habilitar as atualizações para recursos que são definidos pelo modelo de dados, a classe de contêiner de entidade deve implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter um exemplo de uma implementação do <xref:System.Data.Services.IUpdatable> interface, consulte [como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).

O <xref:System.Data.Services.IUpdatable> interface requer que os seguintes membros seja implementado para que as atualizações podem ser propagadas para a fonte de dados usando o provedor de reflexão:

|Membro|Descrição|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Fornece a funcionalidade para adicionar um objeto a uma coleção de objetos relacionados que são acessados a partir de uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Fornece a funcionalidade que Cancela alterações pendentes para os dados.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Fornece a funcionalidade para criar um novo recurso no contêiner especificado.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Fornece a funcionalidade para excluir um recurso.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Fornece a funcionalidade para recuperar um recurso que é identificado por um nome de consulta e o tipo específico.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|Fornece a funcionalidade para retornar o valor de uma propriedade de um recurso.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Fornece a funcionalidade para remover um objeto a uma coleção de objetos relacionados acessado a partir de uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Fornece a funcionalidade para atualizar um recurso especificado.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Fornece a funcionalidade para retornar o recurso que é representado por uma instância de objeto específico.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Fornece a funcionalidade para salvar todas as alterações pendentes.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Fornece a funcionalidade para definir uma referência de objeto relacionado por meio de uma propriedade de navegação.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|Fornece a funcionalidade para definir o valor da propriedade de um recurso.|

## <a name="handling-concurrency"></a>Tratamento de simultaneidade

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dá suporte a um modelo de simultaneidade otimista, permitindo que você definir um token de simultaneidade para uma entidade. Este token de simultaneidade, que inclui uma ou mais propriedades da entidade, é usado pelo serviço de dados para determinar se uma alteração ocorreu nos dados que estão sendo solicitados, atualizados ou excluídos. Quando os valores do token obtidos da eTag na solicitação diferem dos valores atuais da entidade, uma exceção é gerada pelo serviço de dados. O <xref:System.Data.Services.ETagAttribute> é aplicado a um tipo de entidade para definir um token de simultaneidade no provedor de reflexão. O token de simultaneidade não pode incluir uma propriedade de chave ou uma propriedade de navegação. Para obter mais informações, consulte [atualização do serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Usando LINQ to SQL com o provedor de reflexão

Como o Entity Framework tem suporte nativo por padrão, é o provedor de dados recomendado para usar dados relacionais com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. No entanto, você pode usar o provedor de reflexão para usar LINQ to SQL classes com um serviço de dados. O <xref:System.Data.Linq.Table%601> que são retornados pelos métodos em conjuntos de resultados de <xref:System.Data.Linq.DataContext> gerado pelo LINQ para implementar SQL Object Relational Designer (O/R Designer) a <xref:System.Linq.IQueryable%601> interface. Isso permite que o provedor de reflexão acessar esses métodos e retornar dados de entidade do SQL Server usando o gerado classes LINQ to SQL. No entanto, como LINQ to SQL não implementa o <xref:System.Data.Services.IUpdatable> interface, você precisa adicionar uma classe parcial que estende existente <xref:System.Data.Linq.DataContext> classe parcial para adicionar o <xref:System.Data.Services.IUpdatable> implementação. Para obter mais informações, confira [Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
