---
title: Controle de versão de serviço de dados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 9a92346267012d3651d04648b357bbf530097e34
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705702"
---
# <a name="data-service-versioning-wcf-data-services"></a>Controle de versão de serviço de dados (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] permite que você crie serviços de dados para que os clientes podem acessar dados como utilizando URIs de recursos com base em um modelo de dados. OData também suporta a definição de operações de serviço. Após a implantação inicial e possivelmente várias vezes durante a vida, esses serviços de dados podem precisar ser alterada para uma variedade de motivos, como mudanças nas necessidades comerciais, requisitos de tecnologia de informações, ou para resolver outros problemas. Quando você faz alterações em um serviço de dados existente, você deve considerar se deseja definir uma nova versão de seus dados de serviço e a melhor maneira de minimizar o impacto em aplicativos cliente existentes. Este tópico fornece diretrizes sobre quando e como criar uma nova versão de um serviço de dados. Ele também descreve como o WCF Data Services lida com uma troca entre clientes e serviços de dados que dão suporte a diferentes versões do protocolo OData.

## <a name="versioning-a-wcf-data-service"></a>Controle de versão de um WCF Data Service
 Depois que um serviço de dados é implantado e os dados que está sendo consumidos, as alterações ao serviço de dados têm o potencial de causar problemas de compatibilidade com aplicativos cliente existentes. No entanto, como alterações frequentemente precisam cumprir as necessidades de negócios geral do serviço, você deve considerar quando e como criar uma nova versão do seu serviço de dados com menos impacto no cliente de aplicativos.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Alterações do modelo de dados que recomenda uma nova versão do serviço de dados
 Ao considerar se pode publicar uma nova versão de um serviço de dados, é importante entender como os diferentes tipos de alterações podem afetar os aplicativos cliente. Alterações em um serviço de dados que podem exigir que você crie uma nova versão de um serviço de dados podem ser divididas em duas categorias a seguir:

-   Altera para o contrato de serviço — que incluem atualizações para operações de serviço, as alterações a acessibilidade de conjuntos de entidades (feeds), as alterações de versão e outras alterações de comportamentos de serviço.

-   Altera para o contrato de dados — que incluem as alterações no modelo de dados, formatos de feed ou personalizações de feed.

 A tabela a seguir detalha para quais tipos de alterações, você deve considerar uma nova versão do serviço de dados de publicação:

