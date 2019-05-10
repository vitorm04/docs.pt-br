---
title: Usando associações para configurar serviços e clientes
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 0f01fefc46cbc2cddaef9b025d59db8e2f734d9f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645134"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Usando associações para configurar serviços e clientes
Associações são objetos que especificam os detalhes de comunicação necessários para se conectar a um ponto de extremidade. Mais especificamente, as associações contêm informações de configuração que são usadas para criar o tempo de execução do cliente ou serviço, definindo as especificidades de transportes, formatos de transmissão (codificação de mensagens) e de protocolo para o canal de cliente ou de ponto de extremidade do respectivo. Para criar um serviço Windows Communication Foundation (WCF) ativo, cada ponto de extremidade no serviço requer uma associação. Este tópico explica o que são associações, como elas são definidas e como uma ligação específica é especificada para um ponto de extremidade.  
  
## <a name="what-a-binding-defines"></a>O que define uma associação  
 As informações em uma associação podem ser muito básico ou muito complexos. A associação mais básica especifica somente o protocolo de transporte (como HTTP) que deve ser usado para se conectar ao ponto de extremidade. De modo geral, as informações de que uma associação contém sobre como se conectar a um ponto de extremidade se enquadra em uma das categorias na tabela a seguir.  
  
 Protocolos  
 Determina o mecanismo de segurança que está sendo usado, o recurso de mensagens confiável ou configurações de fluxo do contexto de transação.  
  
 Transporte  
 Determina o protocolo de transporte subjacente usada (por exemplo, TCP ou HTTP).  
  
 Codificando  
 Determina a codificação de mensagem, por exemplo, text/XML, binário ou mensagem MTOM Transmission Optimization Mechanism (), que determina como as mensagens são representadas como fluxos de bytes durante a transmissão.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 O WCF inclui um conjunto de associações fornecidas pelo sistema que são projetados para abranger a maioria dos cenários e requisitos do aplicativo. As classes a seguir representam alguns exemplos das associações fornecidas pelo sistema:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: Um protocolo HTTP adequado para se conectar a serviços Web de associação que está em conformidade com o WS-I Basic Profile 1.1 especificação (por exemplo, os serviços de Web do ASP.NET [ASMX]-com base em serviços).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Protocolos de especificações de serviços de um protocolo HTTP associação adequada para se conectar a pontos de extremidade que estão em conformidade com a Web.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Usa o binário do .NET, codificação e de delimitação de quadros tecnologias em conjunto com o Windows chamado transporte de pipe para se conectar a outros pontos de extremidade do WCF no mesmo computador.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Usa o binário do .NET, codificação e as tecnologias em conjunto com o enfileiramento de mensagens (também conhecido como MSMQ) de delimitação de quadros para criar conexões de mensagem na fila com outros pontos de extremidade do WCF.  
  
 Para obter uma lista completa das associações fornecidas pelo sistema, com descrições, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Se a coleção de associação fornecida pelo sistema não tiver a combinação correta de recursos necessários para um aplicativo de serviço, você pode criar um <xref:System.ServiceModel.Channels.CustomBinding> associação. Para obter mais informações sobre os elementos de uma <xref:System.ServiceModel.Channels.CustomBinding> associação, consulte [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e [ligações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Usando associações  
 Usando associações envolve duas etapas básicas:  
  
1. Selecione ou defina uma associação. É o método mais fácil escolher uma das associações fornecidas pelo sistema e usar as configurações padrão. Também pode escolher uma associação fornecida pelo sistema e de redefinição de seus valores de propriedade para atender às suas necessidades. Como alternativa, você pode criar uma ligação personalizada e definir todas as propriedades conforme necessário.  
  
2. Crie um ponto de extremidade que usa essa associação.  
  
## <a name="code-and-configuration"></a>Configuração e código  
 Você pode definir ou configurar as associações por meio de código ou na configuração. Essas duas abordagens são independentes do tipo de associação usado, por exemplo, se você estiver usando um fornecido pelo sistema ou uma <xref:System.ServiceModel.Channels.CustomBinding> associação. Em geral, usando código lhe dá controle total sobre a definição de uma associação ao compilar. Por outro lado, usando a configuração, permite que um administrador do sistema ou o usuário de um serviço WCF ou o cliente para alterar os parâmetros de associações. Essa flexibilidade geralmente é desejável porque não há nenhuma maneira de prever os requisitos de máquina específica e as condições em que um aplicativo WCF deve ser implantada da rede. Separar as informações de associação (e endereçamento) do código permite que os administradores alterem os detalhes de associação sem ter que recompilar ou reimplantar o aplicativo. Observe que, se a associação é definida no código, ele substitui quaisquer definições de configuração feitas no arquivo de configuração. Para obter exemplos dessas abordagens, consulte os tópicos a seguir:  
  
- [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) fornece um exemplo de como criar uma associação no código.  
  
- [Tutorial: Criar um cliente do Windows Communication Foundation](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) fornece um exemplo de criação de um cliente por meio da configuração.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Como: Especificar uma associação de serviço no código](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [Como: Especificar uma associação de cliente na configuração](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [Como: Especificar uma associação de cliente no código](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
