---
title: Considerações de segurança com metadados
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
author: BrucePerlerMS
ms.openlocfilehash: 1469e5b48fbbdcbb289e4ca3147145688e1669f4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082410"
---
# <a name="security-considerations-with-metadata"></a>Considerações de segurança com metadados
Ao usar os recursos de metadados no Windows Communication Foundation (WCF), considere as implicações de segurança de publicação, recuperar e usar metadados do serviço.  
  
## <a name="when-to-publish-metadata"></a>Quando publicar metadados  
 Os serviços WCF não publique metadados por padrão. Para publicar metadados para um serviço WCF você deve habilitar explicitamente publicação de metadados com a adição de pontos de extremidade de metadados para seu serviço (consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Deixando a publicação de metadados desabilitada reduz a superfície de ataque do seu serviço e reduz o risco de divulgação de informações não intencional. Nem todos os serviços devem publicar metadados. Se você não precisa publicar metadados, considere deixá-la desativado. Observe que você ainda pode gerar código de cliente e os metadados diretamente de seus assemblies de serviço usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Para obter mais informações sobre como usar Svcutil.exe para exportação de metadados, consulte [como: Use o Svcutil.exe para exportar metadados de código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publicação de metadados usando uma associação segura  
 As associações de metadados padrão que o WCF fornece não são seguras e eles permitem acesso anônimo aos metadados. Os metadados de serviço publica um serviço WCF contém uma descrição detalhada sobre o serviço e podem intencionalmente ou não conter informações confidenciais. Por exemplo, os metadados de serviço podem conter informações sobre operações de infraestrutura que não foi destinadas a ser difundida publicamente. Para proteger os metadados de serviço contra acesso não autorizado, você pode usar uma associação segura para seu ponto de extremidade de metadados. Pontos de extremidade de metadados respondem às solicitações HTTP/GET que podem usar a camada de soquetes segura (SSL) para proteger os metadados. Para obter mais informações, consulte [como: proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Também proteger os pontos de extremidade de metadados fornece uma maneira para os solicitantes recuperem com segurança os metadados de serviço sem o risco de falsificação ou violação.  
  
## <a name="using-only-trusted-metadata"></a>Usando somente confiáveis metadados  
 Você pode usar os metadados de serviço para construir automaticamente os componentes de tempo de execução necessários para chamar o serviço. Você também pode usar metadados em tempo de design para desenvolver um aplicativo cliente ou em tempo de execução para atualizar dinamicamente a associação de um cliente usa para chamar um serviço.  
  
 Metadados de serviço podem ser violados ou falsificados quando recuperados de uma maneira insegura. Metadados violados podem redirecionar o cliente para um serviço mal-intencionado, contêm configurações de segurança comprometido ou contêm estruturas XML de mal-intencionado. Documentos de metadados podem ser grandes e frequentemente são salvos no sistema de arquivos. Para proteger contra violações e falsificações, use uma associação segura para solicitar metadados de serviço quando houver uma disponível.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Usando técnicas de seguras para o processamento de metadados  
 Metadados de serviço com frequência é recuperado de um serviço em uma rede usando protocolos padronizados, como WS-MetadataExchange (MEX). Muitos formatos de metadados incluem referenciando mecanismos para apontando para metadados adicionais. O <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo processa automaticamente referências para você em documentos de descrição linguagem WSDL (Web Services), o esquema XML e documentos MEX. O tamanho do <xref:System.ServiceModel.Description.MetadataSet> objeto criado a partir de metadados recuperados é diretamente proporcional ao <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> valor para o <xref:System.ServiceModel.Description.MetadataExchangeClient> instância que é usada e o `MaxReceivedMessageSize` valor para a associação que está sendo usada pelo <xref:System.ServiceModel.Description.MetadataExchangeClient> instância. Defina essas cotas para os valores apropriados, conforme determinado pelo seu cenário.  
  
 No WCF, os metadados de serviço é processado como XML. Durante o processamento de documentos XML, aplicativos devem protegerem contra mal-intencionado estruturas XML. Use o `XmlDictionaryReader` por apropriados cotas durante o processamento de XML e também definir o <xref:System.Xml.XmlTextReader.DtdProcessing%2A> propriedade `Prohibit`.  
  
 O sistema de metadados no WCF é extensível e as extensões de metadados podem ser registradas em seu arquivo de configuração do aplicativo (consulte [estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Extensões de metadados podem executar código arbitrário, portanto, você deve proteger seu arquivo de configuração de aplicativo com o controle de acesso apropriado ACLs (listas) e registrar as implementações de extensão somente metadados confiável.  
  
## <a name="validating-generated-clients"></a>Validando clientes gerados  
 Ao gerar o código do cliente dos metadados recuperados de uma fonte que não é confiável, valide o código de cliente gerado para garantir que o cliente gerado está de acordo com suas políticas de segurança de aplicativos cliente. Você pode usar um comportamento de validação para verificar as configurações em sua associação de cliente ou inspecionar visualmente o código gerado por ferramentas. Para obter um exemplo de como implementar um cliente que valida os comportamentos, consulte [validação do cliente](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Protegendo arquivos de configuração de aplicativo  
 Arquivo de configuração de aplicativo do serviço pode controlar como e se os metadados são publicados. É uma boa ideia para proteger o arquivo de configuração de aplicativo com listas de controle de acesso apropriados (ACLs) para garantir que um invasor não pode modificar essas configurações.  
  
## <a name="see-also"></a>Consulte também  
 [Como proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
