---
title: "Segurança de mensagem no WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0948c7447bcfd32ad666072ce6f74b1f6fd8aed8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-in-wcf"></a>Segurança de mensagem no WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]tem dois modos principais para fornecer segurança (`Transport` e `Message`) e um terceiro modo (`TransportWithMessageCredential`) que combina os dois. Este tópico aborda a segurança de mensagem e os motivos para usá-lo.  
  
## <a name="what-is-message-security"></a>O que é a segurança de mensagem?  
 Segurança de mensagem usa a especificação WS-Security para proteger as mensagens. O WS-Securityspecification descreve aprimoramentos para garantir a confidencialidade, integridade e autenticação no nível da mensagem SOAP (em vez de nível de transporte) de mensagens SOAP.  
  
 Em suma, segurança de mensagem é diferente da segurança de transporte, encapsulando as credenciais de segurança e declarações com cada mensagem junto com qualquer proteção de mensagem (assinatura ou criptografia). Aplicar a segurança diretamente para a mensagem modificando seu conteúdo permite que a mensagem protegida seja contendo automaticamente em relação aos aspectos de segurança. Isso permite que alguns cenários que não são possíveis quando a segurança de transporte é usada.  
  
## <a name="reasons-to-use-message-security"></a>Razões para usar segurança de mensagem  
 Na segurança em nível de mensagem, todas as informações de segurança são encapsulados na mensagem. Segurança da mensagem com segurança em nível de mensagem em vez da segurança de nível de transporte tem as seguintes vantagens:  
  
-   Segurança de ponta a ponta. Segurança de transporte, como o protocolo (SSL) protege apenas mensagens quando a comunicação ponto a ponto. Se a mensagem é roteada para um ou mais intermediários SOAP (por exemplo, um roteador) antes de alcançar o receptor ultimate, a mensagem em si não está protegida quando um intermediário lê-lo da transmissão. Além disso, as informações de autenticação de cliente estão disponíveis somente para o primeiro intermediário e devem ser transmitidas novamente para o destinatário final na forma de fora da banda, se necessário. Isso se aplica mesmo se a rota inteira usa segurança SSL entre saltos individuais. Como a segurança de mensagem trabalha diretamente com a mensagem e protege o XML, a segurança permanece com a mensagem, independentemente de quantas intermediários são envolvidos antes de atingir o destinatário final. Isso permite que um cenário de segurança ponta a ponta.  
  
-   Maior flexibilidade. Partes da mensagem, em vez da mensagem inteira, podem ser assinadas ou criptografadas. Isso significa que intermediários podem exibir as partes da mensagem que se destinam para eles. Se o remetente precisa fazer parte das informações na mensagem visível para os intermediários, mas deseja garantir que ele não foi violado, ele apenas pode assiná-lo, mas deixá-lo sem criptografia. Como a assinatura é parte da mensagem, o destinatário final pode verificar se as informações na mensagem foi recebidas intacta. Um cenário pode ter um intermediário SOAP mensagem rotas de acordo com o valor do cabeçalho de ação de serviço. Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] conecta-se a segurança de mensagem é usada, mas não criptografa o valor de ação. Portanto, essas informações estão disponíveis para todos os intermediários, mas não pode alterá-la.  
  
-   Suporte para vários transportes. Você pode enviar mensagens protegidas em muitos transportes diferentes, como pipes nomeados e TCP, sem a necessidade de contar com o protocolo de segurança. Com segurança em nível de transporte, todas as informações de segurança tem escopo para uma conexão de transporte particular único e não estão disponíveis para o conteúdo da mensagem. Segurança de mensagem faz com que a mensagem segura, independentemente de qual transporte você use para transmitir a mensagem e o contexto de segurança é inserido diretamente dentro a mensagem.  
  
-   Suporte para um amplo conjunto de credenciais e declarações. A segurança da mensagem é baseada na especificação WS-Security, que fornece uma estrutura extensível capaz de transmitir qualquer tipo de declaração dentro da mensagem SOAP. Ao contrário de segurança de transporte, o conjunto de mecanismos de autenticação ou declarações, que você pode usar não é limitado pelos recursos de transporte. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]segurança de mensagem inclui vários tipos de declaração e autenticação de transmissão e pode ser estendida para dar suporte a tipos adicionais conforme necessário. Por esses motivos, já por exemplo, um cenário federado credenciais não é possível sem segurança de mensagem. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]oferece suporte a cenários de Federação WCF, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Como comparam a mensagem e segurança de transporte  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Prós e contras de segurança em nível de transporte  
 Segurança de transporte tem as seguintes vantagens:  
  
-   Não exige que as partes da comunicação entendam os conceitos de segurança de nível de XML. Isso pode melhorar a interoperabilidade, por exemplo, quando HTTPS é usado para proteger a comunicação.  
  
-   Em geral, melhor desempenho.  
  
-   Os aceleradores de hardware estão disponíveis.  
  
-   É possível streaming.  
  
 Segurança de transporte tem as seguintes desvantagens:  
  
-   Salto-para-hop somente.  
  
-   Limitado e inextensible conjunto de credenciais.  
  
-   Dependente de transporte.  
  
### <a name="disadvantages-of-message-level-security"></a>Desvantagens de segurança em nível de mensagem  
 Segurança de mensagem tem as seguintes desvantagens:  
  
-   Desempenho  
  
-   Não é possível usar o fluxo de mensagem.  
  
-   Requer a implementação de mecanismos de segurança de nível de XML e suporte para especificação WS-Security. Isso pode afetar a interoperabilidade.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Como: usar a segurança de transporte e as credenciais de mensagem](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft padrões e práticas recomendadas, capítulo 3: segurança de camada de transporte de implementação e de mensagem](http://go.microsoft.com/fwlink/?LinkId=88897)
