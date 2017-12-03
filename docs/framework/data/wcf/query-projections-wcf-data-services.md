---
title: "Projeções de consulta (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d14c67daa387f06a3c7d6e43219991950bceb73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="query-projections-wcf-data-services"></a>Projeções de consulta (WCF Data Services)
Projeção fornece um mecanismo no [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para reduzir a quantidade de dados no feed retornado por uma consulta especificando que somente algumas propriedades de uma entidade são retornadas na resposta. Para obter mais informações, consulte [OData: Selecionar opção de consulta do sistema ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Este tópico descreve como definir uma projeção de consulta, o que os requisitos são para a entidade e tipos de entidade não fazer atualizações aos resultados projetados, Criando tipos projetados e lista algumas considerações de projeção.  
  
## <a name="defining-a-query-projection"></a>Define uma projeção de consulta  
 Você pode adicionar uma cláusula de projeção para uma consulta usando o `$select` opção em um URI ou por meio de consulta a [selecione](~/docs/csharp/language-reference/keywords/select-clause.md) cláusula ([selecione](~/docs/visual-basic/language-reference/queries/select-clause.md) no Visual Basic) em uma consulta LINQ. Retornado entidade dados podem ser projetados para tipos de entidade ou tipos de entidade não no cliente. Os exemplos neste tópico demonstram como usar o `select` cláusula em uma consulta LINQ.  
  
> [!IMPORTANT]
>  Pode ocorrer perda de dados no serviço de dados quando você salvar as atualizações que foram feitas para tipos projetados. Para obter mais informações, consulte [considerações de projeção](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Requisitos para a entidade e tipos de entidade não  
 Tipos de entidade devem ter uma ou mais propriedades de identidade que compõem a chave de entidade. Tipos de entidade são definidos em clientes em uma das seguintes maneiras:  
  
-   Aplicando o <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> para o tipo.  
  
-   Quando o tipo tem uma propriedade denominada `ID`.  
  
-   Quando o tipo tem uma propriedade denominada *tipo*`ID`, onde *tipo* é o nome do tipo.  
  
 Por padrão, quando você projetar os resultados da consulta em um tipo definido no cliente, as propriedades solicitadas na projeção devem existir no tipo de cliente. No entanto, quando você especifica um valor de `true` para o <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriedade o <xref:System.Data.Services.Client.DataServiceContext>, propriedades especificadas na projeção não deve ocorrer no tipo de cliente.  
  
### <a name="making-updates-to-projected-results"></a>Fazer atualizações em resultados projetados  
 Quando você projetar resultados da consulta em tipos de entidade no cliente, o <xref:System.Data.Services.Client.DataServiceContext> pode rastrear esses objetos com as atualizações para ser enviada de volta para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado. No entanto, as atualizações feitas nos dados projetados em tipos de entidade não no cliente não serão enviadas para o serviço de dados. Isso ocorre porque sem uma chave para identificar a instância de entidade, o serviço de dados não é possível atualizar a entidade correta na fonte de dados. Tipos de entidade não não estão conectados ao <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Quando uma ou mais propriedades de um tipo de entidade definido no serviço de dados não ocorrem no tipo de cliente no qual a entidade estiver projetada, inserções de novas entidades não conterá essas propriedades ausentes. Nesse caso, as atualizações feitas para entidades existentes serão **também** não inclua essas propriedades ausentes. Quando um valor existe para essa propriedade, a atualização ele será redefinido para o valor padrão para a propriedade, conforme definido na fonte de dados.  
  
### <a name="creating-projected-types"></a>Criando tipos projetados  
 O exemplo a seguir usa uma consulta LINQ anônima que projeta as propriedades relacionadas a endereço do `Customers` tipo em um novo `CustomerAddress` tipo, que é definido no cliente e é atribuído como um tipo de entidade:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 Neste exemplo, o padrão de inicializador de objeto é usado para criar uma nova instância do `CustmerAddress` tipo em vez de chamar um construtor. Construtores não são suportados quando a projeção em tipos de entidade, mas eles podem ser usados ao projetar em tipos de entidade não e anônimos. Porque `CustomerAddress` é um tipo de entidade, as alterações podem ser feitas e enviadas de volta para o serviço de dados.  
  
 Além disso, os dados do `Customer` projetado em uma instância do tipo de `CustomerAddress` tipo de entidade em vez de um tipo anônimo. Há suporte para a projeção em tipos anônimos, mas os dados são somente leitura, como tipos anônimos são tratados como tipos de entidade não.  
  
 O <xref:System.Data.Services.Client.MergeOption> configurações do <xref:System.Data.Services.Client.DataServiceContext> são usados para resolução de identidade durante a projeção de consulta. Isso significa que, se uma instância do `Customer` tipo já existe no <xref:System.Data.Services.Client.DataServiceContext>, uma instância de `CustomerAddress` com a mesma identidade seguirão a resolução de identidade regras definidas pelo<xref:System.Data.Services.Client.MergeOption>  
  
 A tabela a seguir descreve os comportamentos na projeção de resultados em tipos de entidade e não da entidade:  
  
|Ação|Tipo de entidade|Tipo de entidade não|  
|------------|-----------------|----------------------|  
|Criando uma nova instância projetada usando inicializadores, como no exemplo a seguir:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|Com suporte|Com suporte|  
|Criando uma nova instância projetada usando construtores, como no exemplo a seguir:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|Um <xref:System.NotSupportedException> é gerado.|Com suporte|  
|Uso da projeção para transformar um valor de propriedade, como no exemplo a seguir:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> Não há suporte para essa transformação para tipos de entidade porque isso pode levar a confusão e potencialmente sobrescrever os dados na fonte de dados que pertence a outra entidade.|Um <xref:System.NotSupportedException> é gerado.|Com suporte|  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Considerações de projeção  
 As seguintes considerações adicionais se aplicam ao definir uma projeção de consulta.  
  
-   Quando você define os feeds personalizados para o formato Atom, você deve garantir que todas as propriedades de entidade que têm mapeamentos personalizados são incluídas na projeção. Quando uma propriedade de entidade mapeada não está incluída na projeção, pode ocorrer perda de dados. Para obter mais informações, consulte [personalização Feed](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Quando as inserções são feitas em um tipo projetado que não contém todas as propriedades da entidade no modelo de dados do serviço de dados, as propriedades não são incluídas na projeção no cliente são definidas para seus valores padrão.  
  
-   Quando as atualizações são feitas para um tipo projetado que não contém todas as propriedades da entidade no modelo de dados do serviço de dados, os valores existentes não são incluídos na projeção no cliente serão substituídos com valores padrão não inicializado.  
  
-   Quando uma projeção inclui uma propriedade complexa, todo o objeto complexo deve ser retornado.  
  
-   Quando uma projeção inclui uma propriedade de navegação, os objetos relacionados são carregados implicitamente sem a necessidade de chamar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método. O <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método não é suportado para uso em uma consulta projetado.  
  
-   Consultas de projeções de consulta no cliente são convertidas para usar o `$select` opção no URI de solicitação de consulta. Quando uma consulta com a projeção é executada em uma versão anterior do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] que não oferece suporte a `$select` opção de consulta, um erro será retornado. Isso também pode acontecer quando o <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> do <xref:System.Data.Services.DataServiceBehavior> para os dados de serviço é definido como um valor de <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Para obter mais informações, consulte [como: resultados de consulta do projeto](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
