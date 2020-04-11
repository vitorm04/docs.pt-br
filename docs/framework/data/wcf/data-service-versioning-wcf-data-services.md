---
title: Versão do serviço de dados (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121537"
---
# <a name="data-service-versioning-wcf-data-services"></a>Versão do serviço de dados (WCF Data Services)
O OData (Open Data Protocol, protocolo de dados abertos) permite criar serviços de dados para que os clientes possam acessar dados como recursos usando URIs que são baseados em um modelo de dados. O Data também suporta a definição de operações de serviço. Após a implantação inicial, e potencialmente várias vezes durante sua vida, esses serviços de dados podem precisar ser alterados por uma variedade de razões, como mudanças nas necessidades dos negócios, requisitos de tecnologia da informação ou para resolver outros problemas. Quando você faz alterações em um serviço de dados existente, você deve considerar se deve definir uma nova versão do seu serviço de dados e a melhor maneira de minimizar o impacto nos aplicativos clientes existentes. Este tópico fornece orientações sobre quando e como criar uma nova versão de um serviço de dados. Ele também descreve como o WCF Data Services lida com uma troca entre clientes e serviços de dados que suportam diferentes versões do protocolo OData.

## <a name="versioning-a-wcf-data-service"></a>Versão de um serviço de dados WCF
 Uma vez que um serviço de dados é implantado e os dados estão sendo consumidos, as alterações no serviço de dados têm o potencial de causar problemas de compatibilidade com os aplicativos clientes existentes. No entanto, como as mudanças são frequentemente exigidas pelas necessidades gerais de negócios do serviço, você deve considerar quando e como criar uma nova versão do seu serviço de dados com o menor impacto sobre os aplicativos do cliente.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Alterações do modelo de dados que recomendam uma nova versão do serviço de dados
 Ao considerar se publicar uma nova versão de um serviço de dados, é importante entender como os diferentes tipos de alterações podem afetar os aplicativos do cliente. Alterações em um serviço de dados que podem exigir que você crie uma nova versão de um serviço de dados podem ser divididas nas duas categorias a seguir:

- Alterações no contrato de serviço — que incluem atualizações nas operações de serviço, alterações na acessibilidade de conjuntos de entidades (feeds), alterações de versão e outras alterações nos comportamentos do serviço.

- Alterações no contrato de dados — que incluem alterações no modelo de dados, formatos de feed ou personalizações de alimentação.

 A tabela a seguir detalha quais tipos de alterações você deve considerar a publicação de uma nova versão do serviço de dados:

|Tipo de Alteração|Requer uma nova versão|Nova versão não é necessária|
|--------------------|----------------------------|----------------------------|
|Operações de serviço|- Adicionar novo parâmetro<br />- Alterar o tipo de retorno<br />- Remover operação de serviço|- Excluir parâmetros existentes<br />- Adicionar nova operação de serviço|
|Comportamentos de serviço|- Desativar solicitações de contagem<br />- Desativar suporte de projeção<br />- Aumente a versão de serviço de dados necessária|- Habilitar solicitações de contagem<br />- Habilitar suporte a projeção<br />- Diminua a versão de serviço de dados necessária|
|Permissões de conjunto de entidades|- Restringir permissões de conjunto de entidades<br />- Alterar código de resposta (novo valor do primeiro dígito) <sup>1</sup>|- Relaxe as permissões de definir entidade<br />- Alterar código de resposta (mesmo valor do primeiro dígito)|
|Propriedades da entidade|- Remover a propriedade ou relacionamento existente<br />- Adicionar propriedade não anulada<br />- Alterar a propriedade existente|- Adicionar propriedade anulada<sup>2</sup>|
|Conjuntos de entidades|- Remover conjunto de entidades|- Adicionar tipo derivado<br />- Alterar o tipo de base<br />- Adicionar conjunto de entidades|
|Personalização de alimentos|- Alterar o mapeamento de propriedades de entidade||

 <sup>1</sup> Isso pode depender de como estritamente um aplicativo cliente depende de receber um código de erro específico.

 <sup>2</sup> Você pode <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> definir `true` a propriedade para que o cliente ignore quaisquer novas propriedades enviadas pelo serviço de dados que não estão definidas no cliente. No entanto, quando as inserções são feitas, as propriedades não incluídas pelo cliente na solicitação POST são definidas como seus valores padrão. Para atualizações, quaisquer dados existentes em uma propriedade desconhecida do cliente podem ser substituídos com valores padrão. Neste caso, você deve enviar a atualização como uma solicitação de MESCLAGEM, que é o padrão. Para obter mais informações, consulte [Gerenciando o contexto do serviço de dados](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Como versão de um serviço de dados
 Quando necessário, uma nova versão de serviço de dados é definida criando uma nova instância do serviço com um contrato de serviço atualizado ou modelo de dados. Este novo serviço é então exposto usando um novo ponto final URI, que o diferencia da versão anterior. Por exemplo:

- Versão antiga:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nova versão:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Ao atualizar um serviço de dados, os clientes também precisarão ser atualizados com base nos novos metadados de serviço de dados e usar o novo URI raiz. Quando possível, você deve manter a versão anterior do serviço de dados para dar suporte a clientes que ainda não foram atualizados para usar a nova versão. Versões mais antigas de um serviço de dados podem ser removidas quando não são mais necessárias. Você deve considerar a manutenção do URI ponto final do serviço de dados em um arquivo de configuração externa.

## <a name="odata-protocol-versions"></a>Versões do protocolo OData
 À medida que novas versões do OData são lançadas, os aplicativos clientes podem não estar usando a mesma versão do protocolo OData que é suportado pelo serviço de dados. Um aplicativo cliente mais antigo pode acessar um serviço de dados que suporta uma versão mais recente do OData. Um aplicativo cliente também pode estar usando uma versão mais recente da biblioteca de clientes do WCF Data Services, que suporta uma versão mais recente do OData do que o serviço de dados que está sendo acessado.

 O WCF Data Services aproveita o suporte fornecido pela OData para lidar com esses cenários de versão. Há também suporte para gerar e usar metadados do modelo de dados para criar classes de serviço de dados do cliente quando o cliente usa uma versão diferente do OData do que o serviço de dados usa. Para obter mais informações, consulte a seção Versão de protocolo no artigo [OData: Visão geral.](https://www.odata.org/documentation/odata-version-2-0/overview/)

### <a name="version-negotiation"></a>Negociação de versão
 O serviço de dados pode ser configurado para definir a versão mais alta do protocolo OData que será usado pelo serviço, independentemente da versão solicitada pelo cliente. Você pode fazer isso <xref:System.Data.Services.Common.DataServiceProtocolVersion> especificando <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> um valor <xref:System.Data.Services.DataServiceBehavior> para a propriedade do usado pelo serviço de dados. Para obter mais informações, consulte [Configurando o Serviço de Dados](configuring-the-data-service-wcf-data-services.md).

 Quando um aplicativo usa as bibliotecas clientes do WCF Data Services para acessar um serviço de dados, as bibliotecas definem automaticamente esses cabeçalhos para os valores corretos, dependendo da versão do OData e dos recursos usados em seu aplicativo. Por padrão, o WCF Data Services usa a versão de protocolo mais baixa que suporta a operação solicitada.

 A tabela a seguir detalha as versões do .NET Framework e silverlight que incluem o suporte aos Serviços de Dados WCF para versões específicas do protocolo OData.

|Versão do protocolo OData|Suporte introduzido em...|
|-----------------------------------------------------------------------------------|----------------------------|
|Versão 1|- .NET Framework 3.5 Service Pack 1 (SP1)<br />- Silverlight versão 3|
|Versão 2|- .NET Framework 4<br />- Silverlight versão 4|

### <a name="metadata-versions"></a>Versões de metadados
 Por padrão, o WCF Data Services usa a versão 1.1 do CSDL para representar um modelo de dados. Este é sempre o caso de modelos de dados que são baseados em um provedor de reflexão ou em um provedor de serviços de dados personalizado. No entanto, quando o modelo de dados é definido usando o Quadro de Entidades, a versão do CSDL retornada é a mesma que a versão usada pelo Quadro de Entidades. A versão do CSDL é determinada pelo namespace do [elemento Schema (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 O `DataServices` elemento dos metadados retornados `DataServiceVersion` também contém um atributo, que é o mesmo valor do `DataServiceVersion` cabeçalho na mensagem de resposta. Os aplicativos clientes, como a caixa de diálogo **Adicionar referência** de serviço no Visual Studio, usam essas informações para gerar classes de serviço de dados do cliente que funcionam corretamente com a versão do WCF Data Services que hospeda o serviço de dados. Para obter mais informações, consulte a seção Versão de protocolo no artigo [OData: Visão geral.](https://www.odata.org/documentation/odata-version-2-0/overview/)

## <a name="see-also"></a>Confira também

- [Provedores de serviços de dados](data-services-providers-wcf-data-services.md)
- [Configurando WCF Data Services](defining-wcf-data-services.md)