|Tipo de alteração|Requer uma nova versão|Nova versão não necessária|
|--------------------|----------------------------|----------------------------|
|Operações de serviço|-Adicionar o novo parâmetro<br />-Alterar tipo de retorno<br />-Remova a operação de serviço|-Excluir o parâmetro existente<br />-Adicionar nova operação de serviço|
|Comportamentos de serviço|-Desabilitar solicitações de contagem<br />-Desabilite o suporte de projeção<br />-Aumente a versão do serviço de dados necessários|-Habilitar solicitações de contagem<br />-Habilitar o suporte de projeção<br />-Diminuir a versão do serviço de dados necessários|
|Permissões do conjunto de entidades|-Restringir permissões de conjunto de entidade<br />-Alterar o código de resposta (novo valor do primeiro dígito) <sup>1</sup>|-Relaxar definir permissões de entidade<br />-Alterar o código de resposta (mesmo valor do primeiro dígito)|
|Propriedades da entidade|-Remover propriedade existente ou relação<br />-Adicionar a propriedade não anulável<br />-Alterar a propriedade existente|-Adicionar a propriedade nullable<sup>2</sup>|
|Conjuntos de entidades|-Remova o conjunto de entidades|-Adicionar o tipo derivado<br />-Altere o tipo base<br />-Adicionar conjunto de entidades|
|Personalização de feed|-Alterar o mapeamento de propriedade de entidade||

 <sup>1</sup> isso depende estritamente como um aplicativo cliente se baseia em um código de erro específico.

 <sup>2</sup> você pode definir o <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriedade `true` para que o cliente a ignorar qualquer nova propriedade enviada pelo serviço de dados que não está definida no cliente. No entanto, quando as inserções são feitas, as propriedades não são incluídas pelo cliente na solicitação POST são definidas para seus valores padrão. Para obter atualizações, todos os dados existentes em uma propriedade desconhecida para o cliente poderão ser substituídos por valores padrão. Nesse caso, você deve enviar a atualização como uma solicitação de mesclagem, que é o padrão. Para obter mais informações, consulte [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Como a versão de um serviço de dados
 Quando for necessário, uma nova versão do serviço de dados é definida criando uma nova instância do serviço com um modelo de dados ou contrato de serviço atualizado. Esse novo serviço, em seguida, é exposto por meio de um novo URI ponto de extremidade que diferencie-a da versão anterior. Por exemplo:

-   Versão antiga: `http://services.odata.org/Northwind/v1/Northwind.svc/`

-   Nova versão: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Ao atualizar um serviço de dados, os clientes precisarão também ser atualizados com base nos novos metadados de serviço de dados e usar a nova raiz do URI. Quando possível, você deve manter a versão anterior do serviço de dados para dar suporte a clientes que ainda não foram atualizados para usar a nova versão. Versões mais antigas de um serviço de dados podem ser removidas quando eles não são mais necessários. Você deve considerar a manter o ponto de extremidade de serviço de dados URI no arquivo de configuração externo.

## <a name="odata-protocol-versions"></a>Versões do protocolo OData
 Quando são lançadas novas versões do OData, os aplicativos cliente podem não estar usando a mesma versão do protocolo OData que é compatível com o serviço de dados. Um aplicativo de cliente mais antigo pode acessar um serviço de dados que dá suporte a uma versão mais recente do OData. Um aplicativo cliente também pode usar uma versão mais recente da biblioteca de cliente WCF Data Services, que dá suporte a uma versão mais recente do OData que o serviço de dados que está sendo acessado.

 WCF Data Services utiliza o suporte fornecido pelo OData para lidar com esses cenários de controle de versão. Também há suporte para gerar e usar os metadados de modelo de dados para criar classes de serviço de dados de cliente quando o cliente usa uma versão diferente do OData que os dados de serviço usa. Para obter mais informações, consulte [OData: controle de versão do protocolo](https://go.microsoft.com/fwlink/?LinkId=186071).

### <a name="version-negotiation"></a>Negociação de versão
 O serviço de dados pode ser configurado para definir a versão mais recente do protocolo OData que será usado pelo serviço, independentemente da versão solicitada pelo cliente. Você pode fazer isso especificando um <xref:System.Data.Services.Common.DataServiceProtocolVersion> de valor para o <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> propriedade do <xref:System.Data.Services.DataServiceBehavior> usado pelo serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

 Quando um aplicativo usa as bibliotecas de cliente do WCF Data Services para acessar um serviço de dados, as bibliotecas definido automaticamente esses cabeçalhos para os valores corretos, dependendo da versão do OData e dos recursos que são usados em seu aplicativo. Por padrão, o WCF Data Services usa a versão mais antiga do protocolo que dá suporte à operação solicitada.

 A tabela a seguir fornece detalhes sobre as versões do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] que incluem o suporte para versões específicas do protocolo OData WCF Data Services.

|Versão do protocolo OData|Suporte introduzido no...|
|-----------------------------------------------------------------------------------|----------------------------|
|Versão 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] versão 3|
|Versão 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Uma atualização para [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Você pode baixar e instalar a atualização a partir de [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] versão 4|
|versão 3|-Você pode baixar e instalar uma versão de pré-lançamento que dá suporte a OData versão 3 das [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Versões de metadados
 Por padrão, o WCF Data Services usa a versão 1.1 do CSDL para representar um modelo de dados. Isso é sempre o caso para modelos de dados que são baseados em um provedor de reflexão ou um provedor de serviços de dados personalizados. No entanto, quando o modelo de dados é definido usando o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], a versão do CSDL retornado é o mesmo que a versão que é usada pelo [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. A versão do CSDL é determinada pelo namespace do [elemento de esquema](https://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). Para obter mais informações, consulte a especificação [ \[CSDL MC\]: formato de arquivo de definição de esquema conceitual](https://go.microsoft.com/fwlink/?LinkId=159072).

 O `DataServices` elemento de metadados retornados também contém uma `DataServiceVersion` atributo, que é o mesmo valor como o `DataServiceVersion` cabeçalho na mensagem de resposta. Aplicativos cliente, como o **adicionar referência de serviço** caixa de diálogo no Visual Studio, use essas informações para gerar classes de serviço de dados do cliente que funcionem corretamente com a versão do WCF Data Services que hospedam o serviço de dados. Para obter mais informações, consulte [OData: controle de versão do protocolo](https://go.microsoft.com/fwlink/?LinkId=186071).

## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
