---
title: Estendendo a camada do canal
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 76ca76d7973403c657b8f68bfde9619df36f220e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797142"
---
# <a name="extending-the-channel-layer"></a>Estendendo a camada do canal
A camada de canal é responsável pela troca de mensagens entre clientes e serviços. As extensões de canal podem implementar a nova funcionalidade de protocolo, como segurança ou funcionalidade de transporte, como implementar um novo transporte de rede para transportar mensagens SOAP.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de canal](channel-model-overview.md)  
 Fornece uma visão geral de alto nível de quais canais são, os recursos que eles fornecem e como eles funcionam tanto em um serviço quanto em um aplicativo cliente.  
  
 [Desenvolvimento de canais](developing-channels.md)  
 Descreve detalhadamente as funções que os vários tipos de infraestrutura de canal desempenham, como funciona o ciclo de vida de estado e o mecanismo de estado, como lidar com exceções e falhas, como implementar o suporte a metadados e como os canais funcionam com codificadores de mensagem.  
  
 [Codificadores personalizados](custom-encoders.md)  
 Descreve a função que os codificadores de mensagem desempenham em canais e como criar um.  
  
 [Upgrades de fluxo personalizados](custom-stream-upgrades.md)  
 Descreve o processo de atualização dos fluxos fornecidos por transportes orientados a fluxo.
