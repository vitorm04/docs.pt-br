---
title: Provedor de streaming (WCF Data Services)
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
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc3e7d545a502c040e7e3ee5140d385b60e82d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="streaming-provider-wcf-data-services"></a>Provedor de streaming (WCF Data Services)
Um serviço de dados pode expor dados de objeto binário grande. Esses dados binários podem representar fluxos de vídeo e áudio, imagens, arquivos de documento ou outros tipos de mídia binária. Quando uma entidade no modelo de dados inclui uma ou mais propriedades binárias, o serviço de dados retorna esses dados binários codificados como base 64 no feed de resposta. Como carregar e serializar os dados binários longos dessa maneira podem afetar o desempenho, o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] define um mecanismo para recuperar dados binários independentes da entidade à qual ela pertence. Isso é feito separando os dados binários da entidade em um ou mais fluxos de dados.  
  
-   Recurso de mídia - dados binários que pertencem a uma entidade, como vídeo, áudio, imagem ou outro tipo de fluxo de recurso de mídia.  
  
-   Entrada de link de mídia - uma entidade que tem uma referência a um fluxo de recurso de mídia relacionado.  
  
 Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você define um fluxo de recurso binário implementando um provedor de dados de streaming. A implementação de provedor de streaming fornece o serviço de dados com o fluxo de recurso de mídia associado a uma entidade específica como um <xref:System.IO.Stream> objeto. Essa implementação permite que o serviço de dados aceite e retorne recursos de mídia sobre HTTP como fluxos de dados binários de um tipo MIME especificado.  
  
 A configuração de um serviço de dados para oferecer suporte ao streaming de dados binários requer as seguintes etapas:  
  
1.  Atribua uma ou mais entidades no modelo de dados como uma entrada de link de mídia. Essas entidades não devem incluir os dados binários a serem transmitidos. Todas as propriedades binárias de uma entidade sempre são retornadas na entrada como binário codificado na base 64.  
  
2.  Implemente a interface T:System.Data.Services.Providers.IDataServiceStreamProvider.  
  
3.  Defina um serviço de dados que implemente a interface <xref:System.IServiceProvider>. O serviço de dados usa a implementação de <xref:System.IServiceProvider.GetService%2A> para acessar a implementação do provedor de dados de streaming. Esse método retorna a implementação de provedor de streaming apropriada.  
  
4.  Ative fluxos de mensagem grandes na configuração de aplicativo Web.  
  
