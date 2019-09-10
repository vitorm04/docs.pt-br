---
title: Personalização do feed (WCF Data Services)
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
ms.openlocfilehash: 17d54210d7abc16fe91fa94f39a8f85eac866088
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854190"
---
# <a name="feed-customization-wcf-data-services"></a>Personalização do feed (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]usa o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor dados como um feed. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]dá suporte a formatos Atom e JavaScript Object Notation (JSON) para feeds de dados. Quando você usa um Feed Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] o fornece um método padrão para serializar dados, como entidades e relações, em um formato XML que pode ser incluído no corpo da mensagem http. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]define um mapeamento de propriedade de entidade padrão entre os dados contidos em entidades e elementos Atom. Para obter mais informações, [consulte OData: Formato](https://go.microsoft.com/fwlink/?LinkID=185794)Atom.  
  
 Você pode ter um cenário de aplicativo que exige que os dados de propriedade retornados pelo serviço de dados sejam serializados de uma maneira personalizada em vez de no formato de feed padrão. Com [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]o, você pode personalizar a serialização em um feed de dados para que as propriedades de uma entidade possam ser mapeadas para elementos não utilizados e atributos de uma entrada ou para elementos personalizados de uma entrada no feed.  
  
> [!NOTE]
> A personalização do feed só tem suporte para feeds ATOM. Os feeds personalizados não são retornados quando o formato JSON é solicitado para o feed retornado.  
  
 Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]o, você pode definir um mapeamento de propriedade de entidade alternativo para um conteúdo Atom aplicando manualmente os atributos aos tipos de entidade no modelo de dados. O provedor de fonte de dados do serviço de dados determina como você deve aplicar esses atributos.  
  
