---
title: Como o gRPC se aproxima de RPC-gRPC para desenvolvedores do WCF
description: Comparando os principais recursos do WCF para o gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3da28968f8c8bd6c4fdba7432ffc8458d8340457
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846694"
---
# <a name="how-grpc-approaches-rpc"></a>Como o gRPC aborda o RPC

Windows Communication Foundation (WCF) e gRPC são implementações do padrão RPC ( *chamada de procedimento remoto* ), que visa fazer chamadas para serviços em execução em um computador diferente, ou em um processo diferente, trabalhar de forma direta como se fosse apenas chamadas de método no aplicativo cliente. Embora os objetivos do WCF e do gRPC sejam os mesmos, os detalhes da implementação são bastante diferentes.

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
