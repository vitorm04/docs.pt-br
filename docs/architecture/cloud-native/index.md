---
title: Arquitetando aplicativos .NET nativos de nuvem para o Azure
description: Um guia para a criação de aplicativos nativos de nuvem que aproveitam contêineres, microservices e recursos sem servidor do Azure.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: ebef97fb355cbf682b37ee441a19fbbfdd2d0dc3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199814"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Arquitetando aplicativos .NET nativos de nuvem para o Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![imagem da capa](./media/cover.png)

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2019 da Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste livro, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas listadas em https://www.microsoft.com na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autores:

> **Rob Vettor**, arquiteto de sistema de nuvem principal/arquiteto de IP- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft
>
> **Steve "ardalis" Smith**, arquiteto de software e instrutor- [Ardalis.com](https://ardalis.com)

Participantes e revisores:

> **Cesar de la Torre**, gerente de programa principal, equipe do .net, Microsoft
>
> **Nish Anil**, gerente de programas sênior, equipe do .net, Microsoft
>
> **Jeremy semelhança**, gerente de programas sênior, equipe do .net, Microsoft
>
> **Cecil Phillip**, defensora da nuvem sênior, Microsoft

Saiba mais sobre o eShopOnContainers

Editores:

> **Maira Wenzel**, gerente de programas, equipe do .net, Microsoft

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

O público-alvo deste guia é, principalmente, desenvolvedores, líderes de desenvolvimento e arquitetos interessados em aprender a criar aplicativos projetados para a nuvem.

Um público-alvo secundário são responsáveis pelas decisões técnicas que planejam escolher se desejam criar seus aplicativos usando uma abordagem nativa de nuvem.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Este guia começa definindo a nuvem nativa e introduzindo um aplicativo de referência criado usando princípios e tecnologias nativas de nuvem. Além desses dois primeiros capítulos, o restante do livro é dividido em capítulos específicos focados em tópicos comuns à maioria dos aplicativos nativos de nuvem. Você pode ir para qualquer um desses capítulos para saber mais sobre abordagens nativas de nuvem para:

- Dados e acesso a dados
- Padrões de comunicação
- Dimensionamento e escalabilidade
- Resiliência do aplicativo
- Monitoramento e integridade
- Identidade e segurança
- DevOps

Este guia está disponível em formato PDF e online. Fique à vontade para encaminhar este documento ou links para sua versão online para sua equipe para ajudar a garantir uma compreensão comum desses tópicos. A maioria desses tópicos se beneficia de uma compreensão consistente dos princípios e padrões subjacentes, bem como das compensações envolvidas em decisões relacionadas a esses tópicos. Nosso objetivo com este documento é equipar equipes e seus líderes com as informações de que precisam para tomar decisões bem informadas sobre a arquitetura, o desenvolvimento e a hospedagem dos seus aplicativos.

>[!div class="step-by-step"]
>[Avançar](introduction.md)
