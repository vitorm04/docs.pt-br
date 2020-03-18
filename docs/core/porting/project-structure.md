---
title: Organizar projetos do .NET Framework e .NET Core
description: Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777329"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organize seu projeto para oferecer suporte ao .NET Framework e ao .NET Core

Você pode criar uma solução que compila tanto para o .NET Framework quanto para o .NET Core lado a lado. Este artigo abrange várias opções de organização de projetos para ajudá-lo a alcançar esse objetivo. Aqui estão alguns cenários típicos a considerar quando você está decidindo como configurar seu layout de projeto com o .NET Core. A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.

- [**Combinar projetos existentes e projetos do .NET Core em um mesmo projeto**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Isso é bom para:*
  - Simplifica seu processo de compilação compilando um único projeto em vez de vários projetos que cada um tem como alvo uma versão ou plataforma diferente do .NET Framework.
  - Simplifica o gerenciamento de arquivos de origem para projetos multidirecionados porque você deve gerenciar um único arquivo de projeto. Ao adicionar ou remover arquivos de origem, as alternativas exigem que você os sincronize manualmente com seus outros projetos.
  - Gere facilmente um pacote NuGet para consumo.
  - Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.

  *Cenários sem suporte:*
  - Requer que os desenvolvedores usem o Visual Studio 2017 ou uma versão posterior para abrir projetos existentes. Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.

- <a name="support-vs"></a>[**Manter os projetos existentes e os novos projetos do .NET Core separados**](#keep-existing-projects-and-create-a-net-core-project)

  *Isso é bom para:*
  - Suporta o desenvolvimento de projetos existentes para desenvolvedores e colaboradores que podem não ter o Visual Studio 2017 ou uma versão posterior.
  - Diminui a possibilidade de criação de novos bugs em projetos existentes porque não é necessário churn de código nesses projetos.

## <a name="example"></a>Exemplo

Considere o repositório abaixo:

![Projeto existente](./media/project-structure/existing-project-structure.png)

[**Código Fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Substituir os projetos existentes por um projeto multiplataforma do .NET Core

Reorganize o repositório para que quaisquer arquivos * \*.csproj* existentes sejam removidos e um único * \*arquivo .csproj* seja criado que seja direcionado a várias frameworks. Esta é uma ótima opção, porque um único projeto é capaz de compilar para diferentes frameworks. Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.

![Criar um csproj direcionado a várias estruturas](./media/project-structure/multi-targeted-project.png)

[**Código Fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Observe as seguintes alterações:

- Substituição de *packages.config* e *\*.csproj* por um novo [*\*.csproj* do .NET Core](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Manter projetos existentes e criar um projeto do .NET Core

Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.

![Projeto do .NET Core com um projeto existente em uma pasta diferente](./media/project-structure/separate-projects-same-source.png)

[**Código Fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

O .NET Core e projetos existentes são mantidos em pastas separadas. Manter projetos em pastas separadas evita forçá-lo a ter versões visual studio 2017 ou posteriores. Você pode criar uma solução separada que abre somente os projetos antigos.

## <a name="see-also"></a>Confira também

- [.NET Core portando documentação](index.md)
