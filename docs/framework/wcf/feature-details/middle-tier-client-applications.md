---
title: Aplicativos cliente de camada intermediária
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 1b1ba177c365bb6913679ed2a217e66d7a0d522b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877465"
---
# <a name="middle-tier-client-applications"></a>Aplicativos cliente de camada intermediária
Este tópico aborda diversos problemas específicos de aplicativos de cliente de camada intermediária que usam o Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Aumentando o desempenho do cliente de camada intermediária  
 Em comparação com as tecnologias de comunicações anteriores, como serviços Web usando ASP.NET, a criação de uma instância do cliente WCF pode ser mais complexa devido aos avançado conjunto de recursos do WCF. Por exemplo, quando um <xref:System.ServiceModel.ChannelFactory%601> objeto é aberto. ele pode estabelecer uma sessão segura com o serviço, um procedimento que aumenta o tempo de inicialização para a instância do cliente. Normalmente, esses recursos adicionais não afetam aplicativos cliente significativamente desde que o cliente WCF faz várias chamadas e, em seguida, fecha.  
  
 Aplicativos cliente de camada intermediária, no entanto, podem criar muitos objetos de cliente WCF rapidamente e, como resultado, a experiência de requisitos de inicialização maior. Há duas abordagens principais para aumentar o desempenho dos aplicativos de camada intermediária, ao chamar serviços:  
  
- Armazenar em cache o objeto de cliente WCF e reutilizá-lo nas próximas chamadas sempre que possível.  
  
- Criar um <xref:System.ServiceModel.ChannelFactory%601> de objeto e, em seguida, usar esse objeto para criar objetos de canal para cada chamada de novo cliente do WCF.  
  
 Questões a serem consideradas ao usar esses métodos incluem:  
  
- Se o serviço mantém um estado específico do cliente por meio de uma sessão, é possível reutilizar o cliente do WCF de camada intermediária com solicitações de cliente de várias camadas porque o estado do serviço está ligado do cliente de camada intermediária.  
  
- Se o serviço deve executar a autenticação em uma base por cliente, você deve criar um novo cliente para cada solicitação de entrada na camada intermediária em vez de reutilizar o cliente do WCF de camada intermediária (ou o objeto de canal de cliente do WCF), porque as credenciais do cliente de camada intermediária não pode ser modificado depois que o cliente do WCF (ou <xref:System.ServiceModel.ChannelFactory%601>) foi criado.  
  
- Enquanto os clientes criados pelos canais e canais são thread-safe, eles podem não dar suporte a gravação de mais de uma mensagem para a transmissão simultaneamente. Se você estiver enviando mensagens grandes, especialmente se o streaming, a operação de envio pode bloquear a espera para outro enviar concluir. Isso faz com que dois tipos de problemas: uma falta de simultaneidade e a possibilidade de deadlock se o fluxo de controle retorna para o serviço reutilizando o canal (ou seja, o cliente compartilhado chama um serviço cujos resultados de caminho de código em um retorno de chamada para o cliente compartilhado). Isso é verdadeiro independentemente do tipo de cliente do WCF que é reutilizar.  
  
- Você deve tratar os canais com falha, independentemente se você compartilhar o canal. Quando são reutilizados e canais, no entanto, um canal com falha pode levar mais de uma solicitação pendente ou enviar.  
  
 Para obter um exemplo que demonstra as práticas recomendadas para reutilização de um cliente para várias solicitações, consulte [vinculação de dados em um cliente do ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Além disso, você pode aumentar o desempenho de inicialização para os clientes que usam tipos de dados que são serializados usando o <xref:System.Xml.Serialization.XmlSerializer> gerar e compilar o código de serialização para esses tipos de dados em tempo de execução, o que pode resultar em desempenho de inicialização lento. O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos, gerando o código de serialização necessários a partir de assemblies compilados para o aplicativo. Para obter mais informações, confira [Como: Melhorar o tempo de inicialização do WCF cliente aplicativos usando o XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Consulte também

- [Usando um cliente do WCF para acessar serviços](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
