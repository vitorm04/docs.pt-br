---
title: PNRP no desenvolvimento do aplicativo
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395730"
---
# <a name="pnrp-in-application-development"></a>PNRP no desenvolvimento do aplicativo
No o Windows Vista, os aplicativos de rede podem acessar funções de publicação e de resolução de nomes por meio de uma API (interface de programação de aplicativo) PNRP simplificada.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementando o protocolo PNRP  
 Com a API PNRP simplificada, nuvens não são especificadas explicitamente para registrar o nome e endereços; o componente PNRP determina automaticamente as nuvens apropriadas ingressar e os endereços para publicar dentro delas.  
  
 Para proporcionar uma resolução de nomes PNRP simplificada no Windows Vista, os nomes PNRP agora estão integrados à função getaddrinfo() do Windows Sockets. Para usar o PNRP para solucionar um nome para um endereço IPv6, os aplicativos podem usar a função getaddrinfo() para solucionar o FQDN (nome de domínio totalmente qualificado) nome.prnp.net, no qual nome é o nome do par que está sendo resolvido. O domínio pnrp.net é um domínio reservado no Windows Vista para a resolução de nomes PNRP.  
  
 A mensagem passando entre aplicativos PeerToPeer ainda é manipulada pelo arquiteturas subjacentes, como PeerChannel e [Dados Grandes e Streaming](http://go.microsoft.com/fwlink/?LinkID=179652) de WCF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.PeerToPeer>