> [!IMPORTANT]
> Ao definir feeds personalizados, você deve garantir que todas as propriedades de entidade que têm mapeamentos personalizados definidos sejam incluídas na projeção. Quando uma propriedade de entidade mapeada não é incluída na projeção, pode ocorrer perda de dados. Para obter mais informações, consulte [projeções de consulta](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Personalizando feeds com o provedor de Entity Framework  
 O modelo de dados usado com o provedor de Entity Framework é representado como XML no arquivo. edmx. Nesse caso, os atributos que definem feeds personalizados são adicionados aos `EntityType` elementos `Property` e que representam tipos de entidade e propriedades no modelo de dados. Esses atributos de personalização do feed não são [definidos no \[MC\]-CSDL: Formato](https://go.microsoft.com/fwlink/?LinkId=159072)de arquivo de definição de esquema conceitual, que é o formato que o provedor de Entity Framework usa para definir o modelo de dados. Portanto, você deve declarar atributos de personalização de feed em um namespace de esquema específico, que `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`é definido como. O fragmento XML a seguir mostra `Property` os atributos `Products` de personalização do feed aplicados aos elementos do tipo de `ProductName`entidade `ReorderLevel`que definem as propriedades, e `UnitsInStock` .  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Esses atributos produzem o seguinte feed de dados personalizado para `Products` o conjunto de entidades. No feed de dados personalizado, o `ProductName` valor da propriedade é exibido em ambos `author` no elemento e como o `ProductName` elemento de propriedade, e `UnitsInStock` a propriedade é exibida em um elemento personalizado que tem seu próprio namespace exclusivo e com a `ReorderLevel` Propriedade como um atributo:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Para obter mais informações, confira [Como: Personalize feeds com o provedor](how-to-customize-feeds-with-ef-provider-wcf-data-services.md)de Entity Framework.  
  
> [!NOTE]
> Como as extensões para o modelo de dados não são suportadas pelo Entity Designer, você deve modificar manualmente o arquivo XML que contém o modelo de dados. Para obter mais informações sobre o arquivo. edmx gerado pelas ferramentas de Modelo de Dados de Entidade, consulte [visão geral do arquivo. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Atributos de feed personalizados  
 A tabela a seguir mostra os atributos XML que personalizam feeds que você pode adicionar ao CSDL (linguagem de definição de esquema conceitual) que define o modelo de dados. Esses atributos são equivalentes às propriedades do <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> usadas com o provedor de reflexão.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|`FC_ContentKind`|Indica o tipo do conteúdo. As palavras-chave a seguir definem tipos de conteúdo de distribuição.<br /><br /> `text:`O valor da propriedade é exibido no feed como texto.<br /><br /> `html:`O valor da propriedade é exibido no feed como HTML.<br /><br /> `xhtml:`O valor da propriedade é exibido no feed como HTML formatado em XML.<br /><br /> Essas palavras-chave são equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationTextContentKind> enumeração usada com o provedor de reflexão.<br /><br /> Não há suporte para esse atributo quando `FC_NsPrefix` os `FC_NsUri` atributos e são usados.<br /><br /> Ao especificar um valor de `xhtml` para o `FC_ContentKind` atributo, você deve garantir que o valor da propriedade contenha XML formatado corretamente. O serviço de dados retorna o valor sem executar nenhuma transformação. Você também deve garantir que todos os prefixos de elemento XML no XML retornado tenham um URI de namespace e um prefixo definidos no feed mapeado.|  
|`FC_KeepInContent`|Indica que o valor da propriedade referenciada deve ser incluído na seção de conteúdo do feed e no local mapeado. Os valores válidos são `true` e `false`. Para tornar o feed resultante compatível com versões anteriores do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], especifique um valor de `true` para certificar-se de que o valor está incluído na seção de conteúdo do feed.|  
|`FC_NsPrefix`|O prefixo do namespace do elemento XML em um mapeamento que não é de distribuição. Esse atributo deve ser usado com o `FC_NsUri` atributo e não pode ser usado com `FC_ContentKind` o atributo.|  
|`FC_NsUri`|O URI do namespace do elemento XML em um mapeamento que não é de distribuição. Esse atributo deve ser usado com o `FC_NsPrefix` atributo e não pode ser usado com `FC_ContentKind` o atributo.|  
|`FC_SourcePath`|O caminho da propriedade da entidade à qual esta regra de mapeamento de feed se aplica. Só há suporte para esse atributo quando ele é usado em `EntityType` um elemento.<br /><br /> A <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade não pode referenciar diretamente um tipo complexo. Para tipos complexos, você deve usar uma expressão de caminho na qual os nomes de propriedade são separados por`/`um caractere de barra invertida (). Por exemplo, os valores a seguir são permitidos para um tipo `Person` de entidade com uma `Age` propriedade de número inteiro e uma propriedade complexa<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> A <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> propriedade não pode ser definida como um valor que contenha um espaço ou qualquer outro caractere que não seja válido em um nome de propriedade.|  
|`FC_TargetPath`|O nome do elemento de destino do feed resultante para mapear a propriedade. Esse elemento pode ser um elemento definido pela especificação Atom ou um elemento personalizado.<br /><br /> As palavras-chave a seguir são valores de caminho de destino de agregação predefinidos que [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] apontam para um local específico em um feed.<br /><br /> `SyndicationAuthorEmail:`O `atom:email` elemento filho `atom:author` do elemento.<br /><br /> `SyndicationAuthorName:`O `atom:name` elemento filho `atom:author` do elemento.<br /><br /> `SyndicationAuthorUri:`O `atom:uri` elemento filho `atom:author` do elemento.<br /><br /> `SyndicationContributorEmail:`O `atom:email` elemento filho `atom:contributor` do elemento.<br /><br /> `SyndicationContributorName:`O `atom:name` elemento filho `atom:contributor` do elemento.<br /><br /> `SyndicationContributorUri:`O `atom:uri` elemento filho `atom:contributor` do elemento.<br /><br /> `SyndicationCustomProperty:`Um elemento Property personalizado. Ao mapear para um elemento personalizado, o destino deve ser uma expressão de caminho na qual os elementos aninhados são separados por`/`uma barra invertida () e os atributos`@`são especificados por um e comercial (). No exemplo a seguir, a cadeia `UnitsInStock/@ReorderLevel` de caracteres mapeia um valor de propriedade para `ReorderLevel` um atributo chamado em um `UnitsInStock` elemento filho denominado do elemento de entrada raiz.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Quando o destino for um nome de elemento personalizado, `FC_NsPrefix` os `FC_NsUri` atributos e também deverão ser especificados.<br /><br /> `SyndicationPublished:`O `atom:published` elemento.<br /><br /> `SyndicationRights:`O `atom:rights` elemento.<br /><br /> `SyndicationSummary:`O `atom:summary` elemento.<br /><br /> `SyndicationTitle:`O `atom:title` elemento.<br /><br /> `SyndicationUpdated:`O `atom:updated` elemento.<br /><br /> Essas palavras-chave são equivalentes aos valores da <xref:System.Data.Services.Common.SyndicationItemProperty> enumeração usada com o provedor de reflexão.|  
  
> [!NOTE]
> Os nomes e valores de atributo diferenciam maiúsculas de minúsculas. Os atributos podem ser aplicados ao `EntityType` elemento ou a um ou mais `Property` elementos, mas não a ambos.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Personalizando feeds com o provedor de reflexão  
 Para personalizar feeds para um modelo de dados que foi implementado usando o provedor de reflexão, adicione uma ou mais instâncias <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> do atributo às classes que representam tipos de entidade no modelo de dados. As propriedades da <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> classe correspondem aos atributos de personalização do feed que são descritos na seção anterior. Veja a seguir um exemplo da declaração do `Order` tipo, com o mapeamento de feed personalizado definido para ambas as propriedades.  
  
> [!NOTE]
> O modelo de dados para este exemplo é definido no tópico [como: Crie um serviço de dados usando o provedor](create-a-data-service-using-rp-wcf-data-services.md)de reflexão.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Esses atributos produzem o seguinte feed de dados personalizado para `Orders` o conjunto de entidades. Nesse feed personalizado, o valor `OrderId` da propriedade é exibido somente `title` no elemento do `author` `entry` e o `Customer` valor da propriedade é exibido no elemento e como o `Customer` elemento de propriedade:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Para obter mais informações, confira [Como: Personalize feeds com o provedor](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)de reflexão.  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Personalizando feeds com um provedor de serviços de dados personalizado  
 A personalização do feed para um modelo de dados definido usando um provedor de serviço de dados personalizado é definida para um tipo <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> de recurso <xref:System.Data.Services.Providers.ResourceType> chamando o no que representa um tipo de entidade no modelo de dados. Para obter mais informações, consulte [provedores de serviço de dados personalizados](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Consumindo feeds personalizados  
 Quando o aplicativo consome diretamente um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, ele deve ser capaz de processar quaisquer elementos e atributos personalizados no feed retornado. Quando você implementou feeds personalizados em seu modelo de dados, independentemente do provedor de serviços de `$metadata` dados, o ponto de extremidade retorna informações de feed personalizadas como atributos de feed personalizados no CSDL retornado pelo serviço de dados. Quando você usa a caixa de diálogo **Adicionar referência de serviço** ou a ferramenta [datasvcutil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) para gerar classes de serviço de dados do cliente, os atributos de feed personalizados são usados para garantir que as solicitações e respostas para o serviço de dados sejam manipuladas corretamente.  
  
## <a name="feed-customization-considerations"></a>Considerações de personalização do feed  
 Você deve considerar o seguinte ao definir mapeamentos de feed personalizados.  
  
- O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente trata os elementos mapeados em um feed como vazios quando contêm apenas espaços em branco. Por isso, os elementos mapeados que contêm apenas espaços em branco não são materializados no cliente com o mesmo espaço em branco. Para preservar esse espaço em branco no cliente, você deve definir o valor de `KeepInContext` como `true` no atributo de mapeamento de feed.  
  
## <a name="versioning-requirements"></a>Requisitos de controle de versão  
 A personalização do feed tem [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] os seguintes requisitos de controle de versão de protocolo:  
  
- A personalização do feed requer que o cliente e o serviço de dados ofereçam [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] suporte à versão 2,0 do protocolo e versões posteriores.  
  
 Para obter mais informações, consulte [controle de versão do serviço de dados](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Provedor de reflexão](reflection-provider-wcf-data-services.md)
- [Entity Framework Provider](entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)
