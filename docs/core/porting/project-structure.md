---
title: Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core
description: Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core
keywords: .NET, .NET Core
author: conniey
ms.author: mairaw
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
translationtype: Human Translation
ms.sourcegitcommit: 405bac1faa446687a4acdcf2d5536ee31f31f246
ms.openlocfilehash: b86693b1d6eed0ff5b8d1831e324354241f29806
ms.lasthandoff: 03/15/2017

---

# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core

> [!WARNING]
> Este tópico ainda não foi atualizado para a última versão das ferramentas.

Este artigo tem por objetivo ajudar os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.  Ele fornece várias opções para organizar projetos para ajudar os desenvolvedores a atingirem esse objetivo.  Esses são alguns cenários típicos que você deve considerar ao decidir como configurar o layout de projeto com o .NET Core.  Eles podem não abordar tudo o que você deseja, por isso priorize dependendo das necessidades do seu projeto.

* [**Combinar projetos existentes e do .NET Core em um mesmo projeto**][option-xproj]
  
  *Isso é bom para:*
  * Simplificar o processo de compilação ao compilar um único projeto em vez de vários, cada um direcionado para uma versão ou plataforma diferente do .NET Framework.
  * Simplificar o gerenciamento de arquivos de origem para projetos multiplataforma, pois é necessário gerenciar apenas um único arquivo de projeto.  Ao adicionar/remover arquivos da origem, as alternativas exigem que você sincronize manualmente esses recursos com outros projetos.
  * Fácil geração de um pacote NuGet para consumo.
  * Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.
  
  *Cenários sem suporte:*
  * Não permite que os desenvolvedores sem o Visual Studio 2015 abram projetos existentes. Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.
  * Não permite o compartilhamento de biblioteca do .NET Core entre diferentes tipos de projeto no mesmo arquivo de solução. Para dar suporte a isso, [criar uma Biblioteca de Classes Portátil](#support-pcl) é uma opção melhor.
  * Não permite a compilação do projeto ou carregamento de modificações com suporte em Destinos e Tarefas do MSBuild. Para dar suporte a isso, [criar uma Biblioteca de Classes Portátil](#support-pcl) é uma opção melhor.

* <a name="support-vs"></a>[**Manter projetos existentes e novos projetos do .NET Core separados**][option-xproj-folder]
  
  *Isso é bom para:*
  * Continuar a dar suporte ao desenvolvimento em projetos existentes sem a necessidade de atualizar para os desenvolvedores/colaboradores que podem não ter o Visual Studio 2015.
  * Diminuir a possibilidade de criar novos bugs em projetos existentes, porque nenhuma variação de código é necessária nesses projetos.

* <a name="support-pcl"></a>[**Manter projetos existentes e criar PCLs (Bibliotecas de Classes Portáteis) direcionadas para .NET Core**][option-pcl]

  *Isso é bom para:*
  * Fazer referência às bibliotecas .NET Core em projetos de área de trabalho e/ou da Web direcionado para o .NET Framework completo na mesma solução.
  * Dar suporte a modificações no build do projeto ou processo de carregamento. Essas modificações poderiam ser a inclusão de Tarefas e Destinos do MSBuild no seu arquivo `*.csproj`.

  *Cenários sem suporte:*
  * Não permite que você escreva código para uma versão específica do .NET Framework porque os [símbolos pré-processador predefinidos][how-to-multitarget] não têm suporte.

## <a name="example"></a>Exemplo

Considere o repositório abaixo:

![Projeto existente][example-initial-project]

[**Código-fonte**][example-initial-project-code]

Há várias maneiras diferentes de adicionar suporte ao .NET Core para este repositório dependendo das restrições e da complexidade dos projetos existentes, as quais são descritas abaixo.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project-xproj"></a>Substitua os projetos existentes por um projeto multiplataforma do .NET Core (xproj)

O repositório pode ser reorganizado de forma que qualquer arquivo existente `*.csproj` seja removido e um único arquivo `*.xproj` seja criado, sendo direcionado a diversas estruturas.  Essa é uma ótima opção, pois um único projeto é capaz de ser compilado para estruturas diferentes.  Ele também tem a capacidade de lidar com diferentes opções de compilação, dependências, etc. por estrutura de destino.

![Criar um xproj direcionado a várias estruturas][example-xproj]

[**Código-fonte**][example-xproj-code]

Observe as seguintes alterações:
* Adição de `global.json`
* Substituição de `packages.config` e `*.csproj` por `project.json` e `*.xproj`
* Alterações no [Car's project.json][example-xproj-projectjson] e seu [projeto de teste][example-xproj-projectjson-test] para compilação de suporte para o .NET Framework existente e para outros

## <a name="create-a-portable-class-library-pcl-to-target-net-core"></a>Criar uma PCL (Biblioteca de Classes Portátil) direcionada para o .NET Core

Se os projetos existentes contiverem operações complexas de build ou propriedades em seus arquivos `*.csproj`, poderá ser mais fácil criar uma PCL.

![][example-pcl]

[**Código-fonte**][example-pcl-code]

Observe as seguintes alterações:
*  Renomeando `project.json` para `{project-name}.project.json`
    * Isso impede conflitos em potencial no Visual Studio ao tentar restaurar pacotes para as bibliotecas no mesmo diretório. Para obter mais informações, consulte as [Perguntas Frequentes sobre NuGet](https://docs.nuget.org/consume/nuget-faq#working-with-packages) em "_Tenho vários projetos na mesma pasta, como posso usar arquivos packages.config ou project.json separados para cada projeto?_".
    *  **Alternativa**: crie a PCL em outra pasta e faça referência ao código-fonte original para evitar esse problema.  Colocar a PCL em outra pasta traz ainda um benefício adicional de os usuários que não têm o Visual Studio 2015 ainda poderem trabalhar nos projetos mais antigos sem carregar a nova solução.
*  Para direcionar para o .NET Standard depois de criar a PCL no Visual Studio, abra as **Propriedades do Projeto**. Na seção **Destinos**, clique no link **"Direcionar para o .NET Platform Standard"**.  Essa alteração pode ser revertida repetindo as mesmas etapas.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Manter projetos existentes e criar um projeto do .NET Core

Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.

![Projeto .NET Core com PCL existente em uma pasta diferente][example-xproj-different-folder]

[**Código-fonte**][example-xproj-different-code]

Observe as seguintes alterações:
* O .NET Core e projetos existentes são mantidos em pastas separadas.
    * Isso evita o problema de restauração de pacote que foi mencionado acima devido à presença de vários arquivos project.json/package.config na mesma pasta.
    * Manter projetos em pastas separadas evita a necessidade de ter o Visual Studio 2015 (devido ao project.json).  Você pode criar uma solução separada que abre somente os projetos antigos.

## <a name="see-also"></a>Consulte também

Consulte a [Documentação de portabilidade do .NET Core][porting-doc] para ver as diretrizes para migrar para o project.json e xproj.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projeto existente"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-xproj]: media/project-structure/project.xproj.png "Criar um xproj direcionado a várias estruturas"
[example-xproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/
[example-xproj-projectjson]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/src/Car/project.json
[example-xproj-projectjson-test]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/tests/Car.Tests/project.json

[example-xproj-different-folder]: media/project-structure/project.xproj.different.png "Projeto .NET Core com PCL existente em uma pasta diferente"
[example-xproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj-keep-csproj/

[example-pcl]: media/project-structure/project.pcl.png "PCL direcionada a .NET Core"
[example-pcl-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-pcl

[option-xproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project-xproj
[option-pcl]: #create-a-portable-class-library-pcl-to-target-net-core
[option-xproj-folder]: #keep-existing-projects-and-create-a-net-core-project

[how-to-multitarget]: ../tutorials/libraries.md#how-to-multitarget

