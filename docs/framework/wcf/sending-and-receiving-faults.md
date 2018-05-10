---
title: Enviando e recebendo falhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 5a4b4dc79b0f0dad661d99fae6377d1c86b673b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="sending-and-receiving-faults"></a>Enviando e recebendo falhas
Falhas de SOAP transmitem condição informações de erro de um serviço para um cliente e no caso de um cliente duplex para um serviço de forma interoperável. Normalmente um serviço define o conteúdo de falhas personalizado e especifica quais operações podem retorná-los. (Para obter mais informações, consulte [definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Este tópico discute como um serviço ou cliente duplex pode enviar essas falhas quando a condição de erro correspondente e como um cliente ou aplicativo de serviço lida com essas falhas. Para obter uma visão geral de tratamento de erros em aplicativos do Windows Communication Foundation (WCF), consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Envio de falhas de SOAP  
 Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> que especifica um tipo personalizado de falhas SOAP. Falhas de SOAP não declaradas são aqueles que não são especificados no contrato para uma operação.  
  
### <a name="sending-declared-faults"></a>Envio de falhas declaradas  
 Para enviar uma falha SOAP declarada, detectar a condição de erro para o qual a falha SOAP é apropriada e gerar um novo <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> onde o parâmetro de tipo é um novo objeto do tipo especificado no <xref:System.ServiceModel.FaultContractAttribute> para essa operação. O exemplo de código a seguir mostra o uso de <xref:System.ServiceModel.FaultContractAttribute> para especificar que o `SampleMethod` operação pode retornar uma falha SOAP com o tipo de detalhe de `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 Para transmitir o `GreetingFault` informações de erro para o cliente, capturar a condição de erro apropriado e lançar um novo <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> do tipo `GreetingFault` com um novo `GreetingFault` objeto como argumento, como no exemplo de código a seguir. Se o cliente é um aplicativo de cliente do WCF, ele passa por isso como uma exceção gerenciada em que o tipo é <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> do tipo `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Envio de falhas não declaradas  
 Envio de falhas não declaradas podem ser muito útil para diagnosticar rapidamente e depurar problemas em aplicativos do WCF, mas sua utilidade, como uma ferramenta de depuração é limitada. Geralmente, quando depurá-lo é recomendável que você use o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade. Quando você definir esse valor como true, os clientes enfrentam tais falhas como <xref:System.ServiceModel.FaultException%601> exceções do tipo <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Definir como exceções gerenciadas podem expor informações do aplicativo interno, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` pode permitir que clientes do WCF para obter informações sobre exceções de operação de serviço interno, incluindo pessoal ou de identificação de informações confidenciais.  
>   
>  Portanto, definir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` só é recomendado como um modo de depuração temporariamente um aplicativo de serviço. Além disso, o WSDL para um método que retorna sem tratamento gerenciados exceções dessa maneira não contém o contrato para o <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes devem esperar a possibilidade de uma falha de SOAP desconhecida (retornado para clientes do WCF como <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objetos) para obter as informações de depuração corretamente.  
  
 Para enviar uma falha de SOAP não declarada, gerar um <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objeto (ou seja, não o tipo genérico <xref:System.ServiceModel.FaultException%601>) e passe a cadeia de caracteres para o construtor. Isso é exposto para os aplicativos de cliente do WCF como um lançado <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> exceção onde a cadeia de caracteres está disponível ao chamar o <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> método.  
  
> [!NOTE]
>  Se você declarar uma falha SOAP do tipo cadeia de caracteres e, em seguida, gerar isso em seu serviço como uma <xref:System.ServiceModel.FaultException%601> onde o parâmetro de tipo é um <xref:System.String?displayProperty=nameWithType> o valor de cadeia de caracteres é atribuído para o <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> propriedade e não está disponível no <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Lidando com falhas  
 Em clientes do WCF, falhas de SOAP que ocorrem durante a comunicação que são de interesse para os aplicativos cliente são geradas como exceções gerenciadas. Embora haja muitas exceções que podem ocorrer durante a execução de qualquer programa, aplicativos que usam o modelo de programação de cliente do WCF podem esperar lidar com exceções de dois tipos a seguir como resultado de comunicação.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> objetos são gerados quando uma operação excede o período de tempo limite especificado.  
  
 <xref:System.ServiceModel.CommunicationException> objetos são gerados quando há alguma condição de erro de comunicação recuperáveis no serviço ou cliente.  
  
 O <xref:System.ServiceModel.CommunicationException> classe tem dois tipos derivados importantes <xref:System.ServiceModel.FaultException> e genérica <xref:System.ServiceModel.FaultException%601> tipo.  
  
 <xref:System.ServiceModel.FaultException> exceções são geradas quando um ouvinte recebe uma falha que não é esperada ou especificada no contrato de operação; Normalmente isso ocorre quando o aplicativo está sendo depurado e o serviço tem o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade definida como `true`.  
  
 <xref:System.ServiceModel.FaultException%601> exceções são geradas no cliente quando uma falha que é especificada no contrato de operação é recebida em resposta a uma operação bidirecional (ou seja, um método com um <xref:System.ServiceModel.OperationContractAttribute> atributo com <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> definida como `false`).  
  
> [!NOTE]
>  Quando um serviço do WCF tem o <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade definida como `true` o cliente apresenta isso como um não declarada <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes podem detectar essa falha específica ou tratar a falha em um bloco catch para <xref:System.ServiceModel.FaultException>.  
  
 Normalmente, apenas <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, e <xref:System.ServiceModel.CommunicationException> exceções são de interesse para os clientes e serviços.  
  
> [!NOTE]
>  Outras exceções, obviamente, ocorrer. Exceções inesperadas incluem falhas catastróficas como <xref:System.OutOfMemoryException?displayProperty=nameWithType>; normalmente aplicativos não devem capturar esses métodos.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Capturar exceções de falha na ordem correta  
 Porque <xref:System.ServiceModel.FaultException%601> deriva <xref:System.ServiceModel.FaultException>, e <xref:System.ServiceModel.FaultException> deriva <xref:System.ServiceModel.CommunicationException>, é importante capturar essas exceções na ordem correta. Se, por exemplo, você tem um try/catch bloco no qual você primeiro captura <xref:System.ServiceModel.CommunicationException>, todos especificados e não especificado de falhas de SOAP são manipuladas há; todos os blocos catch subsequentes para manipular um personalizado <xref:System.ServiceModel.FaultException%601> exceção nunca sejam invocados.  
  
 Lembre-se de que uma operação pode retornar qualquer número de falhas especificados. Cada falha é um tipo exclusivo e deve ser tratada separadamente.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Lidar com exceções ao fechar o canal  
 A maioria da discussão anterior tem a ver com falhas enviadas durante o processamento de mensagens do aplicativo, ou seja, as mensagens enviadas explicitamente pelo cliente quando o aplicativo cliente chama as operações no objeto de cliente do WCF.  
  
 Mesmo com objetos locais descartar o objeto pode gerar ou mascarar exceções que ocorrem durante o processo de reciclagem. Algo semelhante pode ocorrer quando você usa objetos de cliente do WCF. Quando você chamar operações está enviando mensagens sobre uma conexão estabelecida. Fechar o canal pode gerar exceções se a conexão não pode ser fechada corretamente ou se já estiver fechado, mesmo se todas as operações retornadas corretamente.  
  
 Normalmente, canais de objeto do cliente são fechados em uma das seguintes maneiras:  
  
-   Quando o objeto de cliente do WCF é reciclado.  
  
-   Quando o aplicativo cliente chama <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   Quando o aplicativo cliente chama <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   Quando o aplicativo cliente chama uma operação que é uma operação de encerramento de uma sessão.  
  
 Em todos os casos, fechar o canal instrui o canal para começar a fechar todos os canais subjacentes que podem estar enviando mensagens para dar suporte a funcionalidades complexas no nível do aplicativo. Por exemplo, quando um contrato requer sessões uma associação tenta estabelecer uma sessão de troca de mensagens com o canal de serviço até que seja estabelecida uma sessão. Quando o canal for fechado, o canal da sessão subjacente notifica o serviço que a sessão seja encerrada. Nesse caso, se o canal já foi anulada, fechado, ou caso contrário, será usado (por exemplo, quando um cabo de rede está desconectado), o canal do cliente não pode informar o canal de serviço que a sessão será encerrada e uma exceção pode ocorrer.  
  
### <a name="abort-the-channel-if-necessary"></a>Anular o canal, se necessário  
 Porque o canal de fechamento, também pode lançar exceções, em seguida, é recomendável que além de capturar exceções de falha na ordem correta, é importante anular o canal que foi usado para fazer a chamada em um bloco catch.  
  
 Se a falha transmite informações de erro específicas para uma operação e continua sendo possível que outras pessoas podem usá-lo, não é necessário para anular o canal (embora nesses casos são raros). Em todos os outros casos, é recomendável que você anula o canal. Para obter um exemplo que demonstra todos esses pontos, consulte [esperado exceções](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 O exemplo de código a seguir mostra como tratar exceções de falha SOAP em um aplicativo cliente básico, incluindo uma falha declarada e uma falha não declarada.  
  
> [!NOTE]
>  Esse código de exemplo não usa o `using` construir. Como fechar canais pode lançar exceções, é recomendável que criam um primeiro e, em seguida, abrir, uso de cliente do WCF e fechar o cliente do WCF no mesmo bloco try. Para obter detalhes, consulte [visão geral do cliente WCF](../../../docs/framework/wcf/wcf-client-overview.md) e [evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultException%601>  
 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
 [Exceções esperadas](../../../docs/framework/wcf/samples/expected-exceptions.md)  
 [Evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)
