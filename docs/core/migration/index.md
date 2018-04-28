---
title: Migração do .NET Core para o formato csproj
description: Migração do project.json para o csproj do .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 102b875072ed77a328bdb6a62ed6cc98612ff059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migrando projetos do .NET Core no formato .csproj

Este documento abrange cenários de migração para projetos do .NET Core e examina os três seguintes cenários de migração:

1. [Migração de um esquema válido mais recente do *project.json* para o *csproj*](#migration-from-projectjson-to-csproj)
2. [Migração do DNX para o csproj](#migration-from-dnx-to-csproj)
3. [Migração do RC3 e de projetos csproj anteriores do .NET Core para o formato final](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migração do project.json para o csproj
A migração do *project.json* para o *.csproj* pode ser feita usando um dos seguintes métodos:

- [Visual Studio 2017](#visual-studio-2017)
- [ferramenta de linha de comando de migração do dotnet](#dotnet-migrate)
 
Ambos os métodos usam o mesmo mecanismo subjacente para migrar os projetos. Portanto, os resultados serão os mesmos. Na maioria dos casos, o uso de uma destas duas maneiras para migrar o *project.json* para o *csproj* é a única coisa exigida e nenhuma edição manual adicional do arquivo de projeto é necessária. O arquivo *.csproj* resultante terá o mesmo nome que o diretório contido.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Quando você abre um arquivo *.xproj* ou uma solução que faz referência a arquivos *.xproj*, a caixa de diálogo **Atualização unidirecional** aparece. A caixa de diálogo exibe os projetos a serem migrados. Se você abrir um arquivo de solução, todos os projetos especificados no arquivo de solução serão listados. Examine a lista de projetos a serem migrados e selecione **OK**.

![Caixa de diálogo Atualização unidirecional mostrando a lista de projetos que serão migrados](media/one-way-upgrade.jpg)

O Visual Studio migrará os projetos escolhidos automaticamente. Ao migrar uma solução, se você não escolher todos os projetos, a mesma caixa de diálogo será exibida solicitando que você atualize os projetos restantes da solução. Depois que o projeto é migrado, é possível ver e modificar seus conteúdos clicando com o botão direito no projeto na janela do **Gerenciador de Soluções** e selecionando **Editar \<nome do projeto>. csproj**.

Os arquivos que foram migrados (*project.json*, *global.json*, *.xproj* e o arquivo de solução) serão movidos para uma pasta de *Backup*. O arquivo de solução que foi migrado será atualizado para o Visual Studio 2017 e você não poderá abrir esse arquivo de solução em versões anteriores do Visual Studio. Um arquivo chamado *UpgradeLog.htm* também será salvo e aberto automaticamente. Ele contém um relatório de migração.

> [!IMPORTANT]
> As novas ferramentas não estão disponível no Visual Studio 2015. Portanto, você não pode migrar seus projetos usando essa versão do Visual Studio.

### <a name="dotnet-migrate"></a>dotnet migrate

No cenário da linha de comando, você pode usar o comando [`dotnet migrate`](../tools/dotnet-migrate.md). Ele migrará um projeto, uma solução ou um conjunto de pastas em uma determinada ordem, dependendo em qual eles foram encontrados. Ao migrar um projeto, o projeto e todas as suas dependências são migrados.

Os arquivos que foram migrados (*project.json*, *global.json* e *.xproj*) serão movidos para uma pasta de *Backup*.

> [!NOTE]
> Se estiver usando o Visual Studio Code, o comando `dotnet migrate` não modificará arquivos específicos do Visual Studio Code, como `tasks.json`. Esses arquivos precisam ser alterados manualmente. Isso também será verdadeiro se você estiver usando o Project Ryder ou qualquer editor ou IDE (ambiente de desenvolvimento integrado) diferente do Visual Studio. 

Consulte [Um mapeamento entre as propriedades project.json e csproj](../tools/project-json-to-csproj.md) para obter uma comparação dos formatos project.json e csproj.

### <a name="common-issues"></a>Problemas comuns

- Se houver um erro: "Nenhum executável encontrado corresponde ao comando dotnet-migrate":

Execute `dotnet --version` para ver qual versão você está usando. [`dotnet migrate`](../tools/dotnet-migrate.md) requer o .NET Core CLI RC3 ou superior.
Esse erro ocorrerá se você tiver um arquivo *global.json* no diretório atual ou pai e se a versão `sdk` estiver definida como uma versão mais antiga.

## <a name="migration-from-dnx-to-csproj"></a>Migração do DNX para o csproj
Se você ainda estiver usando o DNX para desenvolvimento no .NET Core, o processo de migração deverá ser feito em dois estágios:

1. Use as [diretrizes de migração existentes do DNX](from-dnx.md) para migrar do DNX para a CLI habilitada para project-json.
2. Siga as etapas da seção anterior para migrar do *project.json* para o *.csproj*.  

> [!NOTE]
> O DNX foi preterido oficialmente durante a versão Visualização 1 da CLI do .NET Core. 

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migração de formatos csproj anteriores do .NET Core para o csproj do RTM
O formato csproj do .NET Core foi mudando e evoluindo com cada nova versão de pré-lançamento da ferramenta. Não há nenhuma ferramenta que migrará seu arquivo de projeto de versões anteriores do csproj para a versão mais recente. Sendo assim, você precisa editar manualmente o arquivo de projeto. As etapas reais dependem da versão do arquivo de projeto que você está migrando. A seguir, há algumas diretrizes para serem consideradas com base nas alterações que ocorreram entre as versões:

* Remova a propriedade de versão das ferramentas do elemento `<Project>`, se ele existir. 
* Remova o namespace de XML (`xmlns`) do elemento `<Project>`.
* Se ele não existir, adicione o atributo `Sdk` ao elemento `<Project>` e defina-o como `Microsoft.NET.Sdk` ou `Microsoft.NET.Sdk.Web`. Esse atributo especifica que o projeto usa o SDK que será utilizado. `Microsoft.NET.Sdk.Web` é usado em aplicativos Web.
* Remova as instruções `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` e `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` da parte superior e inferior do projeto. Essas instruções estão implícitas no SDK. Portanto, não é necessário que elas estejam no projeto. 
* Se os itens `Microsoft.NETCore.App` ou `NETStandard.Library` `<PackageReference>` estiverem em seu projeto, você deverá removê-los. Essas referências do pacote estão [implícitas no SDK](https://aka.ms/sdkimplicitrefs). 
* Remova o elemento `Microsoft.NET.Sdk` `<PackageReference>`, se ele existir. A referência do SDK é fornecida por meio do atributo `Sdk` no elemento `<Project>`. 
* Remova os [globs](https://en.wikipedia.org/wiki/Glob_(programming)) que estão [implícitos no SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Deixar esses globs em seu projeto causará um erro no build, uma vez que os itens de compilação serão duplicados. 

Após essas etapas, seu projeto deverá estar totalmente compatível com o formato csproj do RTM .NET Core. 

Para obter exemplos de antes e depois da migração do formato csproj antigo para o novo, consulte o artigo [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (Atualizando o Visual Studio 2017 RC – melhorias na ferramenta .NET Core) no blog do .NET.

## <a name="see-also"></a>Consulte também
[Portar, migrar e atualizar projetos do Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