5.  Habilitar o acesso aos recursos binários no servidor ou em uma fonte de dados.  
  
 Os exemplos neste tópico se baseiam em uma amostra de streaming de serviço de fotos, que é discutido em detalhes na postagem do [Streaming série de provedor de serviços de dados: Implementando um provedor de Streaming (parte 1)](http://go.microsoft.com/fwlink/?LinkID=198989). O código-fonte para esse serviço de exemplo está disponível na [página de exemplo de serviço de dados de foto Streaming](http://go.microsoft.com/fwlink/?LinkID=198988) na Galeria de códigos do MSDN.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Definindo uma entrada de link de mídia no modelo de dados  
 O provedor de fonte de dados determina a maneira que uma entidade é definida como uma entrada de link de mídia no modelo de dados.  
  
 **Entity Framework Provider** (Provedor de Entity Framework)  
 Para indicar que uma entidade é uma entrada de link de mídia, adicione o atributo `HasStream` à definição de tipo de entidade no modelo conceitual, como no exemplo a seguir:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Você também deve adicionar o namespace `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` à entidade ou à raiz do arquivo .edmx ou .csdl que define o modelo de dados.  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]um serviço de dados que usa o [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provedor e expõe um recurso de mídia, consulte a postagem [Streaming série de provedor de serviços de dados: Implementando um provedor de Streaming (parte 1)](http://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Provedor de reflexão**  
 Para indicar que uma entidade é uma entrada de link de mídia, adicione o <xref:System.Data.Services.Common.HasStreamAttribute> à classe que define o tipo de entidade no provedor de reflexão.  
  
 **Provedor de serviços de dados personalizados**  
 Ao usar provedores de serviços personalizados, você implementa a interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> para definir os metadados do serviço de dados. Para obter mais informações, consulte [provedores de serviço de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Você indica que um fluxo de recurso binário pertence a um <xref:System.Data.Services.Providers.ResourceType> definindo a propriedade <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> para `true` no <xref:System.Data.Services.Providers.ResourceType> que representa o tipo de entidade, que é uma entrada de link de mídia.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>Implementando a interface IDataServiceStreamProvider  
 Para criar um serviço de dados que oferece suporte a fluxos de dados binários, você deve implementar a interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Essa implementação permite que o serviço de dados retorne dados binários como um fluxo para o cliente e consuma dados binários como um fluxo enviado pelo cliente. O serviço de dados cria uma instância dessa interface sempre que precisa acessar dados binários como um fluxo. A interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider> especifica os seguintes membros:  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Este método é chamado pelo serviço de dados para excluir o recurso de mídia correspondente quando sua entrada de link de mídia é excluída. Quando você implementa o <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, este método contém o código que exclui o recurso de mídia associado à entrada de link de mídia fornecida.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Este método é chamado pelo serviço de dados para retornar um recurso de mídia como um fluxo. Quando você implementa o <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, este método contém o código que fornece um fluxo usado pelo serviço de dados ao recurso de mídia de retorno que está associado à entrada de link de mídia fornecida.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Este método é chamado pelo serviço de dados para retornar o URI usado para solicitar o recurso de mídia da entrada de link de mídia. Esse valor é usado para criar o atributo `src` no elemento de conteúdo da entrada de link de mídia que é usado para solicitar o fluxo de dados. Quando este método retorna `null`, o serviço de dados determina automaticamente o URI. Use este método quando precisar fornecer aos clientes acesso direto aos dados binários sem usar o provedor de streaming.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Este método é chamado pelo serviço de dados para retornar o valor Content-Type do recurso de mídia associado à entrada de link de mídia especificada.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Este método é chamado pelo serviço de dados para retornar o eTag do fluxo de dados associado à entidade especificada. Este método é usado quando você gerencia a simultaneidade dos dados binários. Quando este método retorna um valor nulo, o serviço de dados não rastreia a simultaneidade.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Este método é chamado pelo serviço de dados para obter o fluxo usado durante o recebimento do fluxo enviado pelo cliente. Quando você implementar o <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, deverá retornar um fluxo gravável no qual o serviço de dados grava os dados de fluxo recebidos.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Retorna um nome de tipo qualificado para namespace que representa o tipo que o tempo de execução do serviço de dados deve criar para a entrada de link de mídia associada ao fluxo de dados do recurso de mídia que está sendo inserido.|  
  
## <a name="creating-the-streaming-data-service"></a>Criando o serviço de dados de streaming  
 Para fornecer o tempo de execução do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] com acesso à implementação do <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, o serviço de dados que você cria também deve implementar a interface <xref:System.IServiceProvider>. O exemplo a seguir mostra como implementar o método <xref:System.IServiceProvider.GetService%2A> para retornar uma instância da classe `PhotoServiceStreamProvider` que implementa o <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Para obter informações gerais sobre como criar um serviço de dados, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Ativando os fluxos de binário grandes no ambiente de hospedagem  
 Quando você cria um serviço de dados em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é usado para fornecer a implementação do protocolo HTTP. Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limita o tamanho de mensagens HTTP para apenas 65 mil bytes. Para transmitir dados binários grandes para e do serviço de dados, você também deve configurar o aplicativo Web para ativar arquivos binários grandes e usar fluxos de transferência. Para fazer isso, adicione o seguinte ao elemento `<configuration />` do arquivo Web.config do aplicativo:  
  
  
  
> [!NOTE]
>  Você deve usar um modo de transferência <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> para garantir que os dados binários nas mensagens de resposta e de solicitação sejam transmitidos e não armazenados em buffer pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Para obter mais informações, consulte [Streaming de transferência de mensagens](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) e [cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Por padrão, os Serviços de Informações da Internet (IIS) também limita o tamanho das solicitações a 4 MB. Para habilitar o serviço de dados receber mais de 4MB de fluxos quando em execução no IIS, você também deve definir o `maxRequestLength` atributo do [httpRuntime Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/e9b81350-8aaf-47cc-9843-5f7d0c59f369) no `<system.web />` seção de configuração, como como mostrado no exemplo a seguir:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Usando fluxos de dados em um aplicativo cliente  
 A biblioteca de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite a recuperação e a atualização desses recursos expostos como fluxos binários no cliente. Para obter mais informações, consulte [trabalhando com dados binários](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Considerações para trabalhar com um provedor de streaming  
 Considere o seguinte ao implementar um provedor de streaming e acessar recursos de mídia de um serviço de dados.  
  
-   Não há suporte para solicitações MERGE nos recursos de mídia. Use uma solicitação PUT para alterar o recurso de mídia de uma entidade existente.  
  
-   Uma solicitação POST não pode ser usada para criar uma nova entrada de link de mídia. Em vez disso, você deve emitir uma solicitação POST para criar um novo recurso de mídia, e o serviço de dados cria uma nova entrada de link de mídia com os valores padrão. Essa nova entidade pode ser atualizada por uma solicitação MERGE ou PUT subsequente. Você também pode considerar o armazenamento em cache e fazer atualizações na área de descarte, como definir o valor da propriedade para o valor do cabeçalho de campo de dados dinâmico na solicitação POST.  
  
-   Quando uma solicitação POST for recebida, o serviço de dados chamará o <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> para criar o recurso de mídia antes que ele chame <xref:System.Data.Services.IUpdatable.SaveChanges%2A> para criar a entrada de link de mídia.  
  
-   Uma implementação do <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> não deve retornar um objeto <xref:System.IO.MemoryStream>. Quando você usar esse tipo de fluxo, os problemas de recurso de memória ocorrerão quando o serviço receber fluxos de dados muito grandes.  
  
-   Considere o seguinte ao armazenar recursos de mídia em um banco de dados:  
  
    -   Uma propriedade binária que é um recurso de mídia não deve ser incluída no modelo de dados. Todas as propriedades expostas em um modelo de dados são retornadas na entrada em um feed de resposta.  
  
    -   Para melhorar o desempenho com um fluxo binário grande, é recomendável que você crie uma classe de fluxo personalizada para armazenar dados binários no banco de dados. Essa classe é retornado pela implementação do <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> e envia os dados binários ao banco de dados em partes. Para um [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] banco de dados, é recomendável que você use um FILESTREAM para o fluxo de dados no banco de dados quando os dados binários são maiores que 1 MB.  
  
    -   Verifique se o banco de dados foi projetado para armazenar os fluxos binários grandes que serão recebidos pelo serviço de dados.  
  
    -   Quando um cliente enviar uma solicitação POST para inserir uma entrada de link de mídia com um recurso de mídia em uma única solicitação, o <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> será chamado para obter o fluxo antes que o serviço de dados insira a nova entidade no banco de dados. Uma implementação de provedor de streaming deve ser capaz de manipular esse comportamento do serviço de dados. É recomendável usar uma tabela de dados separada para armazenar os dados binários ou para armazenar o fluxo de dados em um arquivo até depois da inserção da entidade no banco de dados.  
  
-   Ao implementar os métodos <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, o <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A> ou o <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>, você deve usar os valores eTag e Content-Type fornecidos como parâmetros do método. Não defina cabeçalhos eTag ou Content-Type na implementação do provedor <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
-   Por padrão, o cliente envia fluxos binários grandes usando uma codificação de transferência HTTP em partes. Porque o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server não dá suporte a esse tipo de codificação, você não pode usar esse servidor Web para hospedar um serviço de dados de transmissão que deve aceitar fluxos binários grandes. Para obter mais informações sobre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server, consulte [servidores Web no Visual Studio para projetos Web ASP.NET](http://msdn.microsoft.com/en-us/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Requisitos de controle de versão  
 O provedor de streaming tem os seguintes requisitos de controle de versão do protocolo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]:  
  
-   O provedor de streaming requer que o serviço de dados ofereça suporte à versão 2.0 do protocolo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e às versões posteriores.  
  
 Para obter mais informações, consulte [controle de versão de serviço de dados](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Provedores de serviços de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [Trabalhando com os dados binários](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
