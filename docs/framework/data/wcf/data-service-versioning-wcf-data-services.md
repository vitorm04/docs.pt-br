---
title: Controle de versão do serviço de dados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 03ac1e0a5fec2d7def91466a9dc31853e2007f57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791064"
---
# <a name="data-service-versioning-wcf-data-services"></a>Controle de versão do serviço de dados (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] permite que você crie serviços de dados para que os clientes possam acessar dados como recursos usando URIs baseados em um modelo de dados. O OData também dá suporte à definição de operações de serviço. Após a implantação inicial e, potencialmente, várias vezes durante o tempo de vida, esses serviços de dados talvez precisem ser alterados por vários motivos, como mudanças nas necessidades dos negócios, requisitos de tecnologia da informação ou para resolver outros problemas. Quando você faz alterações em um serviço de dados existente, deve considerar se deseja definir uma nova versão do seu serviço de dados e como é melhor minimizar o impacto em aplicativos cliente existentes. Este tópico fornece orientação sobre quando e como criar uma nova versão de um serviço de dados. Ele também descreve como o WCF Data Services lida com uma troca entre clientes e serviços de dados que dão suporte a versões diferentes do protocolo OData.

## <a name="versioning-a-wcf-data-service"></a>Controle de versão de um serviço de dados WCF
 Depois que um serviço de dados é implantado e os dados estão sendo consumidos, as alterações no serviço de dados têm o potencial de causar problemas de compatibilidade com os aplicativos cliente existentes. No entanto, como as alterações geralmente são exigidas pelas necessidades de negócios gerais do serviço, você deve considerar quando e como criar uma nova versão do serviço de dados com o impacto mínimo sobre os aplicativos cliente.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Alterações no modelo de dados que recomendam uma nova versão do serviço de dados
 Ao considerar se uma nova versão de um serviço de dados deve ser publicada, é importante entender como os diferentes tipos de alterações podem afetar os aplicativos cliente. As alterações em um serviço de dados que podem exigir que você crie uma nova versão de um serviço de dados podem ser divididas nas duas categorias a seguir:

- Alterações no contrato de serviço — que incluem atualizações para operações de serviço, alterações na acessibilidade de conjuntos de entidades (feeds), alterações de versão e outras alterações nos comportamentos de serviço.

- Alterações no contrato de dados — que incluem alterações no modelo de dados, formatos de feed ou personalizações de feed.

 A tabela a seguir fornece detalhes sobre quais tipos de alterações você deve considerar para publicar uma nova versão do serviço de dados:

