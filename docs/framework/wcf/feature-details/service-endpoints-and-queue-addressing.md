---
title: Pontos de extremidade de serviço e endereçamento de fila
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 7b4eca1519eeb1ed6357b625a3253105ece2b8ad
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332514"
---
# <a name="service-endpoints-and-queue-addressing"></a>Pontos de extremidade de serviço e endereçamento de fila
Este tópico discute como os clientes atendem serviços leiam de filas e como pontos de extremidade de serviço são mapeados para as filas. Como lembrete, a ilustração a seguir mostra clássico, implantação de aplicativo na fila do Windows Communication Foundation (WCF).  
  
 ![Na fila de diagrama de aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Para o cliente enviar a mensagem para o serviço, o cliente resolve a mensagem à fila de destino. Para o serviço ler mensagens da fila, ele define seu endereço de escuta para a fila de destino. Trata-se no WCF é baseada em URI Uniform Resource Identifier enquanto os nomes de fila do enfileiramento de mensagens (MSMQ) não são baseados no URI. Portanto, é essencial para entender como abordar filas criadas no MSMQ usando o WCF.  
  
## <a name="msmq-addressing"></a>Endereçamento de MSMQ  
 MSMQ usa caminhos e nomes de formato para identificar uma fila. Caminhos de especificam um nome de host e um `QueueName`. Opcionalmente, pode haver uma `Private$` entre o nome do host e o `QueueName` para indicar uma fila particular que não é publicada no serviço de diretório do Active Directory.  
  
 Nomes de caminho são mapeados para "FormatNames" para determinar os aspectos adicionais do endereço, incluindo o protocolo de transferência de Gerenciador de roteamento e a fila. O Gerenciador de fila dá suporte a dois protocolos de transferência: protocolo MSMQ nativo e confiável de mensagens protocolo SRMP (SOAP).  
  
 Para obter mais informações sobre nomes de caminho e o formato do MSMQ, consulte [sobre o enfileiramento de mensagens](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>Serviço de endereçamento e NetMsmqBinding  
 Ao tratar de uma mensagem para um serviço, o esquema de URI é escolhido com base no transporte usado para comunicação. Cada transporte em WCF tem um esquema exclusivo. O esquema deve refletir a natureza de transporte usado para comunicação. Por exemplo, NET. TCP, NET. pipe, HTTP e assim por diante.  
  
 O MSMQ em fila transporte em WCF expõe um esquema de NET. MSMQ. Qualquer mensagem direcionada usando o esquema de NET. MSMQ é enviada usando o `NetMsmqBinding` no canal de transporte em fila do MSMQ.  
  
 O endereçamento de uma fila no WCF baseia-se no seguinte padrão:  
  
 NET. MSMQ: / / \< *nome do host*> / [privada /] \< *nome da fila*>  
  
 em que:  
  
-   \<*nome do host*> é o nome do computador que hospeda a fila de destino.  
  
-   [privada] é opcional. Ele é usado ao tratar de uma fila de destino que é uma fila particular. Para resolver uma fila pública, você deve especificar não privado. Observe que, ao contrário dos caminhos MSMQ, não há nenhuma "$" no formato URI WCF.  
  
-   \<*nome da fila*> é o nome da fila. O nome da fila também pode consultar uma subfila. Portanto, \< *nome da fila*> = \< *nome-da-fila*> [; *sub-queue-name*].  
  
 Exemplo 1: Para lidar com uma fila particular PurchaseOrders hospedados no computador abc atadatum.com, o URI seria net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Exemplo 2: Para resolver uma fila pública AccountsPayable hospedado no computador def atadatum.com, o URI seria net.msmq://def.adatum.com/AccountsPayable.  
  
 O endereço da fila é usado como o URI de escuta pelo ouvinte para ler mensagens do. Em outras palavras, o endereço da fila é equivalente a soquete TCP de porta de escuta.  
  
 Um ponto de extremidade que lê uma fila deve especificar o endereço da fila usando o mesmo esquema especificado anteriormente ao abrir o ServiceHost. Para obter exemplos, consulte [associação de MSMQ Net](../../../../docs/framework/wcf/samples/net-msmq-binding.md).  
  
### <a name="multiple-contracts-in-a-queue"></a>Vários contratos em uma fila  
 Mensagens em uma fila podem implementar contratos diferentes. Nesse caso, é essencial que uma das seguintes opções é verdadeira para ler e processar todas as mensagens com êxito:  
  
-   Especifique um ponto de extremidade para um serviço que implementa todos os contratos. Essa é a abordagem recomendada.  
  
-   Especificar vários pontos de extremidade com contratos diferentes, mas certifique-se de que todos os pontos de extremidade usem os mesmos `NetMsmqBinding` objeto. A lógica de expedição em ServiceModel usa uma bomba de mensagem que lê mensagens de fora o canal de transporte de expedição, o que, eventualmente, desprovisionar multiplexa as mensagens com base no contrato de pontos de extremidade diferentes. Uma bomba de mensagem é criada para um par de associação/URI de escuta. O endereço da fila é usado como o URI de escuta pelo ouvinte na fila. Todos os o uso de pontos de extremidade, que o mesmo objeto de associação garante que uma bomba de mensagem único é usada para ler a mensagem e demultiplexar aos pontos de extremidade relevantes com base no contrato.  
  
### <a name="srmp-messaging"></a>Mensagens SRMP  
 Conforme discutido anteriormente, você pode usar o protocolo SRMP para transferências de fila para a fila. Isso é comumente usado quando um transporte HTTP transmite mensagens entre a fila de transmissão e a fila de destino.  
  
 Para usar o protocolo SRMP, tratar mensagens usando o esquema de URI do NET. MSMQ, conforme mencionado anteriormente e especificar a opção de SRMP ou SRMP protegido na `QueueTransferProtocol` propriedade do `NetMsmqBinding`.  
  
 Especificando o `QueueTransferProtocol` propriedade é um recurso somente de envio. Essa é uma indicação pelo cliente do qual o tipo de fila de transferência de protocolo a ser usado.  
  
### <a name="using-active-directory"></a>Usando o Active Directory  
 MSMQ vem com suporte para integração do Active Directory. Quando MSMQ é instalado com a integração do Active Directory, o computador deve ser parte de um domínio do Windows. Active Directory é usado para publicar as filas para descoberta; Essas filas são chamadas *filas públicas*. Ao tratar de uma fila, a fila pode ser resolvida usando o Active Directory. Isso é semelhante a como o sistema de nome de domínio (DNS) é usado para resolver o endereço IP de um nome de rede. O `UseActiveDirectory` propriedade em `NetMsmqBinding` é um valor booliano que indica se o canal em fila deve usar o Active Directory para resolver o URI da fila. Por padrão, ele é definido como `false`. Se o `UseActiveDirectory` estiver definida como `true`, em seguida, o canal em fila usa o Active Directory para converter o URI net.msmq:// em nome de formato.  
  
 O `UseActiveDirectory` propriedade é significativa apenas para o cliente que está enviando a mensagem porque ele é usado para resolver o endereço da fila durante o envio de mensagens.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>O mapeamento de URI de NET. MSMQ para nomes de formato de enfileiramento de mensagens  
 O canal em fila lida com o nome do NET. MSMQ URI fornecido para o canal para nomes de formato MSMQ de mapeamento. A tabela a seguir resume as regras usadas para mapear entre eles.  
  
|Endereço da fila com base no URI do WCF|Use a propriedade do Active Directory|Propriedade de protocolo de transferência de fila|Nomes de formato resultantes do MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|Net.msmq://\<machine-name>/private/abc|False (padrão)|Nativo (padrão)|DIRECT=OS:machine-name\private$\abc|  
|Net.msmq://\<machine-name>/private/abc|False|SRMP|DIRECT=http://machine/msmq/private$/abc|  
|Net.msmq://\<machine-name>/private/abc|verdadeiro|Nativo|PÚBLICO = some guid (o GUID da fila)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Leitura de mensagens da fila de inatividade ou a fila de mensagens suspeitas  
 Para ler mensagens de uma fila de mensagens suspeitas que é uma subfila da fila de destino, abra o `ServiceHost` com o endereço da subfila de mensagens.  
  
 Exemplo: Um serviço que lê da fila de mensagens suspeitas da fila da máquina local privada PurchaseOrders aborde net.msmq://localhost/private/PurchaseOrders;poison.  
  
 Para ler mensagens de uma fila mortas transacional do sistema, o URI deve estar no formato: $ net.msmq://localhost/system; DeadXact.  
  
 Para ler mensagens de uma fila de inatividade do sistema não transacional, o URI deve estar no formato: $ net.msmq://localhost/system; mensagens mortas.  
  
 Ao usar uma fila de inatividade personalizada, observe que a fila de inatividade deve residir no computador local. Como tal, o URI para a fila de inatividade é restrito ao formulário:  
  
 NET. MSMQ: //localhost/ [privada /] \< *personalizado-dead-letra-queue-name*>.  
  
 Um serviço WCF verifica que tenham sido tratadas de todas as mensagens recebidas para a determinada fila está escutando. Se a fila de destino da mensagem não corresponde ao encontrado na fila, o serviço não processa a mensagem. Esse é um problema que devem ser resolvidos por serviços de escuta para uma fila de inatividade porque qualquer mensagem na fila de inatividade deveria ser entregue em outro lugar. Para ler mensagens de uma fila de inatividade ou de uma fila de mensagens suspeitas, uma `ServiceBehavior` com o <xref:System.ServiceModel.AddressFilterMode.Any> parâmetro deve ser usado. Por exemplo, consulte [filas de mensagens mortas](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>Serviço de endereçamento e MsmqIntegrationBinding  
 O `MsmqIntegrationBinding` é usado para comunicação com aplicativos tradicionais do MSMQ. Para facilitar a interoperação com um aplicativo de MSMQ existente, o WCF oferece suporte ao endereçamento de nome de formato único. Dessa forma, as mensagens enviadas usando essa associação devem estar em conformidade com o esquema de URI:  
  
 msmq.formatname:\<*MSMQ-format-name*>>  
  
 O nome de MSMQ-formato tem o formato especificado pelo MSMQ no [sobre o enfileiramento de mensagens](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Observe que você só pode usar nomes de formato direto e nomes de formato públicos e privados (requer a integração do Active Directory) ao receber mensagens de uma fila usando `MsmqIntegrationBinding`. No entanto, é recomendável que você use nomes de formato direto. Por exemplo, em [!INCLUDE[wv](../../../../includes/wv-md.md)], usar qualquer outro nome de formato faz com que um erro porque o sistema tenta abrir uma subfila, que só pode ser aberta com nomes de formato direto.  
  
 Ao abordar SRMP usando `MsmqIntegrationBinding`, não há nenhum requisito de adicionar /msmq/ no nome do formato direto para ajudar a serviços de informações da Internet (IIS) com expedição. Por exemplo: Ao tratar de uma fila abc usando o SRMP de protocolo, em vez de DIRECT =http://adatum.com/msmq/private$/ abc, você deve usar DIRECT =http://adatum.com/private$/ abc.  
  
 Observe que você não pode usar net.msmq:// endereçamento com `MsmqIntegrationBinding`. Porque `MsmqIntegrationBinding` dá suporte à forma livre MSMQ formato nome endereçamento, você pode usar um serviço WCF que usa essa associação para usar recursos da lista de distribuição e de multicast no MSMQ. Especificação de uma exceção `CustomDeadLetterQueue` ao usar o `MsmqIntegrationBinding`. Ele deve ser do net.msmq:// formulário, semelhante a como ele é especificado usando o `NetMsmqBinding`.  
  
## <a name="see-also"></a>Consulte também
- [Hospedagem na Web de um aplicativo na fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
