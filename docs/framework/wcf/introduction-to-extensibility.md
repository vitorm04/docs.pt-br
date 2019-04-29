---
title: Introdução à extensibilidade
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 8d7b9c811c557b10160c2581a59f5ebf72882bfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928568"
---
# <a name="introduction-to-extensibility"></a>Introdução à extensibilidade
O modelo de aplicativo do Windows Communication Foundation (WCF) foi projetado para resolver a maior parte dos requisitos de comunicação de qualquer aplicativo distribuído. Mas sempre há cenários que não são compatíveis com o modelo de aplicativo padrão e implementações fornecida pelo sistema. O modelo de extensibilidade do WCF destina-se para dar suporte a cenários personalizados, permitindo que você modificar o comportamento do sistema em todos os níveis, até mesmo para o ponto de substituir o modelo de aplicativo inteiro. Este tópico descreve várias áreas de extensão e aponta para obter mais informações sobre cada um.  
  
## <a name="areas-to-extend"></a>Áreas para estender  
 Você pode estender:  
  
- O tempo de execução do aplicativo. Isso estende a distribuição e o processamento de mensagens para o aplicativo. Essa área também inclui estendendo o sistema de segurança, o sistema de metadados, o sistema de serialização e as associações e elementos de associação que conecta o aplicativo com o sistema de canal subjacente.  
  
- O canal e o tempo de execução do canal. Isso estende o sistema que funciona no nível da mensagem, fornecendo o protocolo de transporte e suporte a codificação.  
  
- O tempo de execução do host. Isso estende a relação do domínio do aplicativo de hospedagem para o tempo de execução do aplicativo e de canal.  
  
### <a name="extending-the-application-runtime"></a>Estendendo o tempo de execução do aplicativo  
 Em aplicativos do WCF, há uma distinção entre as mensagens que são destinadas a um canal correspondente e as mensagens que são destinadas para o aplicativo em si. Mensagens do canal de suportam a algumas funcionalidades relacionadas ao canal, como estabelecer uma conversa segura ou estabelecer uma sessão confiável. Essas mensagens não estão disponíveis para o tempo de execução do aplicativo; eles são processados antes que a camada de aplicativo está envolvida.  
  
 Mensagens de aplicativo contêm dados que são destinados a um cliente ou operação de serviço que você ou seu cliente tiver sido criado. Essas mensagens estão disponíveis para o sistema de extensão de nível de aplicativo no formato de mensagem ou objeto, dependendo das suas necessidades.  
  
 Todas as mensagens passam pelo sistema canal; apenas as mensagens de aplicativo são passadas do sistema de canal para o aplicativo. Para criar a nova funcionalidade de nível de canal, você deve estender o sistema de canal. Para criar a nova funcionalidade de nível de aplicativo, você deve estender o tempo de execução do serviço ou cliente (dispatchers e fábricas de canais, respectivamente). Para obter mais informações sobre como estender o tempo de execução do aplicativo, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Segurança estendida  
 Para criar mecanismos de segurança personalizada, como tokens e credenciais, você deve estender o sistema de segurança. Para obter mais informações, consulte [estendendo segurança](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Estendendo metadados  
 Para expor seus metadados na forma diferente do padrão, você deve estender o sistema de metadados. Para obter mais informações, consulte [estendendo o sistema de metadados](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Estendendo a serialização  
 Para criar codificadores personalizados, fornecer substitutos de dados ou outro trabalho que envolve a personalização dos dados transferidos, você deve estender o sistema de serialização. Para obter mais informações, consulte [estendendo codificadores e serializadores](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Estendendo associações  
 Para associar os canais de transporte ou protocolo de camada de aplicativo, você deve estender o sistema de associação. Para obter mais informações, consulte [estendendo associações](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Estendendo o sistema de canal  
 Para criar canais que dão suporte a transportes personalizados ou funcionalidade de protocolo, consulte [estendendo a camada do canal](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Estendendo o sistema de hospedagem de serviço  
 Para modificar o modelo de todo o serviço de aplicativo, você deve estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> classe. Para obter mais informações, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Para modificar a relação entre o domínio de aplicativo de hospedagem e o host de serviço, você deve estender o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classe. Para obter mais informações, consulte [estendendo hospedagem usando ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Consulte também

- [Estendendo o WCF](../../../docs/framework/wcf/extending/index.md)
