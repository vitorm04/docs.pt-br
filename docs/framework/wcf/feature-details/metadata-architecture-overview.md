---
title: "Visão geral da arquitetura de metadados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1fa7fea1709f2664abe45ebdb916183a46885612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-architecture-overview"></a>Visão geral da arquitetura de metadados
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece uma infraestrutura avançada para exportar, publicação, recuperar e importação de metadados de serviço. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os serviços usam metadados para descrever como interagir com pontos de extremidade do serviço para que as ferramentas, como Svcutil.exe, podem gerar automaticamente o código do cliente para acessar o serviço.  
  
 A maioria dos tipos de que compõem o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadados infraestrutura residem no <xref:System.ServiceModel.Description> namespace.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o <xref:System.ServiceModel.Description.ServiceEndpoint> classe para descrever os pontos de extremidade em um serviço. Você pode usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para gerar metadados para pontos de extremidade de serviço ou importar metadados de serviço para gerar <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]representa os metadados para um serviço como uma instância das <xref:System.ServiceModel.Description.MetadataSet> tipo, a estrutura dos quais está intimamente ligada para o formato de serialização de metadados definido no WS-MetadataExchange. O <xref:System.ServiceModel.Description.MetadataSet> tipo empacota os metadados de serviço real, como documentos WSDL Web Services Description Language (), documentos de esquema XML ou expressões de WS-Policy, como uma coleção de <xref:System.ServiceModel.Description.MetadataSection> instâncias. Cada <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> instância contém um dialeto de metadados específico e um identificador. Um <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> pode conter os seguintes itens em seu <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> propriedade:  
  
-   Metadados bruto.  
  
-   Uma instância de <xref:System.ServiceModel.Description.MetadataReference>.  
  
-   Uma instância de <xref:System.ServiceModel.Description.MetadataLocation>.  
  
 Um <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> instâncias apontam para outro ponto de extremidade de troca (MEX) de metadados e <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> instâncias apontam para um documento de metadados usando uma URL HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte ao uso de documentos WSDL para descrever os pontos de extremidade de serviço, contratos de serviço, associações, mensagem de troca padrões, mensagens e implementadas por um serviço de mensagens de falha. Tipos de dados usados pelo serviço são descritos em documentos WSDL usando o esquema XML. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Esquema de importação e exportação](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). Você pode usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para exportar e importar as extensões WSDL para o comportamento de serviço, contrato de comportamentos e elementos de associação que estendem a funcionalidade de um serviço. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Exportação de metadados de serviço  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], *exportação de metadados* é o processo de descrever os pontos de extremidade de serviço e projeção-los em uma representação padronizada paralela que os clientes podem usar para entender como usar o serviço. Para exportar metadados de <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias, use uma implementação do <xref:System.ServiceModel.Description.MetadataExporter> classe abstrata. Um <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementação gera metadados que é encapsulado em um <xref:System.ServiceModel.Description.MetadataSet> instância.  
  
 O <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> classe fornece uma estrutura para a geração de expressões de política que descrevem os recursos e requisitos de uma associação de ponto de extremidade e suas operações associadas, mensagens e falhas. Essas expressões de política são capturadas em um <xref:System.ServiceModel.Description.PolicyConversionContext> instância. Um <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementação pode, em seguida, anexar essas expressões de política para os metadados que ele gera.  
  
 O <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> chamadas em cada <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> que implementa o <xref:System.ServiceModel.Description.IPolicyExportExtension> interface na associação de um <xref:System.ServiceModel.Description.ServiceEndpoint> ao gerar uma <xref:System.ServiceModel.Description.PolicyConversionContext> de objeto para o <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> implementação para usar. Você pode exportar novas declarações de política Implementando o <xref:System.ServiceModel.Description.IPolicyExportExtension> interface em suas implementações personalizadas do <xref:System.ServiceModel.Channels.BindingElement> tipo.  
  
 O <xref:System.ServiceModel.Description.WsdlExporter> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> acompanha de classe abstrata [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. O <xref:System.ServiceModel.Description.WsdlExporter> tipo gera metadados WSDL com expressões de política anexada.  
  
 Para exportar metadados WSDL personalizado ou extensões WSDL para comportamentos de ponto de extremidade, comportamentos de contrato ou elementos de associação em um ponto de extremidade de serviço, você pode implementar o <xref:System.ServiceModel.Description.IWsdlExportExtension> interface. O <xref:System.ServiceModel.Description.WsdlExporter> examina um <xref:System.ServiceModel.Description.ServiceEndpoint> instância para associar elementos, comportamentos de operação, comportamentos de contrato e comportamentos de ponto de extremidade que implementam o <xref:System.ServiceModel.Description.IWsdlExportExtension> interface ao gerar o documento WSDL.  
  
## <a name="publishing-service-metadata"></a>Metadados do serviço de publicação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Serviços de publicar metadados ao expor um ou mais pontos de extremidade de metadados. Publicar metadados de serviço torna metadados de serviço disponíveis usando protocolos padronizados, como solicitações de MEX e HTTP/GET. Pontos de extremidade de metadados são semelhantes para outros pontos de extremidade de serviço têm um endereço, uma ligação e um contrato. Você pode adicionar pontos de extremidade de metadados para um host de serviço na configuração ou no código.  
  
 Para publicar pontos de extremidade de metadados para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço, primeiro você deve adicionar uma instância do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço. Adicionando um <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instância para seu serviço aumenta seu serviço com a capacidade de publicar metadados ao expor um ou mais pontos de extremidade de metadados. Depois de adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> comportamento de serviço, em seguida, você pode expor pontos de extremidade de metadados que dão suporte os MEX protocolo ou metadados de pontos de extremidade que respondem às solicitações HTTP/GET.  
  
 Para adicionar pontos de extremidade de metadados que usam o protocolo MEX, adicione pontos de extremidade de serviço para o host de serviço que usam o contrato de serviço chamado IMetadataExchange.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Define o <xref:System.ServiceModel.Description.IMetadataExchange> interface que tem esse nome de contrato de serviço. Pontos de extremidade do WS-MetadataExchange ou pontos de extremidade MEX, podem usar uma das associações quatro padrão expostas pelos métodos de fábrica estáticos no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe para corresponder as associações padrão usadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ferramentas, como o Svcutil.exe. Você também pode configurar pontos de extremidade de metadados MEX usando uma associação personalizada.  
  
 O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usa um <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> para exportação de metadados para todos os pontos de extremidade de serviço em seu serviço. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]exportação de metadados de um serviço, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> aumenta o host de serviço, adicionando um <xref:System.ServiceModel.Description.ServiceMetadataExtension> instância como uma extensão para o host de serviço. O <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> fornece a implementação para os protocolos de publicação de metadados. Você também pode usar o <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> para obter metadados do serviço em tempo de execução, acessando o <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> propriedade.  
  
