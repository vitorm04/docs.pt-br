---
title: Controle de versão de serviço de dados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 0d77f54b5ef20db81c3c20f486ac7314f73aece8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-service-versioning-wcf-data-services"></a>Controle de versão de serviço de dados (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] permite criar serviços de dados para que os clientes possam acessar dados como usando URIs de recursos com base em um modelo de dados. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] também suporta a definição de operações de serviço. Após a implantação inicial e potencialmente várias vezes durante a vida útil, esses serviços de dados podem precisar ser alterada para uma variedade de motivos, como alterar as necessidades de negócios, requisitos de tecnologia da informação, ou para solucionar outros problemas. Quando você faz alterações a um serviço de dados existente, você deve considerar se deseja definir uma nova versão de seus dados de serviço e a melhor maneira de minimizar o impacto nos aplicativos cliente existentes. Este tópico fornece orientações sobre quando e como criar uma nova versão de um serviço de dados. Ele também descreve como [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] manipula uma troca entre clientes e serviços de dados que oferecem suporte a versões diferentes do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo.  
  
## <a name="versioning-a-wcf-data-service"></a>Controle de versão de um WCF Data Services  
 Depois que um serviço de dados é implantado e os dados que está sendo consumidos, as alterações no serviço de dados tem o potencial de causar problemas de compatibilidade com aplicativos existentes do cliente. No entanto, como alterações geralmente são necessárias pelas necessidades de negócios em geral do serviço, você deve considerar quando e como criar uma nova versão do seu serviço de dados com o menor impacto no cliente de aplicativos.  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Alterações de modelo de dados que recomendam uma nova versão do serviço de dados  
 Ao considerar a possibilidade de publicar uma nova versão de um serviço de dados, é importante entender como os diferentes tipos de alterações podem afetar os aplicativos cliente. Alterações em um serviço de dados que podem exigir que você crie uma nova versão de um serviço de dados podem ser divididas em duas categorias a seguir:  
  
-   Altera para o contrato de serviço, que incluem atualizações para operações de serviço, as alterações a acessibilidade de conjuntos de entidades (feeds), alterações de versão e outras alterações de comportamentos de serviço.  
  
-   Altera para o contrato de dados, que incluem alterações para o modelo de dados, formatos de feed ou personalizações de feed.  
  
 A tabela a seguir detalha quais tipos de alterações, você deve considerar uma nova versão do serviço de dados de publicação:  
  
