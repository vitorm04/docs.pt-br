---
title: "Visão geral do SDK do .NET Core"
description: "Visão geral do SDK do .NET Core"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 5ecc2dd249ab0e1e25e2fcaa4f7548f91085e54a
ms.contentlocale: pt-br
ms.lasthandoff: 04/10/2017

---

# <a name="net-core-sdk-overview"></a>Visão geral do SDK do .NET Core 

## <a name="introduction"></a>Introdução
O SDK (Software Development Kit) do .NET Core é um conjunto de bibliotecas e ferramentas que permitem aos desenvolvedores criar bibliotecas e aplicativos do .NET Core. Este é o pacote que os desenvolvedores provavelmente adquirirão. 

Ele contém os seguintes componentes:

1. As Ferramentas de Linha de Comando do .NET Core que são usadas para criar aplicativos
2. .NET Core (bibliotecas e tempo de execução) que permitem que aplicativos sejam compilados e executados
3. O driver do `dotnet` para executar o [comandos da CLI](tools/index.md) e aplicativos


## <a name="acquiring-the-net-core-sdk"></a>Adquirindo o SDK do .NET Core
Assim como acontece com qualquer ferramenta, o primeiro passo é obtê-la no seu computador. Dependendo do seu cenário, você pode usar instaladores nativos ou o script de shell de instalação para instalar o SDK.

Instaladores nativos destinam-se principalmente a computadores do desenvolvedor. O SDK é distribuído usando o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo com pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalarão e configurarão o ambiente conforme necessário para o usuário utilizar o SDK imediatamente após a instalação. No entanto, eles também exigem privilégios administrativos no computador. Você pode exibir as instruções de instalação no [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs).

Scripts de instalação, por outro lado, não exigem privilégios administrativos. No entanto, eles também não instalarão nenhum pré-requisito no computador. Você precisa instalar todos os pré-requisitos manualmente. Os scripts destinam-se principalmente a configurar servidores de build ou para quando você deseja instalar as ferramentas sem privilégios de administrador (observe as limitações dos pré-requisitos acima). Veja mais informações no [tópico de referência do script de instalação](tools/dotnet-install-script.md). Se você estiver interessado em como configurar o SDK no seu servidor de build de CI, leia o documento [SDK com servidores de CI](tools/using-ci-with-cli.md). 

Por padrão, o SDK será instalado “lado a lado” (SxS). Isso significa que várias versões das ferramentas de CLI podem coexistir em um determinado momento em um único computador. A maneira como a versão correta é usada é explicada mais detalhadamente na [seção do driver](tools/index.md#driver) do tópico de Ferramentas de Linha de Comando do .NET Core.
