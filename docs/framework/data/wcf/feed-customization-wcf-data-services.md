---
title: Personalização de feed (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: c54ea70049544e5205613ab76eb810798513fab2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680212"
---
# <a name="feed-customization-wcf-data-services"></a>Personalização de feed (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor dados como um feed. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dá suporte a formatos Atom e notação JSON (JavaScript Object) para feeds de dados. Quando você usa um feed Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fornece um método padrão para serializar os dados, como entidades e relações, em um formato XML que pode ser incluído no corpo da mensagem HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] define um mapeamento de propriedade de entidade padrão entre os dados contidos em entidades e os elementos do Atom. Para obter mais informações, consulte [OData: Formato Atom](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Você pode ter um cenário de aplicativo que exige que os dados de propriedade retornados pelo serviço de dados seja serializado em uma maneira personalizada em vez de no padrão de formato de feed. Com [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], você pode personalizar a serialização em um feed de dados para que as propriedades de uma entidade podem ser mapeadas para elementos não utilizados e os atributos de uma entrada ou para elementos personalizados de uma entrada no feed.  
  
> [!NOTE]
>  Somente há suporte para personalização de feed para feeds Atom. Feeds personalizados não são retornados quando o formato JSON é solicitado para o feed retornado.  
  
 Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode definir um mapeamento de propriedade de entidade alternativo para uma carga de Atom manualmente aplicando atributos aos tipos de entidade no modelo de dados. O provedor de fonte de dados do serviço de dados determina como você deve aplicar esses atributos.  
  
> [!IMPORTANT]
>  Quando você define feeds personalizados, você deve assegurar que todas as propriedades de entidade que têm mapeamentos personalizados definidos são incluídas na projeção. Quando uma propriedade de entidade mapeada não está incluída na projeção, pode ocorrer perda de dados. Para obter mais informações, consulte [projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Como personalizar Feeds com o provedor do Entity Framework  
 O modelo de dados usado com o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provedor é representado como XML no arquivo. edmx. Nesse caso, os atributos que definem os feeds personalizados são adicionados para o `EntityType` e `Property` elementos que representam os tipos de entidade e propriedades no modelo de dados. Esses atributos de personalização de feed não estão definidos na [ \[MC CSDL\]: Formato de arquivo de definição de esquema conceitual](https://go.microsoft.com/fwlink/?LinkId=159072), que é o formato que o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provedor usa para definir o modelo de dados. Portanto, você deve declarar atributos de personalização de feed em um namespace de esquema específico, que é definida como `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. O fragmento XML a seguir mostra os atributos de personalização de feed aplicados a `Property` elementos do `Products` tipo de entidade que definem a `ProductName`, `ReorderLevel`, e `UnitsInStock` propriedades.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Esses atributos produzem os seguintes dados personalizados de feed para o `Products` conjunto de entidades. Personalizado feed de dados, o `ProductName` o valor da propriedade é exibido em ambos na `author` elemento e como o `ProductName` elemento de propriedade e o `UnitsInStock` propriedade é exibida em um elemento personalizado tem seu próprio namespace exclusivo e com o `ReorderLevel` a propriedade como um atributo:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Para obter mais informações, confira [Como: Personalizar Feeds com o provedor do Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Porque não há suporte para extensões para o modelo de dados pelo Designer de entidade, você deve modificar manualmente o arquivo XML que contém o modelo de dados. Para obter mais informações sobre o arquivo. edmx são geradas pelo [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ferramentas, consulte [visão geral do arquivo. edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Atributos de Feed personalizados  
 A tabela a seguir mostra os atributos XML que personalizar feeds que podem ser adicionados para o linguagem de definição de esquema conceitual (CSDL) que define o modelo de dados. Esses atributos são equivalentes às propriedades do <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> usado com o provedor de reflexão.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|`FC_ContentKind`|Indica o tipo de conteúdo. As seguintes palavras-chave definem os tipos de conteúdo de sindicalização.<br /><br /> `text:` O valor da propriedade é exibido no feed como texto.<br /><br /> `html:` O valor da propriedade é exibido no feed como HTML.<br /><br /> `xhtml:` O valor da propriedade é exibido no feed como HTML formatado em XML.<br /><br /> Essas palavras-chave é equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationTextContentKind> enumeração usada com o provedor de reflexão.<br /><br /> Esse atributo não é suportado quando o `FC_NsPrefix` e `FC_NsUri` atributos são usados.<br /><br /> Quando você especifica um valor de `xhtml` para o `FC_ContentKind` atributo, você deve garantir que o valor da propriedade contém o XML formatado corretamente. O serviço de dados retorna o valor sem executar todas as transformações. Você também deve garantir que quaisquer prefixos de elemento XML no XML retornado tem um URI de namespace e prefixo definido no feed mapeado.|  
|`FC_KeepInContent`|Indica que o valor da propriedade referenciados deve ser incluído na seção de conteúdo do feed e no local mapeado. Os valores válidos são `true` e `false`. Para tornar o feed resultante compatível com versões anteriores do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], especifique um valor de `true` para certificar-se de que o valor é incluído na seção de conteúdo do feed.|  
|`FC_NsPrefix`|O prefixo de namespace do elemento XML em um mapeamento de não agregação. Esse atributo deve ser usado com o `FC_NsUri` de atributos e não pode ser usado com o `FC_ContentKind` atributo.|  
|`FC_NsUri`|O URI do namespace do elemento XML em um mapeamento de não agregação. Esse atributo deve ser usado com o `FC_NsPrefix` de atributos e não pode ser usado com o `FC_ContentKind` atributo.|  
|`FC_SourcePath`|O caminho da propriedade da entidade ao qual este feed mapeamento regra se aplica. Esse atributo é suportado apenas quando ele é usado em um `EntityType` elemento.<br /><br /> O <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade diretamente não é possível fazer referência a um tipo complexo. Para tipos complexos, você deve usar uma expressão de caminho em que os nomes de propriedade são separados por uma barra invertida (`/`) caracteres. Por exemplo, os seguintes valores são permitidos para um tipo de entidade `Person` com uma propriedade de inteiro `Age` e uma propriedade complexa<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> O <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade não pode ser definida como um valor que contém um espaço ou qualquer outro caractere que não é válido em um nome de propriedade.|  
|`FC_TargetPath`|O nome do elemento de destino do feed resultante para mapear a propriedade. Esse elemento pode ser um elemento definido pela especificação do Atom ou um elemento personalizado.<br /><br /> As seguintes palavras-chave são valores de caminho de destino de sindicalização predefinidos que apontam para um local específico em um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.<br /><br /> `SyndicationAuthorEmail:` O `atom:email` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationAuthorName:` O `atom:name` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationAuthorUri:` O `atom:uri` elemento filho do `atom:author` elemento.<br /><br /> `SyndicationContributorEmail:` O `atom:email` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationContributorName:` O `atom:name` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationContributorUri:` O `atom:uri` elemento filho do `atom:contributor` elemento.<br /><br /> `SyndicationCustomProperty:` Um elemento de propriedade personalizada. Ao mapear para um elemento personalizado, o destino deve ser uma expressão de caminho no qual os elementos aninhados são separados por uma barra invertida (`/`) e atributos são especificados por um e comercial (`@`). No exemplo a seguir, a cadeia de caracteres `UnitsInStock/@ReorderLevel` mapeia um valor da propriedade para um atributo denominado `ReorderLevel` em um elemento filho chamado `UnitsInStock` do elemento de entrada de raiz.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Quando o destino é um nome de elemento personalizado, o `FC_NsPrefix` e `FC_NsUri` atributos também devem ser especificados.<br /><br /> `SyndicationPublished:` O `atom:published` elemento.<br /><br /> `SyndicationRights:` O `atom:rights` elemento.<br /><br /> `SyndicationSummary:` O `atom:summary` elemento.<br /><br /> `SyndicationTitle:` O `atom:title` elemento.<br /><br /> `SyndicationUpdated:` O `atom:updated` elemento.<br /><br /> Essas palavras-chave é equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationItemProperty> enumeração usada com o provedor de reflexão.|  
  
> [!NOTE]
>  Valores e nomes de atributo diferenciam maiusculas de minúsculas. Os atributos podem ser aplicadas para o `EntityType` elemento ou a um ou mais `Property` elementos, mas não a ambos.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Como personalizar Feeds com o provedor de reflexão  
 Para personalizar feeds para um modelo de dados que foi implementada usando o provedor de reflexão, adicione uma ou mais instâncias da <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> atributo às classes que representam os tipos de entidade no modelo de dados. As propriedades do <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> classe correspondem aos atributos de personalização de feed que são descritos na seção anterior. A seguir está um exemplo da declaração do `Order` tipo, com o mapeamento definido para ambas as propriedades do feed personalizado.  
  
> [!NOTE]
>  O modelo de dados para este exemplo é definido no tópico [como: Criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Esses atributos produzem os seguintes dados personalizados de feed para o `Orders` conjunto de entidades. Este feed, personalizado a `OrderId` valor da propriedade exibe apenas na `title` elemento da `entry` e o `Customer` valor da propriedade exibe no `author` elemento e como o `Customer` elemento de propriedade:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Para obter mais informações, confira [Como: Personalizar Feeds com o provedor de reflexão](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Como personalizar Feeds com um provedor de serviços de dados personalizados  
 Personalização de feed para um modelo de dados definido usando um provedor de serviços de dados personalizados é definido para um tipo de recurso chamando o <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> sobre o <xref:System.Data.Services.Providers.ResourceType> que representa um tipo de entidade no modelo de dados. Para obter mais informações, consulte [provedores de serviço de dados personalizado](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Consumindo personalizado Feeds  
 Quando seu aplicativo consome diretamente um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, deve ser capaz de processar qualquer personalizada de elementos e atributos no feed retornado. Quando você tiver implementado feeds personalizados em seu modelo de dados, independentemente do provedor de serviços de dados, o `$metadata` retorna de ponto de extremidade personalizado os atributos de feed personalizados como de informações de feed no CSDL retornado pelo serviço de dados. Quando você usa o **adicionar referência de serviço** caixa de diálogo ou o [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) ferramenta para gerar classes de serviço de dados do cliente, o feed personalizado atributos são usados para garantir que as solicitações e respostas para o serviço de dados são tratadas corretamente.  
  
## <a name="feed-customization-considerations"></a>Considerações sobre a personalização de feed  
 Você deve considerar o seguinte ao definir mapeamentos de feed personalizados.  
  
-   O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente trata elementos mapeados em um feed como vazio quando contém apenas espaços em branco. Por isso, os elementos mapeados que contêm somente espaço em branco não são materializados no cliente com o mesmo espaço em branco. Para preservar esse espaço em branco no cliente, você deve definir o valor de `KeepInContext` para `true` no atributo de mapeamento de feed.  
  
## <a name="versioning-requirements"></a>Requisitos de controle de versão  
 Personalização do feed tem as seguintes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] requisitos de controle de versão de protocolo:  
  
-   Personalização de feed requer que o cliente e dados de serviço suporte a versão 2.0 do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo e versões posteriores.  
  
 Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também
- [Provedor de reflexão](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)