|Tipo de alteração|Requer uma nova versão|Nova versão não necessária|
|--------------------|----------------------------|----------------------------|
|Operações de serviço|-Adicionar novo parâmetro<br />-Alterar tipo de retorno<br />-Remover operação de serviço|-Excluir parâmetro existente<br />-Adicionar nova operação de serviço|
|Comportamentos de serviço|-Desabilitar solicitações de contagem<br />-Desabilitar suporte à projeção<br />-Aumentar a versão do serviço de dados necessária|-Habilitar solicitações de contagem<br />-Habilitar suporte à projeção<br />-Diminuir a versão do serviço de dados necessária|
|Permissões do conjunto de entidades|-Restringir permissões do conjunto de entidades<br />-Alterar código de resposta (novo valor do primeiro dígito) <sup>1</sup>|-Relaxar as permissões do conjunto de entidades<br />-Alterar código de resposta (mesmo valor do primeiro dígito)|
|Propriedades da entidade|-Remover propriedade ou relação existente<br />-Adicionar Propriedade não anulável<br />-Alterar propriedade existente|-Adicionar Propriedade Anulável<sup>2</sup>|
|Conjuntos de entidades|-Remover conjunto de entidades|-Adicionar tipo derivado<br />-Alterar tipo de base<br />-Adicionar conjunto de entidades|
|Personalização do feed|-Alterar mapeamento de propriedade de entidade||

 <sup>1</sup> isso pode depender de quão estritamente um aplicativo cliente depende do recebimento de um código de erro específico.

 <sup>2</sup> você pode definir a <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> Propriedade como `true` para que o cliente ignore todas as novas propriedades enviadas pelo serviço de dados que não estão definidas no cliente. No entanto, quando são feitas inserções, as propriedades não incluídas pelo cliente na solicitação POST são definidas com seus valores padrão. Para atualizações, todos os dados existentes em uma propriedade desconhecida para o cliente podem ser substituídos por valores padrão. Nesse caso, você deve enviar a atualização como uma solicitação de MESCLAgem, que é o padrão. Para obter mais informações, consulte [Gerenciando o contexto do serviço de dados](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Como fazer a versão de um serviço de dados
 Quando necessário, uma nova versão do serviço de dados é definida pela criação de uma nova instância do serviço com um contrato de serviço ou modelo de dados atualizado. Esse novo serviço é então exposto usando um novo ponto de extremidade de URI, que o diferencia da versão anterior. Por exemplo:

- Versão antiga:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nova versão:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Ao atualizar um serviço de dados, os clientes também precisarão ser atualizados com base nos novos metadados do serviço de dados e usar o novo URI de raiz. Quando possível, você deve manter a versão anterior do serviço de dados para dar suporte a clientes que ainda não foram atualizados para usar a nova versão. As versões mais antigas de um serviço de dados podem ser removidas quando não são mais necessárias. Você deve considerar a manutenção do URI do ponto de extremidade do serviço de dados em um arquivo de configuração externo.

## <a name="odata-protocol-versions"></a>Versões do protocolo OData
 À medida que novas versões do OData são lançadas, os aplicativos cliente podem não estar usando a mesma versão do protocolo OData com suporte no serviço de dados. Um aplicativo cliente mais antigo pode acessar um serviço de dados que dá suporte a uma versão mais recente do OData. Um aplicativo cliente também pode estar usando uma versão mais recente da biblioteca de cliente WCF Data Services, que dá suporte a uma versão mais recente do OData do que o serviço de dados que está sendo acessado.

 WCF Data Services aproveita o suporte fornecido pelo OData para lidar com esses cenários de controle de versão. Também há suporte para gerar e usar metadados de modelo de dados para criar classes de serviço de dados do cliente quando o cliente usa uma versão diferente do OData do que o serviço de dados usa. Para obter mais informações, [consulte OData: Controle de versão](https://go.microsoft.com/fwlink/?LinkId=186071)de protocolo.

### <a name="version-negotiation"></a>Negociação de versão
 O serviço de dados pode ser configurado para definir a versão mais recente do protocolo OData que será usada pelo serviço, independentemente da versão solicitada pelo cliente. Você pode fazer isso especificando um <xref:System.Data.Services.Common.DataServiceProtocolVersion> valor para a <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> Propriedade do <xref:System.Data.Services.DataServiceBehavior> usado pelo serviço de dados. Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md).

 Quando um aplicativo usa as bibliotecas de cliente WCF Data Services para acessar um serviço de dados, as bibliotecas definem automaticamente esses cabeçalhos com os valores corretos, dependendo da versão do OData e dos recursos que são usados em seu aplicativo. Por padrão, WCF Data Services usa a versão de protocolo mais baixa que dá suporte à operação solicitada.

 A tabela a seguir detalha as versões do .NET Framework e do Silverlight que incluem WCF Data Services suporte a versões específicas do protocolo OData.

|Versão do protocolo OData|Suporte introduzido em...|
|-----------------------------------------------------------------------------------|----------------------------|
|Versão 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Service Pack 1 (SP1)<br />-Silverlight versão 3|
|Versão 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Uma atualização para [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] o SP1. Você pode baixar e instalar a atualização no [centro de download da Microsoft](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-Silverlight versão 4|
|Versão 3|-Você pode baixar e instalar uma versão de pré-lançamento que dá suporte à versão 3 do OData no [centro de download da Microsoft](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Versões de metadados
 Por padrão, WCF Data Services usa a versão 1,1 do CSDL para representar um modelo de dados. Esse é sempre o caso para modelos de dados que se baseiam em um provedor de reflexão ou em um provedor de serviços de dados personalizado. No entanto, quando o modelo de dados é definido [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]usando o, a versão de CSDL retornada é igual à versão usada [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]pelo. A versão do CSDL é determinada pelo namespace do [elemento Schema (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 O `DataServices` elemento dos metadados retornados também contém um `DataServiceVersion` atributo, que é o mesmo valor que o `DataServiceVersion` cabeçalho na mensagem de resposta. Aplicativos cliente, como a caixa de diálogo **Adicionar referência de serviço** no Visual Studio, usam essas informações para gerar classes de serviço de dados do cliente que funcionam corretamente com a versão do WCF Data Services que hospeda o serviço de dados. Para obter mais informações, [consulte OData: Controle de versão](https://go.microsoft.com/fwlink/?LinkId=186071)de protocolo.

## <a name="see-also"></a>Consulte também

- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)
