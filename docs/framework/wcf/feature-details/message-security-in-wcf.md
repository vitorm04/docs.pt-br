---
title: Segurança de mensagem no WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 81d9acde3c8fab1860904074199066cca55c7186
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724494"
---
# <a name="message-security-in-wcf"></a>Segurança de mensagem no WCF
Windows Communication Foundation (WCF) tem dois modos principais para fornecer segurança (`Transport` e `Message`) e um terceiro modo (`TransportWithMessageCredential`) que combina os dois. Este tópico aborda a segurança de mensagem e os motivos para usá-lo.  
  
## <a name="what-is-message-security"></a>O que é a segurança de mensagem?  
 Segurança de mensagem usa a especificação WS-Security para proteger as mensagens. O WS-Securityspecification descreve aprimoramentos para garantir a confidencialidade, integridade e autenticação no nível da mensagem SOAP (em vez de nível de transporte) de mensagens SOAP.  
  
 Em suma, segurança de mensagem é diferente de segurança de transporte, encapsulando as credenciais de segurança e declarações com todas as mensagens, juntamente com qualquer proteção de mensagem (assinatura ou criptografia). Aplicando a segurança diretamente para a mensagem modificando seu conteúdo permite que a mensagem segura seja automaticamente recipiente em relação aos aspectos de segurança. Isso permite alguns cenários que não são possíveis quando a segurança de transporte é usada.  
  
## <a name="reasons-to-use-message-security"></a>Motivos para usar a segurança de mensagem  
 Na segurança de nível de mensagem, todas as informações de segurança é encapsulada na mensagem. Segurança da mensagem com segurança em nível de mensagem em vez da segurança de nível de transporte tem as seguintes vantagens:  
  
-   Segurança de ponta a ponta. Segurança de transporte, como o protocolo (SSL) protege apenas mensagens quando a comunicação ponto a ponto. Se a mensagem é roteada para um ou mais intermediários SOAP (por exemplo, um roteador) antes de alcançar o receptor ultimate, a mensagem em si não está protegida depois que um intermediário lê-lo na transmissão. Além disso, as informações de autenticação de cliente estão disponíveis somente para o primeiro intermediário e devem ser transmitidas novamente para o receptor ultimate de modo out-of-band, se necessário. Isso se aplica mesmo se a rota inteira usa a segurança SSL entre saltos individuais. Como segurança de mensagem funciona diretamente com a mensagem e protege o XML nele, a segurança permanece com a mensagem, independentemente de quantos intermediários estão envolvidos antes de atingir o receptor ultimate. Isso permite que um cenário de segurança de ponta a ponta true.  
  
-   Maior flexibilidade. Partes da mensagem, em vez da mensagem inteira, podem ser assinadas ou criptografadas. Isso significa que intermediários podem exibir as partes da mensagem que se destinam para eles. Se o remetente precisa fazer parte das informações na mensagem visível para os intermediários, mas deseja garantir que ele não seja violado, ele apenas pode assiná-lo, mas deixá-lo sem criptografia. Uma vez que a assinatura é parte da mensagem, o receptor ultimate pode verificar que as informações na mensagem foi recebidas intacta. Um cenário pode ter um intermediário SOAP essa mensagem de rotas de acordo com o valor do cabeçalho de ação de serviço. Por padrão, o WCF não criptografa o valor de ação, mas assina-se a segurança de mensagem é usada. Portanto, essas informações estão disponíveis para todos os intermediários, mas ninguém pode alterá-lo.  
  
-   Suporte a vários transportes. Você pode enviar as mensagens seguras em muitos diferentes transportes, como pipes nomeados e TCP, sem a necessidade de contar com o protocolo de segurança. Com a segurança de nível de transporte, todas as informações de segurança estão no escopo para uma conexão de transporte particular único e não está disponíveis no conteúdo da mensagem em si. Segurança de mensagem torna a mensagem segura, independentemente de qual transporte deve usar para transmitir a mensagem e o contexto de segurança é incorporado diretamente dentro da mensagem.  
  
-   Suporte para um amplo conjunto de credenciais e declarações. A segurança da mensagem se baseia na especificação WS-Security, que fornece uma estrutura extensível capaz de transmitir qualquer tipo de declaração dentro da mensagem SOAP. Ao contrário de segurança de transporte, o conjunto de mecanismos de autenticação ou declarações, que você pode usar não é limitado pelos recursos de transporte. Segurança de mensagem do WCF inclui vários tipos de autenticação e a declaração de transmissão e pode ser estendida para dar suporte a tipos adicionais conforme necessário. Por esses motivos, já por exemplo, um cenário federado credenciais não é possível sem segurança de mensagem. Para obter mais informações sobre dá suporte a WCF de cenários de federação, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Como comparam a mensagem e segurança de transporte  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Prós e contras de segurança em nível de transporte  
 Segurança de transporte tem as seguintes vantagens:  
  
-   Não requer que as partes da comunicação compreendam os conceitos de segurança de nível de XML. Isso pode melhorar a interoperabilidade, por exemplo, quando HTTPS é usado para proteger a comunicação.  
  
-   Geralmente, melhorar o desempenho.  
  
-   Aceleradores de hardware estão disponíveis.  
  
-   É possível de streaming.  
  
 Segurança de transporte tem as seguintes desvantagens:  
  
-   Salto-para-hop apenas.  
  
-   Conjunto de credenciais inextensible e limitado.  
  
-   Dependente de transporte.  
  
### <a name="disadvantages-of-message-level-security"></a>Desvantagens de segurança em nível de mensagem  
 Segurança de mensagem tem as seguintes desvantagens:  
  
-   Desempenho  
  
-   Não é possível usar o streaming de mensagem.  
  
-   Requer a implementação de mecanismos de segurança de nível de XML e suporte para especificação WS-Security. Isso pode afetar a interoperabilidade.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Como usar a segurança do transporte e as credenciais de mensagem](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices, capítulo 3: segurança de camada de transporte de implementação e de mensagem](https://go.microsoft.com/fwlink/?LinkId=88897)
