---
title: Linguagem de definição de interface-gRPC para desenvolvedores do WCF
description: Apresentando os buffers de protocolo IDL.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184424"
---
# <a name="interface-definition-language"></a>Linguagem de definição de interface

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Com o WCF, os serviços podem expor metadados de descrição usando o WSDL (Web Service Definition Language), que é gerado dinamicamente usando a reflexão do .NET em tempo de execução. Os desenvolvedores podem usar esses metadados para gerar clientes para esses serviços, potencialmente em outras linguagens se uma associação de plataforma neutra, como SOAP sobre HTTP, for usada.

gRPC usa o IDL (Interface Definition Language) dos buffers de protocolo. Os buffers de protocolo IDL são uma linguagem personalizada de plataforma neutra com uma especificação aberta. Os desenvolvedores codificam `.proto` arquivos para descrever serviços junto com suas entradas e saídas. Esses `.proto` arquivos podem então ser usados para gerar stubs específicos de idioma ou de plataforma para clientes e servidores, permitindo que várias plataformas diferentes se comuniquem. Ao compartilhar `.proto` arquivos, as equipes podem gerar código para usar os serviços de cada um sem precisar usar uma dependência de código.

Uma das vantagens da Protobuf IDL é que, como uma linguagem personalizada, ela permite que o gRPC seja completamente independente de linguagem e plataforma, não favorecendo nenhuma tecnologia sobre outra.

O Protobuf IDL também é projetado para os seres humanos para leitura e gravação, enquanto o WSDL é destinado a um formato legível por máquina/gravável. A alteração do WSDL de um serviço WCF normalmente requer a realização das alterações no próprio código do serviço, na execução do serviço e na regeneração do arquivo WSDL a partir do servidor. Por outro lado, com `.proto` um arquivo, as alterações são simples de se aplicar a um editor de texto e fluir automaticamente pelo código gerado. O Visual Studio 2019 `.proto` compila arquivos em segundo plano quando eles são salvos; ao usar outros editores, como vs Code as alterações serão aplicadas quando o projeto for compilado.

Quando comparado com XML e particularmente SOAP, mensagens codificadas usando Protobuf têm muitas vantagens. As mensagens Protobuf tendem a ser menores do que os mesmos dados serializados como XML SOAP, e codificar, decodificá-los e transmiti-los por meio de uma rede podem ser mais rápidos.

A desvantagem potencial do Protobuf em comparação com o SOAP é que, como as mensagens não são legíveis, ferramentas adicionais são necessárias para depurar o conteúdo da mensagem.

> [!TIP]
> *o* gRPC oferece suporte à reflexão de servidor para acessar serviços dinamicamente sem stubs pré-compilados, embora ele seja mais destinado a ferramentas de finalidade geral do que clientes específicos do aplicativo. Para obter mais informações sobre a reflexão do gRPC Server, consulte repositório [gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) no github.

> [!NOTE]
> O formato binário do WCF, usado com a associação NetTCP, é muito mais próximo de Protobuf em termos de compactação e desempenho, mas NetTCP só é utilizável entre clientes e servidores .NET, enquanto o Protobuf é uma solução de plataforma cruzada.

>[!div class="step-by-step"]
>[Anterior](approach.md)
>[Próximo](network-protocols.md)
