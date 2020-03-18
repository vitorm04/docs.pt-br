---
title: Por que recomendamos gRPC para desenvolvedores WCF - gRPC para desenvolvedores WCF
description: Uma discussão sobre por que o gRPC é um bom ajuste para desenvolvedores WCF que querem migrar para arquiteturas e plataformas modernas.
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147640"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Por que recomendamos o gRPC para desenvolvedores do WCF

Antes de mergulharmos profundamente na linguagem e técnicas do gRPC, vale a pena discutir por que o gRPC é a solução certa para desenvolvedores da Windows Communication Foundation (WCF) que querem migrar para o .NET Core.

## <a name="similarity-to-wcf"></a>Semelhança com WCF

Embora a implementação e a abordagem sejam diferentes para o gRPC, a experiência de desenvolver e consumir serviços com gRPC deve ser intuitiva para os desenvolvedores do WCF. O objetivo subjacente é o mesmo: tornar possível o código como se o cliente e o servidor estiverem na mesma plataforma, sem precisar se preocupar com a rede.

Ambas as plataformas compartilham o princípio de declarar e, em seguida, implementar uma interface, mesmo que o processo para declarar essa interface seja diferente. E como você verá no capítulo 5, os diferentes tipos de chamadas de RPC que o gRPC suporta bem o mapa para as vinculações disponíveis para serviços WCF.

## <a name="benefits-of-grpc"></a>Benefícios do gRPC

o gRPC está acima de outras soluções pelas seguintes razões.

### <a name="performance"></a>Desempenho

O uso de HTTP/2 em vez de HTTP/1.1 remove o requisito para mensagens leíveis por humanos e, em vez disso, usa o protocolo binário menor e mais rápido. Isso é mais eficiente para os computadores analisarem. O HTTP/2 também suporta solicitações de multiplexação em uma única conexão. Esse suporte permite que as respostas sejam enviadas assim que estiverem prontas sem a necessidade de esperar em uma fila. (Em HTTP/1.1, este problema é conhecido como "bloqueio de cabeça de linha (HOL).") Você precisa de menos recursos ao usar o gRPC, o que o torna uma boa solução para usar para dispositivos móveis e sobre redes mais lentas.

### <a name="interoperability"></a>Interoperabilidade

Existem ferramentas e bibliotecas gRPC para todas as principais linguagens e plataformas de programação, incluindo .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby e PHP. Graças ao formato de fio binário Protocol Buffers e à geração eficiente de código para cada plataforma, os desenvolvedores podem criar aplicativos performáticos enquanto ainda desfrutam de suporte multiplataforma completo.

### <a name="usability-and-productivity"></a>Usabilidade e produtividade

gRPC é uma solução Abrangente de RPC. Funciona consistentemente em vários idiomas e plataformas. Ele também fornece excelentes ferramentas, com grande parte do código necessário da caldeira gerada automaticamente. Assim, mais tempo de desenvolvedor é liberado para se concentrar na lógica de negócios.

### <a name="streaming"></a>Streaming

O gRPC tem streaming bidirecional completo, que fornece funcionalidade semelhante aos serviços duplex completos do WCF. O streaming gRPC pode operar através de conexões regulares de internet, balanceadores de carga e redes de serviço.

### <a name="deadlinetimeouts-and-cancellation"></a>Prazos/intervalos e cancelamento

o gRPC permite que os clientes especifiquem um tempo máximo para que um RPC termine. Se o prazo especificado for excedido, o servidor poderá cancelar a operação independentemente do cliente. Prazos e cancelamentos podem ser propagados através de novas chamadas gRPC para ajudar a impor limites de uso de recursos. Os clientes também podem interromper as operações quando um prazo é excedido, ou mais cedo, se necessário (por exemplo, por causa de uma interação do usuário).

### <a name="security"></a>Segurança

O gRPC é implicitamente seguro quando está usando HTTP/2 em uma conexão criptografada de ponta a ponta TLS. O suporte para autenticação de certificadode cliente (ver [capítulo 6](security.md)) aumenta ainda mais a segurança e a confiança entre cliente e servidor.

>[!div class="step-by-step"]
>[Próximo](network-protocols.md)
>[anterior](protocol-buffers.md)
