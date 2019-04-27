---
title: Objetos binários de codificação com codificador ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856499"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Objetos binários de codificação com codificador ByteStream
Enviar e receber dados binários brutos com o Windows Communication Foundation (WCF) é configurado usando <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Arquitetura de codificador de mensagem do byte Stream  
 O codificador de mensagem binária usado pelo WCF não têm recursos para processar, validar ou identificando os dados binários subjacentes na mensagem. O pacote de dados é codificado em XML, enviado, recebido e decodificado. O codificador processa os dados após ser transmitido para o transporte e antes da mensagem é enviada para a fila de mensagens. Funcionalmente, o codificador binário encapsula os dados da mensagem em `<binary>` elementos para o envio e remove os elementos depois que a mensagem é recebida.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Usando o codificador de mensagem do Byte Stream  
 O exemplo a seguir mostra um contrato de serviço que implementa o codificador de mensagem de fluxo de bytes.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 O exemplo a seguir mostra o serviço que está sendo invocado.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 No caso de uso de um serviço que implementa uma infra-estrutura de mensagem (como um roteador), a mensagem é processada sem inspecionando, validar ou caso contrário, interagir com a mensagem, conforme mostrado no exemplo a seguir.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Cenários  
 O codificador do Byte Stream é útil nos cenários a seguir.  
  
-   Transferência de uma imagem JPEG entre computadores usando o WCF. Nesse cenário, a imagem será chegam por meio do transporte de uma fonte externa e os dados enviados serão os bytes brutos que compõem a imagem. Um serviço receberá os dados binários e exibir a imagem.  
  
-   Ler informações de fora de uma fila de mensagens e processá-la. A mensagem será ler de um Gerenciador de fila de mensagens e passada para cima o canal de mensagens da fila a ser manipulado. O canal de mensagens da fila atuará como um Gerenciador de fila na pilha de canais do WCF.  
  
 No caso de enviar uma mensagem sobre um canal de mensagens da fila, o remetente não tem controle sobre os bytes recebidos do Gerenciador de fila. Se o processo de recebimento não tem nenhum recurso para ler os bytes brutos, a mensagem será recebida medida formatada incorretamente e não serão processados; supõe-se que o processo de recebimento terão a capacidade de converter os bytes recebidos para um formato utilizável.
