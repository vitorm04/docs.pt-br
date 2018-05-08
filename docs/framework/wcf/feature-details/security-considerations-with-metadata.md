---
title: Considerações de segurança com metadados
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b8028b27e721e19a5fc01887e4095218d0e14436
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-considerations-with-metadata"></a>Considerações de segurança com metadados
Ao usar os recursos de metadados no Windows Communication Foundation (WCF), considere as implicações de segurança de publicação, recuperar e usando metadados de serviço.  
  
## <a name="when-to-publish-metadata"></a>Quando publicar metadados  
 Serviços WCF não publicar metadados por padrão. Para publicar metadados para um serviço WCF você deve habilitar explicitamente publicação de metadados com a adição de pontos de extremidade de metadados para o serviço (consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Publicação de metadados desabilitada reduz a superfície de ataque para o serviço e reduz o risco de divulgação de informações não intencionais. Nem todos os serviços devem publicar metadados. Se você não precisa publicar metadados, considere deixá-la desativado. Observe que você ainda pode gerar o código de cliente e metadados diretamente de seus conjuntos de serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Para obter mais informações sobre como usar o Svcutil.exe para exportar metadados, consulte [como: usar a Svcutil.exe para exportar metadados de código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Metadados de publicação usando uma associação de segurança  
 As associações de metadados padrão que o WCF fornece não são seguras e permitir o acesso anônimo aos metadados. Os metadados de serviço que um serviço WCF publica contém uma descrição detalhada sobre o serviço e podem intencionalmente ou não conter informações confidenciais. Por exemplo, os metadados de serviço podem conter informações sobre as operações de infra-estrutura que não foi desenvolvidas para ser transmitida publicamente. Para proteger os metadados de serviço contra acesso não autorizado, você pode usar uma associação de segurança para seu ponto de extremidade de metadados. Pontos de extremidade de metadados respondem a solicitações HTTP/GET que podem usar o SSL Secure Sockets Layer () para proteger os metadados. Para obter mais informações, consulte [como: proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Proteger os pontos de extremidade de metadados também fornece uma maneira para que os solicitantes de recuperar metadados de serviço sem o risco de falsificação ou violação.  
  
## <a name="using-only-trusted-metadata"></a>Usando somente confiáveis metadados  
 Você pode usar os metadados de serviço para construir automaticamente os componentes de tempo de execução necessários para chamar o serviço. Você também pode usar metadados em tempo de design para desenvolver um aplicativo cliente ou em tempo de execução para atualizar dinamicamente a associação de um cliente usa para chamar um serviço.  
  
 Metadados de serviço podem ser violados ou falsificados quando recuperados de uma maneira segura. Metadados violado podem redirecionar o cliente para um serviço mal-intencionado, contêm configurações de segurança comprometido ou conter mal-intencionado estruturas XML. Documentos de metadados podem ser grandes e frequentemente são salvos no sistema de arquivos. Para proteger contra violações e falsificações, use uma associação de segurança para solicitar metadados de serviço quando houver uma disponível.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Usando técnicas de seguras para o processamento de metadados  
 Metadados de serviço com frequência são recuperados de um serviço em uma rede usando protocolos padronizados, como WS-MetadataExchange (MEX). Vários formatos de metadados incluem mecanismos para apontar para metadados adicionais de referência. O <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo processa automaticamente as referências para você em documentos WSDL Web Services Description Language (), o esquema XML e documentos MEX. O tamanho do <xref:System.ServiceModel.Description.MetadataSet> objeto criado a partir de metadados recuperados é diretamente proporcional ao <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> valor para o <xref:System.ServiceModel.Description.MetadataExchangeClient> instância é usada e o `MaxReceivedMessageSize` valor para a associação está sendo usada por que <xref:System.ServiceModel.Description.MetadataExchangeClient> instância. Defina essas cotas para os valores apropriados, conforme determinado pelo seu cenário.  
  
 No WCF, os metadados de serviço é processado como XML. Durante o processamento de documentos XML, aplicativos devem se proteger contra mal-intencionado estruturas XML. Use o `XmlDictionaryReader` com apropriado cotas durante o processamento de XML e também definir o <xref:System.Xml.XmlTextReader.DtdProcessing%2A> propriedade `Prohibit`.  
  
 O sistema de metadados no WCF é extensível e as extensões de metadados podem ser registradas em seu arquivo de configuração do aplicativo (consulte [estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Extensões de metadados podem executar um código arbitrário, para que você deve proteger seu arquivo de configuração do aplicativo com o controle de acesso apropriadas de ACLs e registrar apenas os metadados confiável implementações de extensão.  
  
## <a name="validating-generated-clients"></a>Validando clientes gerados  
 Ao gerar o código do cliente de metadados recuperados de uma fonte que não é confiável, valide o código de cliente gerada para garantir que o cliente gerado está em conformidade com as políticas de segurança de aplicativos cliente. Você pode usar um comportamento de validação para verificar as configurações no seu cliente de associação ou inspecionar visualmente o código gerado por ferramentas. Para obter um exemplo de como implementar um cliente que valida os comportamentos, consulte [validação do cliente](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Protegendo arquivos de configuração do aplicativo  
 Arquivo de configuração de aplicativo do serviço pode controlar como e se os metadados são publicados. É uma boa ideia para proteger o arquivo de configuração do aplicativo com listas de controle de acesso adequadas (ACLs) para garantir que o invasor não pode modificar essas configurações.  
  
## <a name="see-also"></a>Consulte também  
 [Como proteger pontos de extremidade de metadados](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
