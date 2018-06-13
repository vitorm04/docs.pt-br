---
title: Objetos binários de codificação com codificador ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489476"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Objetos binários de codificação com codificador ByteStream
Enviar e receber dados binários brutos com o Windows Communication Foundation (WCF) é configurado usando <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Arquitetura de codificador de mensagem de fluxo de bytes  
 O codificador de mensagem binária usado pelo WCF não têm recursos para processamento, validar ou identificar os dados binários subjacentes na mensagem. O pacote de dados é codificado em XML, enviado, recebido e decodificar. O codificador processa os dados após ser transmitido para o transporte e antes que a mensagem é enviada para a fila de mensagens. Funcionalmente, o codificador binário encapsula os dados da mensagem em `<binary>` elementos para enviar e remove os elementos após receber a mensagem.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Usando o codificador de mensagens do fluxo de bytes  
 O exemplo a seguir mostra um contrato de serviço que implementa o codificador de mensagens do fluxo de bytes.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 O exemplo a seguir mostra o serviço que está sendo invocado.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 No caso de uso de um serviço que implementa uma infraestrutura de mensagem (como um roteador), a mensagem é processada sem inspecionando, validar ou caso contrário, interagir com a mensagem, conforme mostrado no exemplo a seguir.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Cenários  
 O codificador de fluxo de bytes é útil nas seguintes situações.  
  
-   Transferência de uma imagem JPEG entre computadores usando o WCF. Nesse cenário, a imagem será enviado por meio do transporte de uma fonte externa, e os dados enviados serão os bytes brutos que compõem a imagem. Um serviço receberá os dados binários e exibir a imagem.  
  
-   Ler informações de fora de uma fila de mensagens e processá-la. A mensagem será lido de um Gerenciador de fila de mensagens e passada o canal de mensagens da fila devem ser tratados. O canal de fila de mensagens irá atuar como um Gerenciador de fila na pilha de canal WCF.  
  
 No caso de enviar uma mensagem por um canal de mensagens da fila, o remetente não tem controle sobre os bytes recebidos do Gerenciador de fila. Se o processo de recebimento não tem nenhum recurso para ler os bytes brutos, a mensagem será recebida como mal formatado e não será processada; presume-se que o processo de recebimento terá a capacidade de converter os bytes recebidos para um formato utilizável.
