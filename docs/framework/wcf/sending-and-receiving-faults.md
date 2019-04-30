---
title: Enviando e recebendo falhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 2757f98066931ca1b5e3ef147cee2c819ee22606
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949598"
---
# <a name="sending-and-receiving-faults"></a>Enviando e recebendo falhas
Falhas de SOAP transmitem condição informações de erro de um serviço em um cliente e no caso de duplex de um cliente a um serviço de uma maneira interoperável. Normalmente, um serviço define o conteúdo de falha personalizado e especifica quais operações poderá retorná-los. (Para obter mais informações, consulte [definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Este tópico discute como um serviço ou cliente duplex pode enviar essas falhas quando a condição de erro correspondente e como um cliente ou aplicativo de serviço lida com essas falhas. Para obter uma visão geral de tratamento de erros em aplicativos do Windows Communication Foundation (WCF), consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Envio de falhas de SOAP  
 Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> que especifica um tipo personalizado de falhas SOAP. Falhas SOAP não declaradas são aqueles que não são especificados no contrato para uma operação.  
  
### <a name="sending-declared-faults"></a>Enviar falhas declaradas  
 Para enviar uma falha SOAP declarada, detectar a condição de erro para o qual a falha de SOAP é apropriada e lançar uma nova <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> onde o parâmetro de tipo é um novo objeto do tipo especificado no <xref:System.ServiceModel.FaultContractAttribute> para essa operação. O exemplo de código a seguir mostra o uso de <xref:System.ServiceModel.FaultContractAttribute> para especificar que o `SampleMethod` operação pode retornar uma falha SOAP com o tipo de detalhe de `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 Para transmitir o `GreetingFault` informações de erro para o cliente, capturar a condição de erro apropriado e gerar um novo <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> do tipo `GreetingFault` com um novo `GreetingFault` objeto como argumento, como no exemplo de código a seguir. Se o cliente é um aplicativo de cliente do WCF, ele passa por isso como uma exceção gerenciada em que o tipo é <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> do tipo `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Envio de falhas não declaradas  
 Envio de falhas não declaradas podem ser muito útil para diagnosticar e depurar problemas em aplicativos do WCF, mas sua utilidade, pois uma ferramenta de depuração é limitada rapidamente. De modo geral, quando depurá-lo é recomendável que você use o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade. Quando você definir esse valor como true, os clientes enfrentar tais falhas como <xref:System.ServiceModel.FaultException%601> exceções do tipo <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Pois exceções gerenciadas podem expor informações de aplicativo interno, definindo <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` pode permitir que clientes do WCF para obter informações sobre exceções de operação de serviço interno, incluindo pessoal ou de identificação de informações confidenciais.  
>   
>  Portanto, definir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` só é recomendado como uma forma de depuração temporariamente um aplicativo de serviço. Além disso, o WSDL para um método que retorna sem tratamento gerenciadas exceções dessa maneira não contém o contrato para o <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes devem esperar a possibilidade de uma falha SOAP desconhecida (retornadas aos clientes do WCF como <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objetos) para obter as informações de depuração corretamente.  
  
 Para enviar uma falha SOAP não declarada, lançar uma <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objeto (ou seja, não o tipo genérico <xref:System.ServiceModel.FaultException%601>) e passe a cadeia de caracteres para o construtor. Isso é exposto para os aplicativos de cliente do WCF como um lançada <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> exceção onde a cadeia de caracteres está disponível por meio da chamada a <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> método.  
  
> [!NOTE]
>  Se você declarar uma falha SOAP do tipo cadeia de caracteres e, em seguida, acionar isso em seu serviço como um <xref:System.ServiceModel.FaultException%601> onde o parâmetro de tipo é um <xref:System.String?displayProperty=nameWithType> o valor de cadeia de caracteres é atribuído para o <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> propriedade e não está disponível em <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Tratamento de falhas  
 Em clientes do WCF, falhas SOAP que ocorrem durante a comunicação que são de interesse para os aplicativos cliente são geradas como exceções gerenciadas. Embora existam muitas exceções que podem ocorrer durante a execução de qualquer programa, aplicativos que usam o modelo de programação de cliente do WCF podem esperar tratar exceções de dois tipos a seguir como resultado da comunicação.  
  
- <xref:System.TimeoutException>  
  
- <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> objetos são gerados quando uma operação excede o período de tempo limite especificado.  
  
 <xref:System.ServiceModel.CommunicationException> objetos são gerados quando há alguma condição de erro de comunicação recuperáveis no serviço ou no cliente.  
  
 O <xref:System.ServiceModel.CommunicationException> classe tem dois tipos derivados importantes <xref:System.ServiceModel.FaultException> e o genérico <xref:System.ServiceModel.FaultException%601> tipo.  
  
 <xref:System.ServiceModel.FaultException> as exceções são geradas quando um ouvinte recebe uma falha que não é esperada ou especificada no contrato de operação; Normalmente, isso ocorre quando o aplicativo está sendo depurado e o serviço tem o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade definida como `true`.  
  
 <xref:System.ServiceModel.FaultException%601> exceções são geradas no cliente quando uma falha que é especificada no contrato de operação é recebida em resposta a uma operação bidirecional (ou seja, um método com um <xref:System.ServiceModel.OperationContractAttribute> do atributo com <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> definido como `false`).  
  
> [!NOTE]
>  Quando um serviço WCF tem o <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade definida como `true` o cliente apresenta isso como um não declarada <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes podem capturar essa falha específica ou tratar a falha em um bloco catch para <xref:System.ServiceModel.FaultException>.  
  
 Normalmente, apenas <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, e <xref:System.ServiceModel.CommunicationException> exceções são de interesse para os clientes e serviços.  
  
> [!NOTE]
>  Outras exceções, é claro, ocorrer. Exceções inesperadas incluem falhas catastróficas como <xref:System.OutOfMemoryException?displayProperty=nameWithType>; normalmente aplicativos não devem capturar esses métodos.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Capturar exceções de falha na ordem correta  
 Porque <xref:System.ServiceModel.FaultException%601> deriva <xref:System.ServiceModel.FaultException>, e <xref:System.ServiceModel.FaultException> deriva <xref:System.ServiceModel.CommunicationException>, é importante capturar essas exceções na ordem correta. Se, por exemplo, você tiver um try/catch bloco no qual você primeiro catch <xref:System.ServiceModel.CommunicationException>, todos especificados e não especificado de falhas de SOAP são manipuladas há; todos os blocos catch subsequentes para lidar com um personalizado <xref:System.ServiceModel.FaultException%601> exceção nunca sejam invocados.  
  
 Lembre-se de que uma única operação pode retornar qualquer número de falhas especificados. É um tipo exclusivo de cada falha e deve ser tratada separadamente.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Tratar exceções ao fechar o canal  
 A maioria da discussão anterior tem a ver com falhas enviadas no decorrer de processamento de mensagens do aplicativo, ou seja, as mensagens enviadas explicitamente pelo cliente quando o aplicativo cliente chama operações no objeto de cliente do WCF.  
  
 Mesmo com objetos locais descarte o objeto pode elevar ou mascarar exceções que ocorrem durante o processo de reciclagem. Algo semelhante pode ocorrer quando você usa objetos de cliente do WCF. Quando você chama operações você está enviando mensagens ao longo de uma conexão estabelecida. Fechando o canal pode gerar exceções se a conexão não pode ser fechada corretamente ou se já estiver fechado, mesmo se todas as operações retornadas corretamente.  
  
 Normalmente, os canais de objeto do cliente são fechados em uma das seguintes maneiras:  
  
- Quando o objeto de cliente do WCF é reciclado.  
  
- Quando o aplicativo cliente chama <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
- Quando o aplicativo cliente chama <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
- Quando o aplicativo cliente chama uma operação que é uma operação de encerramento de uma sessão.  
  
 Todos os casos, fechando o canal instrui o canal para comece fechando quaisquer canais subjacentes que podem estar enviando mensagens para dar suporte a funcionalidades complexas no nível do aplicativo. Por exemplo, quando um contrato requer sessões uma associação tenta estabelecer uma sessão por meio da troca mensagens com o canal de serviço até que uma sessão é estabelecida. Quando o canal está fechado, o canal de sessão subjacente notifica o serviço que a sessão seja encerrada. Nesse caso, se o canal já foi anulada, fechado, ou caso contrário, será inutilizável (por exemplo, quando um cabo de rede está desconectado), o canal do cliente não pode informar o canal de serviço que a sessão é encerrada e uma exceção pode ocorrer.  
  
### <a name="abort-the-channel-if-necessary"></a>Anular o canal, se necessário  
 Porque fechando o canal também pode lançar exceções, em seguida, é recomendável que, além de capturar exceções de falha na ordem correta, é importante anular o canal que foi usado para fazer a chamada em um bloco catch.  
  
 Se a falha transmite informações de erro específicas a uma operação e continua sendo possível que outras pessoas possam usá-lo, não é necessário para anular o canal (embora esses casos são raros). Em todos os outros casos, é recomendável que você anular o canal. Para obter um exemplo que demonstra todos esses pontos, consulte [esperado exceções](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 O exemplo de código a seguir mostra como tratar exceções de falha SOAP em um aplicativo cliente básico, incluindo uma falha de declarado e uma falha não declarada.  
  
> [!NOTE]
>  Esse código de exemplo não usa o `using` construir. Como fechar canais pode lançar exceções, é recomendável que os aplicativos criam um primeiro e, em seguida, abrir, uso de cliente do WCF e fechar o cliente WCF no mesmo bloco try. Para obter detalhes, consulte [visão geral do cliente WCF](../../../docs/framework/wcf/wcf-client-overview.md) e [uso Close e Abort para liberar os recursos de cliente do WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Exceções esperadas](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [Use fechar e anular para liberar recursos de cliente do WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