> [!CAUTION]
>  Se você adicionar um ponto de extremidade MEX em seu arquivo de configuração do aplicativo e, em seguida, tentar adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> com o host de serviço em código tenha a seguinte exceção:  
>   
>  System. InvalidOperationException: O nome do contrato 'IMetadataExchange' não pôde ser encontrado na lista de contratos implementados pelo serviço Service1. Adicione um ServiceMetadataBehavior ao arquivo de configuração ou ao ServiceHost diretamente para habilitar o suporte para este contrato.  
>   
>  Você pode contornar esse problema, adicionando o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> no arquivo de configuração ou ao adicionar o ponto de extremidade e <xref:System.ServiceModel.Description.ServiceMetadataBehavior> no código.  
>   
>  Para obter um exemplo de adição de <xref:System.ServiceModel.Description.ServiceMetadataBehavior> em um arquivo de configuração do aplicativo, consulte o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). Para obter um exemplo de adição de <xref:System.ServiceModel.Description.ServiceMetadataBehavior> no código, consulte o [auto-host](../../../../docs/framework/wcf/samples/self-host.md) exemplo.  
  
> [!CAUTION]
>  Quando os metadados de publicação para um serviço que expõe dois serviços diferentes contratos qual cada contêm uma operação com o mesmo nome de uma exceção será lançada. Por exemplo, se você tiver um serviço que expõe um contrato de serviço chamado ICarService que tem uma operação obter (Car c) e o mesmo serviço expõe um contrato de serviço chamado IBookService que tem uma operação Get (catálogo b), uma exceção será lançada ou uma mensagem de erro é exibida quando a geração de metadados do serviço. Para contornar esse problema, faça o seguinte:  
>   
>  -   Renomeie uma das operações.  
> -   Definir o <xref:System.ServiceModel.OperationContractAttribute.Name%2A> para um nome diferente.  
> -   Defina um dos namespaces as operações em um namespace diferente usando o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.  
  
