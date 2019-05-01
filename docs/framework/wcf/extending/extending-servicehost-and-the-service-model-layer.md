---
title: Estendendo a camada de modelo de serviço e o ServiceHost
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991764"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Estendendo a camada de modelo de serviço e o ServiceHost
A camada de modelo de serviço é responsável por efetuar pull de mensagens recebidas fora de canais subjacentes, convertendo-os em invocações de método no código do aplicativo e enviar os resultados para o chamador. Extensões do modelo de serviço modificarem ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de cliente ou dispatcher, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do cliente, bem como as classes nas quais você pode inserir suas extensões personalizadas em aplicativos cliente. Por exemplo, executar o log de mensagem do cliente personalizado, executar a serialização de mensagens personalizadas e assim por diante.  
  
 [Estendendo dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do serviço, bem como as classes nas quais você pode inserir suas extensões personalizadas em aplicativos de serviço. Por exemplo, você pode executar o registro em log do serviço personalizado, a validação de mensagem do lado do serviço, expedição personalizados e assim por diante.  
  
 [Objetos extensíveis](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Descreve os cinco objetos extensíveis e o <xref:System.ServiceModel.IExtensibleObject%601> padrão. O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar o novo estado a um objeto. Extensões, anexadas a um dos objetos extensíveis, habilitar comportamentos em muito diferentes estágios de processamento para acessar o estado compartilhado e a funcionalidade anexada a um objeto extensível comum que eles podem acessar.  
  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Para alterar as configurações no ou inserir extensões em tempo de execução WCF, você deve usar comportamentos. O WCF inclui comportamentos implementado pelo sistema para controlar a limitação de instanciação e muitos outros aspectos dos serviços e operações. Esta seção descreve como criar seus próprios comportamentos personalizados e como torná-los disponíveis tanto por meio de programação e usando arquivos de configuração.  
  
 [Estendendo a hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Descreve como estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>e usar o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes para personalizar o ambiente de host.  
  
## <a name="reference"></a>Referência  
  
## <a name="related-sections"></a>Seções relacionadas
