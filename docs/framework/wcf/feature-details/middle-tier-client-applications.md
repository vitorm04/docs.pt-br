---
title: Aplicativos cliente de camada intermediária
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 4cca832266b2eb2ab7b1b4eb1a5fe937525db97d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="middle-tier-client-applications"></a>Aplicativos cliente de camada intermediária
Este tópico discute vários problemas específicos para aplicativos cliente de camada intermediária que usam o Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Aumentando o desempenho do cliente de camada intermediária  
 Em comparação com as tecnologias de comunicações anteriores, como serviços Web usando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], a criação de uma instância do cliente WCF pode ser mais complexa devido ao conjunto completo de recursos do WCF. Por exemplo, quando um <xref:System.ServiceModel.ChannelFactory%601> objeto é aberto possa estabelecer uma sessão segura com o serviço, um procedimento que aumenta o tempo de inicialização para a instância do cliente. Normalmente, esses recursos adicionais não afeta os aplicativos cliente significativamente desde que o cliente WCF faz várias chamadas e, em seguida, fecha.  
  
 Aplicativos cliente de camada intermediária, no entanto, podem criar muitos objetos de cliente do WCF rapidamente e, como resultado, a experiência de requisitos de aumento de inicialização. Há duas abordagens principais para aumentar o desempenho de aplicativos de camada intermediária quando a chamada de serviços:  
  
-   Armazenar em cache o objeto de cliente do WCF e reutilizá-lo para as chamadas subsequentes, sempre que possível.  
  
-   Criar um <xref:System.ServiceModel.ChannelFactory%601> de objeto e, em seguida, usar esse objeto para criar objetos de canal para cada chamada novo cliente do WCF.  
  
 Questões a serem consideradas ao usar esses métodos incluem:  
  
-   Se o serviço mantém um estado específico do cliente por meio de uma sessão, não é possível reutilizar o cliente do WCF de camada intermediária com solicitações de cliente de várias camadas porque o estado do serviço estiver associado a que o cliente de camada intermediária.  
  
-   Se o serviço deve executar a autenticação em uma base por cliente, você deve criar um novo cliente para cada solicitação de entrada na camada intermediária em vez de reutilizá o cliente do WCF de camada intermediária (ou o objeto do canal do cliente WCF), porque as credenciais do cliente de camada intermediária não pode ser modificado após o cliente do WCF (ou <xref:System.ServiceModel.ChannelFactory%601>) foi criado.  
  
-   Enquanto o cliente criado pelos canais e canais é thread-safe, eles podem não suportar mais de uma mensagem de gravação para a transmissão simultaneamente. Se você estiver enviando mensagens grandes, particularmente se streaming, a operação de envio poderão bloquear aguardando outro enviar concluir. Isso faz com que dois tipos de problemas: falta de simultaneidade e a possibilidade de deadlock se o fluxo de controle retorna para o serviço reutilizando o canal (ou seja, o cliente compartilhado chama um serviço cujos resultados de caminho de código em um retorno de chamada para o cliente compartilhado). Isso é verdadeiro independentemente do tipo de cliente do WCF que é reutilizar.  
  
-   Você deve tratar os canais com defeito, independentemente de se você compartilhar o canal. Quando são reutilizados e canais, no entanto, um canal com falha pode desativar a mais de uma solicitação pendente ou enviar.  
  
 Para obter um exemplo que demonstra práticas recomendadas para reutilização de um cliente para várias solicitações, consulte [associação de dados em um cliente do ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Além disso, você pode aumentar o desempenho de inicialização para os clientes que usam tipos de dados pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer> gerar e compilar o código de serialização para esses tipos de dados em tempo de execução, o que pode resultar em desempenho de inicialização lenta. O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos por meio da geração de código de serialização necessários dos assemblies compilados para o aplicativo. Para obter mais informações, consulte [como: melhorar a inicialização do tempo de WCF aplicativos cliente que usam o XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Usando um cliente do WCF para acessar serviços](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