## <a name="retrieving-service-metadata"></a>Recuperando metadados de serviço  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pode recuperar metadados de serviço usando protocolos padronizados, como WS-MetadataExchange e HTTP. Ambos os protocolos com suporte a <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo. Recuperar metadados de serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo fornecendo um endereço e uma associação opcional. A associação usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância pode ser uma das associações padrão da <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe estática, uma associação fornecida pelo usuário ou uma associação carregado de uma configuração de ponto de extremidade para o `IMetadataExchange` contrato. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> também pode resolver referências de URL de HTTP a metadados usando o <xref:System.Net.HttpWebRequest> tipo.  
  
 Por padrão, um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância está associada a um único <xref:System.ServiceModel.Channels.ChannelFactoryBase> instância. Você pode alterar ou substituir o <xref:System.ServiceModel.Channels.ChannelFactoryBase> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> , substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> método virtual. Da mesma forma, você pode alterar ou substituir o <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para fazer solicitações HTTP/GET, substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> método virtual.  
  
 Você pode recuperar metadados de serviço usando o WS-MetadataExchange ou HTTP/GET solicitações usando a ferramenta Svcutil.exe e passando o **/target:metadata** comutador e um endereço. Svcutil.exe baixa os metadados no endereço especificado e salva os arquivos no disco. Svcutil.exe usa um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância internamente e carrega uma configuração de ponto de extremidade MEX (a partir do arquivo de configuração de aplicativo) cujo nome corresponda ao esquema do endereço passada para Svcutil.exe, se um existe. Caso contrário, o Svcutil.exe padronizado para usar uma das associações definidas pelo <xref:System.ServiceModel.Description.MetadataExchangeBindings> tipo de fábrica estáticos.  
  
## <a name="importing-service-metadata"></a>Importação de metadados de serviço  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], importação de metadados é o processo de geração de uma representação abstrata de um serviço ou seus componentes de seus metadados. Por exemplo, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode importar <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias, <xref:System.ServiceModel.Channels.Binding> instâncias ou <xref:System.ServiceModel.Description.ContractDescription> instâncias de um WSDL documentos para um serviço. Para importar os metadados de serviço em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], use uma implementação do <xref:System.ServiceModel.Description.MetadataImporter> classe abstrata. Tipos que derivam de <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> classe implementa o suporte para formatos de metadados de importação que aproveitam o WS-Policy importar lógica em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Um <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> implementação coleta as expressões de política anexadas aos metadados do serviço em um <xref:System.ServiceModel.Description.PolicyConversionContext> objeto. O <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> , em seguida, processa as diretivas como parte da importação de metadados chamando as implementações do <xref:System.ServiceModel.Description.IPolicyImportExtension> interface o <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> propriedade.  
  
 Você pode adicionar suporte para importar novo declarações de política para um <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> adicionando sua própria implementação do <xref:System.ServiceModel.Description.IPolicyImportExtension> interface para o <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> coleção em uma <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> instância. Como alternativa, você pode registrar a sua extensão de importação de política no arquivo de configuração do aplicativo cliente.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> acompanha de classe abstrata [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo importa os metadados WSDL anexado políticas que são empacotadas em um <xref:System.ServiceModel.Description.MetadataSet> objeto.  
  
 Você pode adicionar suporte para a importação de extensões WSDL Implementando o <xref:System.ServiceModel.Description.IWsdlImportExtension> interface e, em seguida, adicionar a implementação para o <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> propriedade em seu <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> instância. O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> também pode carregar implementações do <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface registrada no arquivo de configuração do aplicativo cliente.  
  
## <a name="dynamic-bindings"></a>Associações dinâmicas  
 Você pode atualizar dinamicamente a associação que você usa para criar um canal para um ponto de extremidade de serviço, que altera a associação para o ponto de extremidade ou para criar um canal para um ponto de extremidade que usa o mesmo contrato, mas tem uma associação diferente. Você pode usar o <xref:System.ServiceModel.Description.MetadataResolver> classe estática para recuperar e importar metadados em tempo de execução para pontos de extremidade de serviço que implementa um contrato específico. Você pode usar o importados <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> objetos para criar uma fábrica de canal ou de cliente para o ponto de extremidade desejado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description>  
 [Formatos de metadados](../../../../docs/framework/wcf/feature-details/metadata-formats.md)  
 [Exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Recuperando metadados](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)  
 [Uso de metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
