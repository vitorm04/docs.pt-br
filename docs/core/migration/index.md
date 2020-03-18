---
title: Migração do .NET Core com project.json
description: Saiba como migrar um projeto .NET Core mais antigo usando project.json
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77450681"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migração de projetos do .NET Core com project.json

Este documento abrange os seguintes três cenários de migração para projetos .NET Core:

1. [Migração de um esquema válido mais recente do *project.json* para o *csproj*](#migration-from-projectjson-to-csproj)
2. [Migração do DNX para o csproj](#migration-from-dnx-to-csproj)
3. [Migração do RC3 e de projetos csproj anteriores do .NET Core para o formato final](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Este documento só é aplicável a projetos mais antigos do .NET Core que usam project.json. Não se aplica à migração do .NET Framework para .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migração do project.json para o csproj

A migração do *project.json* para o *.csproj* pode ser feita usando um dos seguintes métodos:

- [Estúdio Visual](#visual-studio)
- [ferramenta de linha de comando de migração do dotnet](#dotnet-migrate)

Ambos os métodos usam o mesmo mecanismo subjacente para migrar os projetos. Portanto, os resultados serão os mesmos. Na maioria dos casos, usar uma dessas duas maneiras de migrar o *projeto.json* para *csproj* é a única coisa necessária, e nenhuma edição manual adicional do arquivo do projeto é necessária. O arquivo *.csproj* resultante terá o mesmo nome que o diretório contido.

### <a name="visual-studio"></a>Visual Studio

Quando você abre um arquivo *.xproj* ou um arquivo de solução que faz referência a arquivos *.xproj* no Visual Studio 2017 ou visual Studio 2019 versão 16.2 e anterior, a caixa **de diálogo de atualização unidirecional** aparece. A caixa de diálogo exibe os projetos a serem migrados. Se você abrir um arquivo de solução, todos os projetos especificados no arquivo de solução serão listados. Examine a lista de projetos a serem migrados e selecione **OK**.

![Caixa de diálogo Atualização unidirecional mostrando a lista de projetos que serão migrados](media/one-way-upgrade.jpg)

O Visual Studio migra automaticamente os projetos selecionados. Ao migrar uma solução, se você não escolher todos os projetos, o mesmo diálogo aparece pedindo que você atualize os projetos restantes dessa solução. Depois que o projeto é migrado, é possível ver e modificar seus conteúdos clicando com o botão direito no projeto na janela do **Gerenciador de Soluções** e selecionando **Editar \<nome do projeto>. csproj**.

Os arquivos que foram migrados (*project.json,* *global.json,* *.xproj*e arquivo de solução) são movidos para uma pasta *backup.* O arquivo de solução migrado é atualizado para o Visual Studio 2017 ou Visual Studio 2019 e você não poderá abrir esse arquivo de solução no Visual Studio 2015 ou nas versões anteriores. Um arquivo chamado *UpgradeLog.htm* que contém um relatório de migração também é salvo e aberto automaticamente.

> [!IMPORTANT]
> No Visual Studio 2019 versão 16.3 e posterior, você não pode carregar ou migrar um arquivo *.xproj.* Além disso, o Visual Studio 2015 não fornece a capacidade de migrar um arquivo *.xproj.* Se você estiver usando uma dessas versões do Visual Studio, instale uma versão adequada do Visual Studio ou use a ferramenta de migração de linha de comando descrita a seguir.

### <a name="dotnet-migrate"></a>dotnet migrate

No cenário de linha de comando, você pode usar o [`dotnet migrate`](../tools/dotnet-migrate.md) comando. Ele migra um projeto, uma solução ou um conjunto de pastas nessa ordem, dependendo de quais foram encontradas. Ao migrar um projeto, o projeto e todas as suas dependências são migrados.

Os arquivos que foram migrados (*project.json*, *global.json*e *.xproj*) são movidos para uma pasta *de backup.*

> [!NOTE]
> Se você estiver usando o `dotnet migrate` Visual Studio Code, o comando não modifica arquivos específicos do Visual Studio Code, como *tasks.json*. Esses arquivos precisam ser alterados manualmente.
> Isso também é verdade se você estiver usando um editor ou Ambiente de Desenvolvimento Integrado (IDE) diferente do Visual Studio.

Consulte [Um mapeamento entre as propriedades project.json e csproj](../tools/project-json-to-csproj.md) para uma comparação dos formatos *project.json* e *.csproj.*

Se houver um erro:

> Nenhum executável encontrado correspondente comando dotnet-migrar

Execute `dotnet --version` para ver qual versão você está usando. [`dotnet migrate`](../tools/dotnet-migrate.md)foi introduzido no .NET Core SDK 1.0.0 e removido na versão 3.0.100.
Você obterá esse erro se tiver um arquivo *global.json* no diretório `sdk` atual ou pai, e a versão especificada está fora deste intervalo.

## <a name="migration-from-dnx-to-csproj"></a>Migração do DNX para o csproj

Se você ainda estiver usando o DNX para desenvolvimento no .NET Core, o processo de migração deverá ser feito em dois estágios:

1. Use as [diretrizes de migração existentes do DNX](from-dnx.md) para migrar do DNX para a CLI habilitada para project-json.
2. Siga as etapas da seção anterior para migrar do *project.json* para o *.csproj*.

> [!NOTE]
> O DNX foi preterido oficialmente durante a versão Visualização 1 da CLI do .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migração de formatos csproj anteriores do .NET Core para o csproj do RTM

O formato csproj do .NET Core foi mudando e evoluindo com cada nova versão de pré-lançamento da ferramenta. Não há nenhuma ferramenta que migrará seu arquivo de projeto de versões anteriores do csproj para a versão mais recente. Sendo assim, você precisa editar manualmente o arquivo de projeto. As etapas reais dependem da versão do arquivo de projeto que você está migrando. A seguir, há algumas diretrizes para serem consideradas com base nas alterações que ocorreram entre as versões:

- Remova a propriedade de versão das ferramentas do elemento `<Project>`, se ele existir.
- Remova o namespace de XML (`xmlns`) do elemento `<Project>`.
- Se ele não existir, adicione o atributo `Sdk` ao elemento `<Project>` e defina-o como `Microsoft.NET.Sdk` ou `Microsoft.NET.Sdk.Web`. Esse atributo especifica que o projeto usa o SDK que será utilizado. `Microsoft.NET.Sdk.Web` é usado em aplicativos Web.
- Remova as instruções `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` e `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` da parte superior e inferior do projeto. Essas instruções estão implícitas no SDK. Portanto, não é necessário que elas estejam no projeto.
- Se você `Microsoft.NETCore.App` `NETStandard.Library` `<PackageReference>` tiver ou itens em seu projeto, você deve removê-los. Essas referências do pacote estão [implícitas no SDK](https://aka.ms/sdkimplicitrefs).
- Remova `Microsoft.NET.Sdk` `<PackageReference>` o elemento, se ele existir. A referência do SDK é fornecida por meio do atributo `Sdk` no elemento `<Project>`.
- Remova os [globs](https://en.wikipedia.org/wiki/Glob_(programming)) que estão [implícitos pelo SDK](../project-sdk/overview.md#default-compilation-includes). Deixar esses globs em seu projeto causará um erro no build, uma vez que os itens de compilação serão duplicados.

Após essas etapas, seu projeto deverá estar totalmente compatível com o formato csproj do RTM .NET Core.

Para obter exemplos de antes e depois da migração do formato csproj antigo para o novo, consulte o artigo [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (Atualizando o Visual Studio 2017 RC – melhorias na ferramenta .NET Core) no blog do .NET.

## <a name="see-also"></a>Confira também

- [Portar, migrar e atualizar projetos do Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
