---
title: Como o gRPC se aproxima de RPC-gRPC para desenvolvedores do WCF
description: Comparando os principais recursos do WCF para o gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711487"
---
# <a name="how-grpc-approaches-rpc"></a>Como o gRPC aborda o RPC

Windows Communication Foundation (WCF) e gRPC são implementações do padrão RPC ( *chamada de procedimento remoto* ). Esse padrão tem como objetivo fazer chamadas para serviços executados em um computador diferente, ou em um processo diferente, trabalhar de forma direta, como chamadas de método no aplicativo cliente. Embora os objetivos do WCF e do gRPC sejam os mesmos, os detalhes da implementação são bastante diferentes.

A tabela a seguir define como os principais recursos do WCF se relacionam com o gRPC e onde você pode encontrar explicações mais detalhadas.

| Recursos | WCF | gRPC |
| -------- | --- | ---- |
| Objetivo | Separe o código comercial da implementação de rede. | Separe o código comercial da definição de interface e da implementação de rede. |
| Definir serviços e mensagens (capítulos 3-4)  | Contrato de serviço, contrato de operação e contrato de dados. | Usa o arquivo proto para declarar serviços e mensagens. |
| Idioma (capítulos 3-5) | Contratos escritos no C# ou Visual Basic. | Idioma do buffer de protocolo. |
| Formato de conexão (capítulo 3) | Configurável, incluindo SOAP/XML, XML simples, JSON e binário do .NET. | Formato binário de buffer de protocolo (embora seja possível usar outros formatos).
| Interoperabilidade (capítulo 4) | Ao usar SOAP sobre HTTP. | Suporte oficial: .NET, Java, Python, JavaScript, C/C++, go, Rust, Ruby, Swift, Dart, php. Suporte não oficial para outros idiomas da Comunidade. |
| Rede (capítulo 4) | Configurado em tempo de execução. Alterne entre NetTCP, HTTP e MSMQ. | HTTP/2, atualmente sobre TCP somente com ASP.NET Core gRPC. |
| Abordagem (capítulo 4) | Geração de tempo de execução de serialização, desserialização e código de rede em classes base. | Geração de tempo de compilação de serialização, desserialização e código de rede em classes base. |
| Segurança (capítulo 6) | Autenticação, WS-Security, criptografia de mensagem. | Credenciais, ASP.NET Core segurança, rede TLS. |

>[!div class="step-by-step"]
>[Anterior](grpc-overview.md)
>[Próximo](interface-definition-language.md)
