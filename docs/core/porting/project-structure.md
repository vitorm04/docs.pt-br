---
title: Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core
description: Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.
keywords: .NET, .NET Core, .NET Framework, layout de projeto, várias estruturas
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.workload:
- dotnetcore
ms.openlocfilehash: 2392c6e477138e21dc98055fe7ecca84789f07af
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core

Este artigo ajuda os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado. Ele fornece várias opções para organizar projetos para ajudar os desenvolvedores a atingirem esse objetivo. A lista a seguir fornece alguns cenários típicos a serem considerados ao decidir como configurar o layout de projeto com o .NET Core. A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.

* [**Combinar projetos existentes e do .NET Core em um mesmo projeto**][option-csproj]

  *Isso é bom para:*
  * Simplificar o processo de compilação ao compilar um único projeto em vez de vários, cada um direcionado para uma versão ou plataforma diferente do .NET Framework.
  * Simplificar o gerenciamento de arquivos de origem para projetos multiplataforma, pois é necessário gerenciar um único arquivo de projeto. Ao adicionar/remover arquivos da origem, as alternativas exigem que você sincronize manualmente esses recursos com outros projetos.
  * Fácil geração de um pacote NuGet para consumo.
  * Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.

  *Cenários sem suporte:*
  * Requer que os desenvolvedores usem o Visual Studio 2017 para abrir projetos existentes. Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.

* <a name="support-vs"></a>[**Manter projetos existentes e novos projetos do .NET Core separados**][option-csproj-folder]

  *Isso é bom para:*
  * Continuar a dar suporte ao desenvolvimento em projetos existentes sem a necessidade de atualizar para os desenvolvedores/colaboradores que podem não ter o Visual Studio 2017.
  * Diminuir a possibilidade de criar novos bugs em projetos existentes porque nenhuma variação de código é necessária nesses projetos.

## <a name="example"></a>Exemplo

Considere o repositório abaixo:

![Projeto existente][example-initial-project]

[**Código-fonte**][example-initial-project-code]

A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Substituir os projetos existentes por um projeto multiplataforma do .NET Core

Reorganize o repositório para que todos os arquivos *\*.csproj* existentes sejam removidos e seja criado um único arquivo *\*.csproj* direcionado a várias estruturas. Essa é uma ótima opção, pois um único projeto é capaz de ser compilado para estruturas diferentes. Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.

![Criar um csproj direcionado a várias estruturas][example-csproj]

[**Código-fonte**][example-csproj-code]

Observe as seguintes alterações:
* Substituição de *packages.config* e *\*.csproj* por um novo [.NET Core *\*.csproj*][example-csproj-netcore]. Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Manter projetos existentes e criar um projeto do .NET Core

Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.

![Projeto .NET Core com um projeto existente em uma pasta diferente][example-csproj-different-folder]

[**Código-fonte**][example-csproj-different-code]

Observe as seguintes alterações:
* O .NET Core e projetos existentes são mantidos em pastas separadas.
    * Manter projetos em pastas separadas evita a necessidade de ter o Visual Studio 2017. Você pode criar uma solução separada que abre somente os projetos antigos.

## <a name="see-also"></a>Consulte também

Consulte a [Documentação de portabilidade do .NET Core][porting-doc] para obter mais diretrizes sobre a migração para o .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projeto existente"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Criar um csproj direcionado a várias estruturas"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projeto .NET Core com PCL existente em uma pasta diferente"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