|Tipo de alteração|Requer uma nova versão|Nova versão não necessária|  
|--------------------|----------------------------|----------------------------|  
|Operações de serviço|-Adicionar o novo parâmetro<br />-Alterar tipo de retorno<br />-Remover a operação de serviço|-Exclua o parâmetro existente<br />-Adicionar nova operação de serviço|  
|Comportamentos de serviço|-Desabilite as solicitações de contagem<br />-Desabilite o suporte de projeção<br />-Aumente a versão do serviço de dados necessários|-Habilitar solicitações de contagem<br />-Habilitar o suporte de projeção<br />-Diminuir a versão do serviço de dados necessários|  
|Permissões do conjunto de entidades|-Restringir as permissões do conjunto de entidade<br />-Altere o código de resposta (novo valor do primeiro dígito) <sup>1</sup>|-Relaxar definir permissões de entidade<br />-Altere o código de resposta (mesmo primeiro valor de dígitos)|  
|Propriedades da entidade|-Remover relação ou propriedade existente<br />-Adicionar a propriedade não anulável<br />-Alteração de propriedade existente|-Adicionar a propriedade nullable<sup>2</sup>|  
|Conjuntos de entidade|-Remova o conjunto de entidades|-Adicionar o tipo derivado<br />-Altere o tipo base<br />-Adicionar o conjunto de entidades|  
|Personalização de feed|-Altere o mapeamento de propriedade de entidade||  
  
 <sup>1</sup> isso pode depender estritamente como um aplicativo cliente se baseia em receber um código de erro específico.  
  
 <sup>2</sup> você pode definir o <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriedade `true` para que o cliente a ignorar novas propriedades enviadas pelo serviço de dados que não estão definidas no cliente. No entanto, quando as inserções são feitas, as propriedades não incluídas pelo cliente na solicitação POST são definidas para seus valores padrão. Para atualizações, quaisquer dados existentes em uma propriedade desconhecida para o cliente podem ser substituídos com valores padrão. Nesse caso, você deve enviar a atualização como uma solicitação de mesclagem, que é o padrão. Para obter mais informações, consulte [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
### <a name="how-to-version-a-data-service"></a>A versão de um serviço de dados  
 Quando necessário, uma nova versão do serviço de dados é definida ao criar uma nova instância do serviço com um modelo de dados ou contrato de serviço atualizado. Esse novo serviço, em seguida, é exposto por meio de um ponto de extremidade URI novo, que diferencia da versão anterior. Por exemplo:  
  
-   Versão antiga: `http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   Nova versão: `http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 Ao atualizar um serviço de dados, os clientes precisará também seja atualizado com base nos metadados do serviço de dados novo e usar o novo URI de raiz. Quando possível, você deve manter a versão anterior do serviço de dados para dar suporte a clientes que ainda não foram atualizados para usar a nova versão. Versões mais antigas de um serviço de dados podem ser removidas quando eles não são mais necessários. Considere a possibilidade de manter o ponto de extremidade de serviço de dados URI em um arquivo de configuração externo.  
  
## <a name="odata-protocol-versions"></a>Versões de protocolo OData  
 Como novas versões de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] são lançadas, os aplicativos cliente podem não estar usando a mesma versão do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo com suporte pelo serviço de dados. Um aplicativo cliente mais antigo pode acessar um serviço de dados que oferece suporte a uma versão mais recente do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Um aplicativo cliente também pode estar usando uma versão mais recente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente, que oferece suporte a uma versão mais recente do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] que o serviço de dados que está sendo acessado.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] aproveita o suporte fornecido por [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] para lidar com esses cenários de controle de versão. Também há suporte para gerar e usar os metadados do modelo de dados para criar classes de serviço de dados de cliente quando o cliente usa uma versão diferente do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] que o serviço de dados usa. Para obter mais informações, consulte [OData: controle de versão de protocolo](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
### <a name="version-negotiation"></a>Negociação de versão  
 O serviço de dados pode ser configurado para definir a versão mais recente do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo que será usado pelo serviço, independentemente da versão solicitada pelo cliente. Você pode fazer isso especificando uma <xref:System.Data.Services.Common.DataServiceProtocolVersion> valor para o <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> propriedade o <xref:System.Data.Services.DataServiceBehavior> usado pelo serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Quando um aplicativo usa o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliotecas de cliente para acessar um serviço de dados, as bibliotecas automaticamente definir esses cabeçalhos para os valores corretos, dependendo da versão do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e os recursos que são usados em seu aplicativo. Por padrão, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa a versão mais antiga do protocolo que oferece suporte à operação solicitada.  
  
 A tabela a seguir fornece detalhes sobre as versões do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] que incluem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] suporte para versões específicas do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocolo.  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Versão de protocolo|Suporte introduzido em...|  
|-----------------------------------------------------------------------------------|----------------------------|  
|Versão 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] Versão 3|  
|Versão 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Uma atualização [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Você pode baixar e instalar a atualização a partir de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] versão 4|  
|Versão 3|-Você pode baixar e instalar uma versão de pré-lançamento que dá suporte a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] versão 3 do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=203885).|  
  
### <a name="metadata-versions"></a>Versões de metadados  
 Por padrão, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa a versão 1.1 do CSDL para representar um modelo de dados. Isso é sempre o caso para modelos de dados se baseiam em um provedor de reflexão ou um provedor de serviços de dados personalizados. No entanto, quando o modelo de dados é definido usando o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], a versão de CSDL retornado é o mesmo que a versão que é usada pelo [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. A versão de CSDL é determinada pelo namespace do [elemento Schema](http://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). Para obter mais informações, consulte a especificação [ \[MC CSDL\]: formato de arquivo de definição de esquema conceitual](http://go.microsoft.com/fwlink/?LinkId=159072).  
  
 O `DataServices` elemento de metadados retornados também contém um `DataServiceVersion` atributo, que é o mesmo valor como o `DataServiceVersion` cabeçalho na mensagem de resposta. Aplicativos cliente, como o **adicionar referência de serviço** caixa de diálogo no Visual Studio, use essas informações para o serviço de dados do cliente de gerar classes que funcionam corretamente com a versão do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] que hospedam o serviço de dados. Para obter mais informações, consulte [OData: controle de versão de protocolo](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
