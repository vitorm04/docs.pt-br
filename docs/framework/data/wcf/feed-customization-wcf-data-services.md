---
title: "Personalização de feed (WCF Data Services)"
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
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e31f14d59bb2ac7caa233ff60c60eb944ee5bbbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="feed-customization-wcf-data-services"></a>Personalização de feed (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]usa o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor dados como um feed. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]oferece suporte a formatos Atom e JSON JavaScript Object Notation () para feeds de dados. Quando você usar um feed Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fornece um método padrão para serializar os dados, como entidades e relações em um formato XML que pode ser incluído no corpo da mensagem HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um mapeamento de propriedade de entidade padrão entre os dados contidos em entidades e elementos do Atom. Para obter mais informações, consulte [OData: formato Atom](http://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Você pode ter um cenário de aplicativo que exige que os dados de propriedade retornados pelo serviço de dados ser serializado de maneira personalizada em vez de no formato de feed padrão. Com [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], você pode personalizar a serialização de um feed de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados e atributos de uma entrada ou para elementos personalizados de uma entrada no feed.  
  
> [!NOTE]
>  Feed de personalização só há suporte para feeds Atom. Feeds personalizados não são retornados quando o formato JSON é solicitado para o feed retornado.  
  
 Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode definir um mapeamento de propriedade de entidade alternativo para uma carga de Atom pela aplicação manual de atributos para os tipos de entidade no modelo de dados. O provedor de fonte de dados do serviço de dados determina como você deve aplicar esses atributos.  
  
> [!IMPORTANT]
>  Quando você define feeds personalizados, você deve assegurar que todas as propriedades de entidade que têm mapeamentos personalizados são incluídas na projeção. Quando uma propriedade de entidade mapeada não está incluída na projeção, pode ocorrer perda de dados. Para obter mais informações, consulte [projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Personalizando Feeds com o provedor do Entity Framework  
 O modelo de dados usado com o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provedor é representado como XML no arquivo. edmx. Nesse caso, os atributos que definem os feeds personalizados são adicionados para o `EntityType` e `Property` elementos que representam os tipos de entidade e propriedades no modelo de dados. Esses atributos de personalização do feed não estão definidos na [ \[MC CSDL\]: formato de arquivo de definição de esquema conceitual](http://go.microsoft.com/fwlink/?LinkId=159072), que é o formato que o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provedor usa para definir o modelo de dados. Portanto, você deve declarar atributos de personalização de feed em um namespace de esquema específico, que é definido como `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. O fragmento XML a seguir mostra os atributos de personalização de feed aplicados a `Property` elementos do `Products` tipo de entidade que definem o `ProductName`, `ReorderLevel`, e `UnitsInStock` propriedades.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Esses atributos produzem os seguintes dados personalizados de feed para o `Products` conjunto de entidades. No feed, de dados personalizados a `ProductName` o valor da propriedade é exibido no `author` elemento e como o `ProductName` elemento de propriedade e o `UnitsInStock` propriedade é exibida em um elemento personalizado que tem seu próprio espaço para nome exclusivo e com o `ReorderLevel` a propriedade como um atributo:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Para obter mais informações, consulte [como: Personalizar Feeds com o provedor do Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Porque não há suporte para as extensões para o modelo de dados pelo Designer de entidade, você deve modificar manualmente o arquivo XML que contém o modelo de dados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o arquivo. edmx que é gerado pelo [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ferramentas, consulte [. edmx visão geral do arquivo](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Atributos de Feed personalizados  
 A tabela a seguir mostra os atributos XML que personalizam feeds que podem ser adicionados para a linguagem de definição de esquema conceitual (CSDL) que define o modelo de dados. Esses atributos são equivalentes às propriedades do <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> usado com o provedor de reflexão.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|`FC_ContentKind`|Indica o tipo do conteúdo. As seguintes palavras-chave definem os tipos de conteúdo de distribuição.<br /><br /> `text:`O valor da propriedade é exibido no feed como texto.<br /><br /> `html:`O valor da propriedade é exibido no feed como HTML.<br /><br /> `xhtml:`O valor da propriedade é exibido no feed como HTML formatado em XML.<br /><br /> Essas palavras-chave é equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationTextContentKind> enumeração usada com o provedor de reflexão.<br /><br /> Esse atributo não é suportado quando o `FC_NsPrefix` e `FC_NsUri` os atributos são usados.<br /><br /> Quando você especifica um valor de `xhtml` para o `FC_ContentKind` atributo, você deve garantir que o valor da propriedade contém XML formatado corretamente. O serviço de dados retorna o valor sem executar todas as transformações. Você também deve garantir que os prefixos de elemento XML no XML retornado tem um URI de namespace e um prefixo definido no feed mapeado.|  
|`FC_KeepInContent`|Indica que o valor da propriedade referenciada deve ser incluído na seção de conteúdo do feed e no local mapeado. Os valores válidos são `true` e `false`. Para tornar o feed resultante compatibilidade com versões anteriores do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], especifique um valor de `true` para certificar-se de que o valor é incluído na seção de conteúdo do feed.|  
|`FC_NsPrefix`|O prefixo de namespace do elemento XML em um mapeamento de não agregação. Esse atributo deve ser usado com o `FC_NsUri` de atributos e não pode ser usado com o `FC_ContentKind` atributo.|  
|`FC_NsUri`|O URI do namespace do elemento XML em um mapeamento de não agregação. Esse atributo deve ser usado com o `FC_NsPrefix` de atributos e não pode ser usado com o `FC_ContentKind` atributo.|  
|`FC_SourcePath`|O caminho da propriedade da entidade à qual o mapeamento de feed regra se aplica. Esse atributo é suportado apenas quando ele é usado em um `EntityType` elemento.<br /><br /> O <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade diretamente não pode referenciar um tipo complexo. Para tipos complexos, você deve usar uma expressão de caminho em que os nomes de propriedade são separados por uma barra invertida (`/`) caracteres. Por exemplo, os seguintes valores são permitidos para um tipo de entidade `Person` com uma propriedade de inteiro `Age` e uma propriedade complexa<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> O <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade não pode ser definida como um valor que contém um espaço ou qualquer outro caractere que não é válido em um nome de propriedade.|  
|`FC_TargetPath`|O nome do elemento do feed resultante para mapear a propriedade de destino. Esse elemento pode ser um elemento definido pela especificação Atom ou um elemento personalizado.<br /><br /> As seguintes palavras-chave são valores de caminho de destino predefinido de agregação que apontam para o local específico em um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.<br /><br /> `SyndicationAuthorEmail:`O `atom:email` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationAuthorName:`O `atom:name` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationAuthorUri:`O `atom:uri` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationContributorEmail:`O `atom:email` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationContributorName:`O `atom:name` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationContributorUri:`O `atom:uri` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationCustomProperty:`Um elemento de propriedade personalizada. Ao mapear para um elemento personalizado, o destino deve ser uma expressão de caminho no qual os elementos aninhados são separados por uma barra invertida (`/`) e os atributos são especificados por um e comercial (`@`). No exemplo a seguir, a cadeia de caracteres `UnitsInStock/@ReorderLevel` mapeia um valor de propriedade para um atributo chamado `ReorderLevel` em um elemento filho denominado `UnitsInStock` do elemento de entrada de raiz.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Quando o destino é um nome de elemento personalizado, o `FC_NsPrefix` e `FC_NsUri` atributos também devem ser especificados.<br /><br /> `SyndicationPublished:`O `atom:published` elemento.<br /><br /> `SyndicationRights:`O `atom:rights` elemento.<br /><br /> `SyndicationSummary:`O `atom:summary` elemento.<br /><br /> `SyndicationTitle:`O `atom:title` elemento.<br /><br /> `SyndicationUpdated:`O `atom:updated` elemento.<br /><br /> Essas palavras-chave é equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationItemProperty> enumeração usada com o provedor de reflexão.|  
  
> [!NOTE]
>  Valores e nomes de atributo diferenciam maiusculas de minúsculas. Os atributos podem ser aplicadas ao `EntityType` elemento ou a um ou mais `Property` elementos, mas não para ambos.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Personalizando Feeds com o provedor de reflexão  
 Para personalizar os feeds para um modelo de dados que foi implementado usando o provedor de reflexão, adicione uma ou mais instâncias do <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> de atributos para as classes que representam tipos de entidade no modelo de dados. As propriedades da <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> classe correspondem aos atributos de feed de personalização que são descritos na seção anterior. A seguir está um exemplo da declaração de `Order` tipo, com um mapeamento definido para ambas as propriedades de feed personalizado.  
  
> [!NOTE]
>  O modelo de dados para este exemplo é definido no tópico [como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Esses atributos produzem os seguintes dados personalizados de feed para o `Orders` conjunto de entidades. Neste personalizado feed, o `OrderId` valor da propriedade exibe somente no `title` elemento do `entry` e o `Customer` o valor da propriedade exibe no `author` elemento e como o `Customer` elemento de propriedade:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Para obter mais informações, consulte [como: Personalizar Feeds com o provedor de reflexão](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Personalizando Feeds com um provedor de serviços de dados personalizados  
 Feed de personalização para um modelo de dados definido por meio de um provedor de serviços de dados personalizado é definido para um tipo de recurso chamando o <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> no <xref:System.Data.Services.Providers.ResourceType> que representa um tipo de entidade no modelo de dados. Para obter mais informações, consulte [provedores de serviço de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Consumindo personalizada Feeds  
 Quando seu aplicativo diretamente consome um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, deve ser capaz de processar qualquer elementos personalizados e atributos no feed retornado. Quando você tiver implementado feeds personalizados em seu modelo de dados, independentemente do provedor de serviços de dados, o `$metadata` retorna de ponto de extremidade personalizado feed informações personalizados como atributos de feed no CSDL retornado pelo serviço de dados. Quando você usa o **adicionar referência de serviço** caixa de diálogo ou o [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ferramenta para gerar classes de serviço de dados do cliente, o feed personalizado atributos são usados para garantir que as solicitações e respostas o serviço de dados estão sendo tratadas corretamente.  
  
## <a name="feed-customization-considerations"></a>Considerações sobre a personalização de feed  
 Você deve considerar o seguinte ao definir mapeamentos de feed personalizados.  
  
-   O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente trata elementos mapeados em um feed como vazio quando eles contêm apenas espaços em branco. Por isso, os elementos mapeados que contêm apenas espaços em branco não são materializados no cliente com o mesmo espaço em branco. Para preservar esse espaço em branco no cliente, você deve definir o valor de `KeepInContext` para `true` no atributo de mapeamento de feed.  
  
## <a name="versioning-requirements"></a>Requisitos de controle de versão  
 Personalização de feed tem as seguintes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] requisitos de controle de versão de protocolo:  
  
-   Personalização de feed requer que o cliente e os dados de serviço suporte a versão 2.0 do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo e versões posteriores.  
  
 Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)
