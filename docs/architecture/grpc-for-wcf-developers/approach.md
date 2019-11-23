---
title: Como o gRPC se aproxima de RPC-gRPC para desenvolvedores do WCF
description: Comparando os principais recursos do WCF para o gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ebfd102217c9685c5ff5200386c642b2017e98f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968126"
---
# <a name="how-grpc-approaches-rpc"></a>Como o gRPC aborda o RPC

Windows Communication Foundation (WCF) e gRPC são implementações do padrão RPC ( *chamada de procedimento remoto* ), que visa fazer chamadas para os serviços em execução em um computador diferente ou em um processo diferente, como se fossem apenas chamadas de método no aplicativo cliente. Embora os objetivos do WCF e do gRPC sejam os mesmos, os detalhes da implementação são bastante diferentes.

A tabela a seguir define como os principais recursos do WCF se relacionam com o gRPC e onde você pode encontrar explicações mais detalhadas no restante do livro.

| Recursos | WCF | gRPC |
| -------- | --- | ---- |
| Objetivo | Separar código comercial da implementação de rede | Separe o código comercial da definição de interface e da implementação de rede |
| Definir serviços e mensagens (capítulo 3-4)  | Contrato de serviço, contrato de operação e contrato de dados | Usa o arquivo proto para declarar serviços e mensagens |
| Idioma (capítulo 3-5) | Contratos escritos no C# ou Visual Basic | Idioma do buffer de protocolo |
| Formato de conexão (capítulo 3) | Configurável, incluindo SOAP/XML, XML simples, JSON, binário do .NET e assim por diante. | Formato binário de buffer de protocolo (embora seja possível usar outros formatos).
| Interoperabilidade (capítulo 4) | Ao usar SOAP sobre HTTP | Suporte oficial: .NET, Java, Python, JavaScript, C/C++, go, Rust, Ruby, Swift, Dart, php. Suporte não oficial para outros idiomas da Comunidade. |
| Rede (capítulo 4) | Configurado em tempo de execução. Alterne entre NetTCP, HTTP, MSMQ e assim por diante. | HTTP/2, atualmente sobre TCP somente com ASP.NET Core gRPC. |
| Abordagem (capítulo 4) | Geração de tempo de execução de/Deserialization de serialização e código de rede em classes base | Geração de tempo de compilação de/Deserialization de serialização e código de rede em classes base |
| Segurança (capítulo 6) | Autenticação, WS-Security, criptografia de mensagem | Credenciais, segurança de ASP.NET Core, rede TLS |

>[!div class="step-by-step"]
>[Anterior](grpc-overview.md)
>[Próximo](interface-definition-language.md)
