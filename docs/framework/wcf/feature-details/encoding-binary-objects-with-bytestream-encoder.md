---
title: "Objetos binários de codificação com codificador ByteStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acf9d2ace66702c5f0bc522d97ae92869891a38b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Objetos binários de codificação com codificador ByteStream
Enviar e receber dados binários brutos com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é configurado usando <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Arquitetura de codificador de mensagem de fluxo de bytes  
 O codificador de mensagem binária usado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não têm recursos para processamento, validar ou identificar os dados binários subjacentes na mensagem. O pacote de dados é codificado em XML, enviado, recebido e decodificar. O codificador processa os dados após ser transmitido para o transporte e antes que a mensagem é enviada para a fila de mensagens. Funcionalmente, o codificador binário encapsula os dados da mensagem em `<binary>` elementos para enviar e remove os elementos após receber a mensagem.  
  
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
  
-   Transferência de uma imagem JPEG entre computadores usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Nesse cenário, a imagem será enviado por meio do transporte de uma fonte externa, e os dados enviados serão os bytes brutos que compõem a imagem. Um serviço receberá os dados binários e exibir a imagem.  
  
-   Ler informações de fora de uma fila de mensagens e processá-la. A mensagem será lido de um Gerenciador de fila de mensagens e passada o canal de mensagens da fila devem ser tratados. O canal de mensagens da fila atuará como um Gerenciador de filas na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais.  
  
 No caso de enviar uma mensagem por um canal de mensagens da fila, o remetente não tem controle sobre os bytes recebidos do Gerenciador de fila. Se o processo de recebimento não tem nenhum recurso para ler os bytes brutos, a mensagem será recebida como mal formatado e não será processada; presume-se que o processo de recebimento terá a capacidade de converter os bytes recebidos para um formato utilizável.
