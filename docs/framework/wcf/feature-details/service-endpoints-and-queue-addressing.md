---
title: Pontos de extremidade de serviço e endereçamento de fila
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: a2f4807e447482ee790f2ca9a2ab4dbde531b1c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-endpoints-and-queue-addressing"></a>Pontos de extremidade de serviço e endereçamento de fila
Este tópico discute como os clientes atendem serviços leem de filas e como pontos de extremidade de serviço são mapeados para filas. Como um lembrete, a ilustração a seguir mostra clássica, implantação de aplicativo na fila do Windows Communication Foundation (WCF).  
  
 ![Na fila de diagrama do aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Para o cliente enviar a mensagem para o serviço, o cliente trata a mensagem à fila de destino. Para o serviço ler mensagens da fila, ele define o endereço de escuta para a fila de destino. Endereçamento no WCF é baseado no URI Uniform Resource Identifier enquanto nomes de filas do enfileiramento de mensagens (MSMQ) não são baseados no URI. Portanto, é essencial compreender como tratar filas criadas no MSMQ usando o WCF.  
  
## <a name="msmq-addressing"></a>Endereçamento de MSMQ  
 MSMQ usa caminhos e nomes de formato para identificar uma fila. Caminhos de especificar um nome de host e um `QueueName`. Opcionalmente, pode haver um `Private$` entre o nome do host e o `QueueName` para indicar uma fila particular que não é publicada no serviço de diretório do Active Directory.  
  
 Nomes de caminho são mapeados para "FormatNames" para determinar os aspectos adicionais do endereço, incluindo o protocolo de transferência de Gerenciador de roteamento e a fila. O Gerenciador de fila dá suporte a dois protocolos de transferência: o protocolo nativo do MSMQ e confiável de mensagens protocolo SRMP (SOAP).  
  
 Para obter mais informações sobre nomes de caminho e o formato do MSMQ, consulte [sobre enfileiramento](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding e endereçamento de serviço  
 Ao endereçar uma mensagem para um serviço, o esquema de URI é escolhido com base no transporte usado para comunicação. Cada transporte do WCF tem um esquema exclusivo. O esquema deve refletir a natureza de transporte usado para comunicação. Por exemplo, net.tcp, NET. pipe, HTTP e assim por diante.  
  
 O MSMQ em fila transporte em WCF expõe um esquema NET. MSMQ. Qualquer mensagem endereçada usando o esquema NET. MSMQ é enviada usando o `NetMsmqBinding` no canal de transporte em fila do MSMQ.  
  
 O endereçamento de uma fila no WCF com base no seguinte padrão:  
  
 NET. MSMQ: / / \< *nome de host*> / [privada /] \< *nome da fila*>  
  
 em que:  
  
-   \<*nome do host*> é o nome do computador que hospeda a fila de destino.  
  
-   [privada] é opcional. Ele é usado ao endereçar uma fila de destino é uma fila particular. Para resolver uma fila pública, você não deve especificar privada. Observe que, ao contrário dos caminhos MSMQ, não há nenhum "$" no formato URI WCF.  
  
-   \<*nome da fila*> é o nome da fila. O nome da fila também pode referir-se para uma subfila de mensagens. Portanto, \< *nome de fila*> = \< *nome-da-fila*> [; *nome de queue sub*].  
  
 Exemplo 1: Para endereçar uma fila particular PurchaseOrders hospedados no computador abc atadatum.com, o URI seria net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Exemplo 2: Para resolver uma fila pública AccountsPayable hospedado no computador def atadatum.com, o URI seria net.msmq://def.adatum.com/AccountsPayable.  
  
 O endereço da fila é usado como o URI de escuta pelo ouvinte para ler mensagens de. Em outras palavras, o endereço da fila é equivalente para o soquete de TCP de porta de escuta.  
  
 Um ponto de extremidade que lê uma fila deve especificar o endereço da fila usando o mesmo esquema especificado anteriormente ao abrir o ServiceHost. Para obter exemplos, consulte [associação de MSMQ Net](../../../../docs/framework/wcf/samples/net-msmq-binding.md) e [mensagem de enfileiramento de mensagens de associação exemplos de integração](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Vários contratos em uma fila  
 Mensagens em uma fila podem implementar contratos diferentes. Nesse caso, é essencial que uma das seguintes opções é verdadeira para ler e processar todas as mensagens com êxito:  
  
-   Especifique um ponto de extremidade para um serviço que implementa todos os contratos. Essa é a abordagem recomendada.  
  
-   Especificar vários pontos de extremidade com contratos diferentes, mas certifique-se de que todos os pontos de extremidade usem os mesmos `NetMsmqBinding` objeto. A lógica de expedição de ServiceModel usa uma bomba de mensagem que lê mensagens fora do canal de transporte de expedição, que eventualmente desmultiplexa mensagens com base no contrato de pontos de extremidade diferentes. Uma bomba de mensagem é criada para um par de associação/URI de escuta. O endereço da fila é usado como o URI de escuta pelo ouvinte na fila. Com o uso de pontos de extremidade que o mesmo objeto de associação garante que uma bomba de mensagem única é usada para ler a mensagem e eliminação multiplex para pontos de extremidade relevantes com base no contrato.  
  
### <a name="srmp-messaging"></a>Mensagens SRMP  
 Como discutido anteriormente, você pode usar o protocolo SRMP para transferências de fila para a fila. Isso é geralmente usado quando um transporte HTTP transmite mensagens entre a fila de transmissão e a fila de destino.  
  
 Para usar o protocolo de transferência SRMP, receba mensagens usando o esquema URI do NET. MSMQ, conforme mencionado anteriormente e especificar a opção de SRMP ou SRMP protegidos no `QueueTransferProtocol` propriedade o `NetMsmqBinding`.  
  
 Especificando o `QueueTransferProtocol` propriedade é um recurso somente de envio. Essa é uma indicação pelo cliente que tipo de fila de transferência de protocolo a ser usado.  
  
### <a name="using-active-directory"></a>Usando o Active Directory  
 MSMQ vem com suporte para integração do Active Directory. Quando o MSMQ está instalado com a integração do Active Directory, o computador deve ser parte de um domínio do Windows. Active Directory é usado para publicar as filas para descoberta; Essas filas são chamadas *filas públicas*. Ao endereçar uma fila, a fila pode ser resolvida usando o Active Directory. Isso é semelhante a como o sistema de nome de domínio (DNS) é usado para resolver o endereço IP de um nome de rede. O `UseActiveDirectory` propriedade `NetMsmqBinding` é um valor booliano que indica se o canal em fila deve usar o Active Directory para resolver o URI da fila. Por padrão, ele é definido como `false`. Se o `UseActiveDirectory` está definida como `true`, em seguida, o canal em fila usa o Active Directory para converter o net.msmq:// URI para o nome de formato.  
  
 O `UseActiveDirectory` propriedade é significativa apenas para o cliente que está enviando a mensagem porque ele é usado para resolver o endereço da fila ao enviar mensagens.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>O mapeamento de URI do NET. MSMQ para nomes de formato de enfileiramento de mensagens  
 O canal em fila manipula mapear o nome do URI de NET. MSMQ fornecido para o canal para nomes de formato do MSMQ. A tabela a seguir resume as regras usadas para mapear entre eles.  
  
|Endereço da fila com base no URI do WCF|Use a propriedade do Active Directory|Propriedade de protocolo de transferência de fila|Nomes de formato resultantes do MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|NET.MSMQ://\<machine-name >/privado/abc|False (padrão)|Nativo (padrão)|DIRECT=OS:machine-name\private$\abc|  
|NET.MSMQ://\<machine-name >/privado/abc|False|SRMP|DIRECT =http://machine/msmq/private$/ abc|  
|NET.MSMQ://\<machine-name >/privado/abc|verdadeiro|Nativo|PÚBLICO = alguns guid (o GUID da fila)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Lendo mensagens da fila de mensagens mortas ou a fila de mensagens suspeitas  
 Para ler mensagens de uma fila de mensagens suspeitas é uma subfila da fila de destino, abra o `ServiceHost` com o endereço da subfila.  
  
 Exemplo: Um serviço que lê da fila de mensagens suspeitas da fila particular PurchaseOrders na máquina local tratar net.msmq://localhost/private/PurchaseOrders;poison.  
  
 Para ler mensagens de uma fila de mensagens mortas transacional do sistema, o URI deve estar no formato: net.msmq://localhost/system$; DeadXact.  
  
 Para ler mensagens de uma fila de mensagens mortas do sistema não transacionais, o URI deve ser do formulário: net.msmq://localhost/system$; mensagens mortas.  
  
 Ao usar uma fila de mensagens mortas personalizada, observe que a fila de mensagens mortas deve residir no computador local. Como tal, o URI para a fila de mensagens mortas é restrito ao formulário:  
  
 NET. MSMQ: //localhost/ [privada /] \< *personalizado-mortas-letra--nome de fila*>.  
  
 Um serviço WCF verifica que todas as mensagens recebidas foram resolvidas para a fila particular está escutando nas. Se a fila de destino da mensagem não coincide com a fila que for localizado no, o serviço não processa a mensagem. Este é um problema que serviços de escuta em uma fila de mensagens mortas devem tratar porque qualquer mensagem na fila de mensagens mortas deveria ser entregue em outro lugar. Para ler mensagens de uma fila de mensagens mortas ou de uma fila suspeita, um `ServiceBehavior` com o <xref:System.ServiceModel.AddressFilterMode.Any> parâmetro deve ser usado. Para obter um exemplo, consulte [filas de mensagens mortas](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding e endereçamento de serviço  
 O `MsmqIntegrationBinding` é usado para comunicação com aplicativos tradicionais do MSMQ. Para facilitar a interoperação com um aplicativo de MSMQ existente, o WCF dá suporte a endereçamento de nome de formato somente. Assim, as mensagens enviadas usando essa associação devem estar de acordo com o esquema de URI:  
  
 msmq.formatname:\<*MSMQ-format-name*>>  
  
 O nome de MSMQ-formato tem o formato especificado pelo MSMQ em [sobre enfileiramento](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Observe que você só pode usar nomes de formato direto e nomes de formato públicos e privados (requer a integração do Active Directory) ao receber mensagens de uma fila usando `MsmqIntegrationBinding`. No entanto, é recomendável que você use nomes de formato direto. Por exemplo, em [!INCLUDE[wv](../../../../includes/wv-md.md)], usar qualquer outro nome de formato causa um erro porque o sistema tenta abrir uma subfila, que só pode ser aberta com nomes de formato direto.  
  
 Ao abordar SRMP usando `MsmqIntegrationBinding`, não há nenhum requisito de adicionar /msmq/ no nome de formato direto para ajudar a serviços de informações da Internet (IIS) com a distribuição. Por exemplo: quando uma fila de protocolo abc usando o SRMP, em vez de direta de endereçamento =http://adatum.com/msmq/private$/ abc, você deve usar DIRECT =http://adatum.com/private$/ abc.  
  
 Observe que você não pode usar o endereçamento net.msmq:// com `MsmqIntegrationBinding`. Como `MsmqIntegrationBinding` oferece suporte a forma livre MSMQ formato nome de endereçamento, você pode usar um serviço WCF que usa esta associação para usar recursos da lista de distribuição e de multicast no MSMQ. Especificação de uma exceção `CustomDeadLetterQueue` ao usar o `MsmqIntegrationBinding`. Ele deve estar net.msmq:// a forma, semelhante a como ele é especificado usando o `NetMsmqBinding`.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem na Web de um aplicativo na fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
