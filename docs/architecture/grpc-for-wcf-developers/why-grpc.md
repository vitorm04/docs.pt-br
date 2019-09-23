---
title: Por que o gRPC é recomendado para desenvolvedores do WCF – gRPC para desenvolvedores do WCF
description: Uma discussão sobre por que o gRPC é uma boa opção para desenvolvedores do WCF que buscam migrar para arquiteturas e plataformas modernas.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7e80936eb36bbba92958c349b5f1c0cb389d6b8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184032"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>Por que o gRPC é recomendado para desenvolvedores do WCF

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Antes de se aprofundar na linguagem e nas técnicas do gRPC, vale a pena discutir por que gRPC é a solução certa para desenvolvedores de WCF que desejam migrar para o .NET Core, Considerando que há alternativas disponíveis.

## <a name="similarity-to-wcf"></a>Similaridade para o WCF

Embora sua implementação e abordagem seja diferente, a experiência real de desenvolvimento e consumo de serviços com o gRPC deve ser muito intuitiva para desenvolvedores do WCF. O objetivo subjacente de torná-lo possível codificar como se o cliente e o servidor estivessem na mesma plataforma, sem a necessidade de se preocupar com a rede, é o mesmo. Ambas as plataformas compartilham o princípio de declarar e, em seguida, implementar uma interface, mesmo que o processo para declarar essa interface seja diferente. E, como você verá no capítulo 5, os diferentes tipos de chamadas RPC com suporte do gRPC MAP muito bem para as diferentes associações disponíveis para os serviços WCF.

## <a name="benefits-of-grpc"></a>Benefícios do gRPC

Outros motivos pelos quais o gRPC está acima de outras soluções são:

### <a name="performance"></a>Desempenho

Como já abordado, o uso de HTTP/2 em vez de HTTP/1.1 elimina o requisito de mensagens legíveis e, em vez disso, usa o menor protocolo binário mais rápido. Isso é mais eficiente para os computadores analisarem. O HTTP/2 também dá suporte à multiplexação de solicitações em uma única conexão, permitindo que as respostas sejam enviadas assim que estiverem prontas, sem a necessidade de aguardar em uma fila (um problema no HTTP/1.1 conhecido como "bloqueio de linha de frente (Chol)"). Menos recursos são necessários ao usar o gRPC, o que o torna uma boa solução a ser usada para dispositivos móveis e em redes mais lentas.

### <a name="interoperability"></a>Interoperabilidade

Há ferramentas e bibliotecas de gRPC para todas as principais linguagens de programação e plataformas, incluindo .NET, Java, Python C++, go, Node. js, Swift, Dart, Ruby e php. Graças ao formato de cabo binário dos buffers de protocolo e à geração de código eficiente para cada plataforma, os desenvolvedores podem criar aplicativos de alto desempenho enquanto ainda aproveitam o suporte completo a várias plataformas.

### <a name="usability-and-productivity"></a>Usabilidade e produtividade

gRPC é uma solução RPC abrangente. Ele funciona consistentemente em várias linguagens e plataformas e fornece ferramentas excelentes, com grande parte do código clichê necessário gerado automaticamente e, portanto, mais tempo de desenvolvedor é liberado para se concentrar na lógica de negócios.

### <a name="streaming"></a>Streaming

o gRPC tem streaming bidirecional completo, que fornece funcionalidade muito semelhante aos serviços Full duplex do WCF. o streaming gRPC pode operar em conexões de Internet regulares, balanceadores de carga e malhas de serviço.

### <a name="deadlinetimeouts-and-cancellation"></a>Prazo/tempos limite e cancelamento

gRPC permite que os clientes especifiquem um tempo máximo para que um RPC seja concluído. Se o prazo especificado for excedido, o servidor poderá cancelar a operação independentemente do cliente. Os prazos finais e cancelamentos podem ser propagados por meio de chamadas gRPC adicionais para ajudar a reforçar os limites de uso de recursos. Os clientes também podem abortar operações quando um prazo é excedido ou antes, se necessário (por exemplo, devido a uma interação do usuário).

### <a name="security"></a>Segurança

o gRPC é implicitamente seguro ao usar HTTP/2 em uma conexão criptografada de ponta a ponta TLS. O suporte para autenticação de certificado de cliente (consulte o capítulo 6) aumenta ainda mais a segurança e a confiança entre o cliente e o servidor.

>[!div class="step-by-step"]
>[Anterior](network-protocols.md)
>[Próximo](protocol-buffers.md)
