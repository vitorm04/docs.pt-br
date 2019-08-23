---
title: Projeções de consulta (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 44e99db2d75fcd8e84f91f0afc8da54ff6c3f707
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931165"
---
# <a name="query-projections-wcf-data-services"></a>Projeções de consulta (WCF Data Services)

A projeção fornece um mecanismo [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] no para reduzir a quantidade de dados no feed retornada por uma consulta, especificando que apenas determinadas propriedades de uma entidade são retornadas na resposta. Para obter mais informações, [consulte OData: Selecione a opção de consulta do sistema](https://go.microsoft.com/fwlink/?LinkId=186076)($SELECT).

Este tópico descreve como definir uma projeção de consulta, quais são os requisitos para tipos de entidade e não de entidade, fazer atualizações em resultados projetados, criar tipos projetados e listar algumas considerações de projeção.

## <a name="defining-a-query-projection"></a>Definindo uma projeção de consulta

Você pode adicionar uma cláusula de projeção a uma consulta usando a `$select` opção de consulta em um URI ou usando a cláusula [Select](../../../csharp/language-reference/keywords/select-clause.md) ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) em uma consulta LINQ. Os dados de entidade retornados podem ser projetados em tipos de entidade ou tipos que não são de entidade no cliente. Os exemplos neste tópico demonstram como usar a `select` cláusula em uma consulta LINQ.

> [!IMPORTANT]
> A perda de dados pode ocorrer no serviço de dados quando você salva atualizações que foram feitas em tipos projetados. Para obter mais informações, consulte [considerações](#considerations)de projeção.

## <a name="requirements-for-entity-and-non-entity-types"></a>Requisitos para tipos de entidade e não de entidade

Os tipos de entidade devem ter uma ou mais propriedades de identidade que compõem a chave de entidade. Os tipos de entidade são definidos em clientes de uma das seguintes maneiras:

- Aplicando o <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> ao tipo.

- Quando o tipo tem uma propriedade chamada `ID`.

- Quando o tipo tem uma propriedade chamada *Type*`ID`, em que *Type* é o nome do tipo.

Por padrão, quando você projeta os resultados da consulta em um tipo definido no cliente, as propriedades solicitadas na projeção devem existir no tipo de cliente. No entanto, quando você especifica um `true` valor de <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> para a propriedade <xref:System.Data.Services.Client.DataServiceContext>do, as propriedades especificadas na projeção não precisam ocorrer no tipo de cliente.

### <a name="making-updates-to-projected-results"></a>Fazendo atualizações nos resultados projetados

Quando você projeta resultados de consulta em tipos de entidade no cliente, <xref:System.Data.Services.Client.DataServiceContext> o pode controlar esses objetos com atualizações a serem enviadas de volta ao serviço de dados <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> quando o método é chamado. No entanto, as atualizações feitas aos dados projetadas em tipos que não são de entidade no cliente não podem ser enviadas de volta ao serviço de dados. Isso ocorre porque, sem uma chave para identificar a instância de entidade, o serviço de dados não pode atualizar a entidade correta na fonte de dados. Os <xref:System.Data.Services.Client.DataServiceContext>tipos que não são de entidade não são anexados ao.

Quando uma ou mais propriedades de um tipo de entidade definida no serviço de dados não ocorrem no tipo de cliente no qual a entidade está projetada, as inserções de novas entidades não conterá essas propriedades ausentes. Nesse caso, as atualizações feitas em entidades existentes **também** não incluirão essas propriedades ausentes. Quando existe um valor para tal propriedade, a atualização o redefine para o valor padrão da propriedade, conforme definido na fonte de dados.

### <a name="creating-projected-types"></a>Criando tipos projetados

O exemplo a seguir usa uma consulta LINQ anônima que projeta as propriedades relacionadas ao endereço do `Customers` tipo em um novo `CustomerAddress` tipo, que é definido no cliente e é atribuído como um tipo de entidade:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

Neste exemplo, o padrão de inicializador de objeto é usado para criar uma nova instância `CustomerAddress` do tipo em vez de chamar um construtor. Não há suporte para construtores durante a projeção em tipos de entidade, mas eles podem ser usados durante a projeção em tipos anônimos e não de entidade. Como `CustomerAddress` é um tipo de entidade, as alterações podem ser feitas e enviadas de volta para o serviço de dados.

Além disso, os dados do `Customer` tipo são projetados em uma instância `CustomerAddress` do tipo de entidade, em vez de um tipo anônimo. Há suporte para projeção em tipos anônimos, mas os dados são somente leitura porque tipos anônimos são tratados como tipos que não são de entidade.

As <xref:System.Data.Services.Client.MergeOption> configurações<xref:System.Data.Services.Client.DataServiceContext> de são usadas para resolução de identidade durante a projeção de consulta. Isso significa que, se uma instância do `Customer` tipo já existir <xref:System.Data.Services.Client.DataServiceContext>no, uma instância do `CustomerAddress` com a mesma identidade seguirá as regras de resolução de identidade definidas pelo<xref:System.Data.Services.Client.MergeOption>

O seguinte descreve os comportamentos ao projetar resultados em tipos de entidade e não entidade:

**Criando uma nova instância projetada usando inicializadores**

- Exemplo:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Tipo de entidade: Com suporte

- Tipo de não entidade: Com suporte

**Criando uma nova instância projetada usando construtores**

- Exemplo:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Tipo de entidade: Um <xref:System.NotSupportedException> é gerado.

- Tipo de não entidade: Com suporte

**Usando projeção para transformar um valor de propriedade**

- Exemplo:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Tipo de entidade: Essa transformação não tem suporte para tipos de entidade porque pode levar à confusão e potencialmente substituir os dados na fonte de dados que pertence a outra entidade. Um <xref:System.NotSupportedException> é gerado.

- Tipo de não entidade: Com suporte

<a name="considerations"></a>

## <a name="projection-considerations"></a>Considerações sobre projeção

As considerações adicionais a seguir se aplicam ao definir uma projeção de consulta.

- Ao definir feeds personalizados para o formato Atom, você deve certificar-se de que todas as propriedades de entidade que têm mapeamentos personalizados definidos sejam incluídas na projeção. Quando uma propriedade de entidade mapeada não é incluída na projeção, pode ocorrer perda de dados. Para obter mais informações, consulte [personalização de feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).

- Quando são feitas inserções em um tipo projetado que não contém todas as propriedades da entidade no modelo de dados do serviço de dados, as propriedades não incluídas na projeção no cliente são definidas com seus valores padrão.

- Quando são feitas atualizações em um tipo projetado que não contém todas as propriedades da entidade no modelo de dados do serviço de dados, os valores existentes não incluídos na projeção no cliente serão substituídos por valores padrão não inicializados.

- Quando uma projeção inclui uma propriedade complexa, o objeto complexo inteiro deve ser retornado.

- Quando uma projeção inclui uma propriedade de navegação, os objetos relacionados são carregados implicitamente sem a necessidade <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> de chamar o método. Não <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> há suporte para o método para uso em uma consulta projetada.

- As consultas de projeções de consulta no cliente são convertidas para usar a `$select` opção de consulta no URI de solicitação. Quando uma consulta com projeção é executada em uma versão anterior [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do que não oferece suporte `$select` à opção de consulta, um erro é retornado. Isso também pode acontecer quando o <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.DataServiceBehavior> do para o serviço de dados é definido com um valor de <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Para obter mais informações, consulte [controle de versão do serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).

Para obter mais informações, confira [Como: Resultados da](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)consulta do projeto.

## <a name="see-also"></a>Consulte também

- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
