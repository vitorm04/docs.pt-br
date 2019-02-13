---
title: Organizar projetos do .NET Framework e .NET Core
description: Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 57bb766f1d91c502a508b6362dc642310009c8c4
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904018"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organize seu projeto para oferecer suporte ao .NET Framework e ao .NET Core

Saiba como criar uma solução compilada para .NET Framework e .NET Core simultaneamente. Veja várias opções para organizar projetos que o ajudam a atingir esse objetivo. Estes são alguns cenários típicos que você deve considerar ao decidir como configurar o layout de projeto com o .NET Core. A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.

* [**Combinar projetos existentes e projetos do .NET Core em um mesmo projeto**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Isso é bom para:*
  * Simplificar o processo de compilação ao compilar um único projeto em vez de vários, cada um direcionado para uma versão ou plataforma diferente do .NET Framework.
  * Simplificar o gerenciamento de arquivos de origem para projetos multiplataforma, pois é necessário gerenciar um único arquivo de projeto. Ao adicionar/remover arquivos da origem, as alternativas exigem que você sincronize manualmente esses recursos com outros projetos.
  * Fácil geração de um pacote NuGet para consumo.
  * Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.

  *Cenários sem suporte:*
  * Requer que os desenvolvedores usem o Visual Studio 2017 para abrir projetos existentes. Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.

* <a name="support-vs"></a>[**Manter os projetos existentes e os novos projetos do .NET Core separados**](#keep-existing-projects-and-create-a-net-core-project)

  *Isso é bom para:*
  * Continuar a dar suporte ao desenvolvimento em projetos existentes sem a necessidade de atualizar para os desenvolvedores/colaboradores que podem não ter o Visual Studio 2017.
  * Diminuir a possibilidade de criar novos bugs em projetos existentes porque nenhuma variação de código é necessária nesses projetos.

## <a name="example"></a>Exemplo

Considere o repositório abaixo:

![Projeto existente](media/project-structure/project.png)

[**Código-fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Substituir os projetos existentes por um projeto multiplataforma do .NET Core

Reorganize o repositório para que todos os arquivos *\*.csproj* existentes sejam removidos e seja criado um único arquivo *\*.csproj* direcionado a várias estruturas. Essa é uma ótima opção, pois um único projeto é capaz de ser compilado para estruturas diferentes. Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.

![Criar um csproj direcionado a várias estruturas](media/project-structure/project.csproj.png)

[**Código-fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Observe as seguintes alterações:

* Substituição de *packages.config* e *\*.csproj* por um novo [*\*.csproj* do .NET Core](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Manter projetos existentes e criar um projeto do .NET Core

Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.

![Projeto do .NET Core com um projeto existente em uma pasta diferente](media/project-structure/project.csproj.different.png)

[**Código-fonte**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Observe as seguintes alterações:

* O .NET Core e projetos existentes são mantidos em pastas separadas.
  * Manter projetos em pastas separadas evita a necessidade de ter o Visual Studio 2017. Você pode criar uma solução separada que abre somente os projetos antigos.

## <a name="see-also"></a>Consulte também

Confira a [Documentação de portabilidade do .NET Core](index.md) para obter mais diretrizes de migração para o .NET Core.
