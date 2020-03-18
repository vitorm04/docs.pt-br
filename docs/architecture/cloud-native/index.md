---
title: Arquitetando aplicações nativas da nuvem .NET para azure
description: Um guia para a construção de aplicativos nativos da nuvem aproveitando contêineres, microsserviços e recursos sem servidor do Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696785"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Arquitetando aplicações nativas da nuvem .NET para azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![imagem da capa](./media/cover.png)

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019, Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste livro, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

O logotipo da baleia Docker é uma marca registrada da Docker, Inc. Usada por permissão.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autores:

> **Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)

Participantes e Revisores:

> **Cesar De la Torre**, Principal Gerente de Programa, Equipe .NET, Microsoft
>
> **Nish Anil**, Gerente de Programa Sênior, Equipe .NET, Microsoft

Editores:

> **Maira Wenzel**, Sr. Content Developer, equipe .NET, Microsoft

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

O público-alvo deste guia é principalmente desenvolvedores, leads de desenvolvimento e arquitetos interessados em aprender a construir aplicativos projetados para a nuvem.

Um público secundário são os tomadores de decisão técnicos que planejam escolher se devem construir seus aplicativos usando uma abordagem nativa da nuvem.

## <a name="how-you-can-use-this-guide"></a>Como você pode usar este guia

Este guia começa definindo o nativo da nuvem e introduzindo um aplicativo de referência construído usando princípios e tecnologias nativas da nuvem. Além desses dois primeiros capítulos, o resto do livro é dividido em capítulos específicos focados em tópicos comuns à maioria dos aplicativos nativos da nuvem. Você pode pular para qualquer um desses capítulos para aprender sobre abordagens nativas da nuvem para:

- Acesso a dados e dados
- Padrões de comunicação
- Dimensionamento e escalabilidade
- Resiliência de aplicativos
- Monitoramento e integridade
- Identidade e segurança
- DevOps

Este guia está disponível tanto em formato PDF quanto online. Sinta-se livre para encaminhar este documento ou links para sua versão on-line para sua equipe para ajudar a garantir a compreensão comum desses tópicos. A maioria desses tópicos se beneficia de uma compreensão consistente dos princípios e padrões subjacentes, bem como das compensações envolvidas nas decisões relacionadas a esses tópicos. Nosso objetivo com este documento é equipar as equipes e seus líderes com as informações necessárias para tomar decisões bem informadas para a arquitetura, desenvolvimento e hospedagem de seus aplicativos.

>[!div class="step-by-step"]
>[Avançar](introduction.md)
