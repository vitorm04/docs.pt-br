---
title: "Aplicativos cliente de camada intermediária"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 893fa027d2f1eb4fa3782b9119f6ae2d4a78d700
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="middle-tier-client-applications"></a>Aplicativos cliente de camada intermediária
Este tópico descreve diversos problemas específicos de aplicativos de cliente de camada intermediária que usam [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="increasing-middle-tier-client-performance"></a>Aumentando o desempenho do cliente de camada intermediária  
 Em comparação com as tecnologias de comunicações anteriores, como serviços Web usando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], a criação de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] instância de cliente pode ser mais complexa devido ao conjunto completo de recursos de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Por exemplo, quando um <xref:System.ServiceModel.ChannelFactory%601> objeto é aberto possa estabelecer uma sessão segura com o serviço, um procedimento que aumenta o tempo de inicialização para a instância do cliente. Normalmente, esses recursos adicionais não afeta os aplicativos cliente significativamente desde o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faz várias chamadas de cliente e, em seguida, fecha.  
  
 Aplicativos cliente de camada intermediária, no entanto, podem criar muitas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objetos cliente rapidamente e, como resultado, experiência requisitos de aumento de inicialização. Há duas abordagens principais para aumentar o desempenho de aplicativos de camada intermediária quando a chamada de serviços:  
  
-   Cache de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de objeto e reutilizá-lo para as chamadas subsequentes, sempre que possível.  
  
-   Criar um <xref:System.ServiceModel.ChannelFactory%601> de objeto e, em seguida, usar esse objeto para criar novos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objetos de canal do cliente para cada chamada.  
  
 Questões a serem consideradas ao usar esses métodos incluem:  
  
-   Se o serviço mantém um estado específico do cliente por meio de uma sessão, não é possível reutilizar a camada intermediária [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solicitações de cliente com nível de vários clientes porque o estado do serviço estiver associado a que o cliente de camada intermediária.  
  
-   Se o serviço deve executar a autenticação em uma base por cliente, você deve criar um novo cliente para cada solicitação de entrada na camada intermediária em vez de reutilizá camada intermediária [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente (ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objeto do canal do cliente) porque o cliente credenciais da camada intermediária não podem ser modificadas após o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente (ou <xref:System.ServiceModel.ChannelFactory%601>) foi criado.  
  
-   Enquanto o cliente criado pelos canais e canais é thread-safe, eles podem não suportar mais de uma mensagem de gravação para a transmissão simultaneamente. Se você estiver enviando mensagens grandes, particularmente se streaming, a operação de envio poderão bloquear aguardando outro enviar concluir. Isso faz com que dois tipos de problemas: falta de simultaneidade e a possibilidade de deadlock se o fluxo de controle retorna para o serviço reutilizando o canal (ou seja, o cliente compartilhado chama um serviço cujos resultados de caminho de código em um retorno de chamada para o cliente compartilhado). Isso é verdadeiro independentemente do tipo de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente você reutilizar.  
  
-   Você deve tratar os canais com defeito, independentemente de se você compartilhar o canal. Quando são reutilizados e canais, no entanto, um canal com falha pode desativar a mais de uma solicitação pendente ou enviar.  
  
 Para obter um exemplo que demonstra práticas recomendadas para reutilização de um cliente para várias solicitações, consulte [associação de dados em um cliente do ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Além disso, você pode aumentar o desempenho de inicialização para os clientes que usam tipos de dados pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer> gerar e compilar o código de serialização para esses tipos de dados em tempo de execução, o que pode resultar em desempenho de inicialização lenta. O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos por meio da geração de código de serialização necessários dos assemblies compilados para o aplicativo. Para obter mais informações, consulte [como: melhorar a inicialização do tempo de WCF aplicativos cliente que usam o XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Accessing Services Using a WCF Client](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) (Usando um cliente do WCF para acessar serviços)
