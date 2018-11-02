---
title: Bibliotecas do NuGet e .NET
description: Recomendações de melhor prática para o empacotamento com o NuGet para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 479d1786c232ef1f843877169954e847453681c9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185609"
---
# <a name="nuget"></a>NuGet

O NuGet é um gerenciador de pacotes para o ecossistema do .NET e é a principal maneira como os desenvolvedores descobrem e adquirem bibliotecas de código-fonte aberto do .NET. O [NuGet.org](https://www.nuget.org/), um serviço gratuito fornecido pela Microsoft para hospedar pacotes do NuGet, é o host primário para os pacotes públicos do NuGet, mas você pode publicar em serviços personalizados do NuGet, como [MyGet](https://www.myget.org/) e [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Criar um pacote NuGet

Um pacote do NuGet (`*.nupkg`) é um arquivo zip que contém os assemblies do .NET e os metadados associados.

Há duas maneiras principais de criar um pacote do NuGet. A maneira recomendada e mais recente é criar um pacote de um projeto no estilo do SDK (arquivo de projeto cujo conteúdo começa com `<Project Sdk="Microsoft.NET.Sdk">`). Assemblies e destinos são automaticamente adicionados ao pacote e o restante dos metadados é adicionado ao arquivo MSBuild, como o número de versão e o nome do pacote. Compilar com o comando [`dotnet pack`](../../core/tools/dotnet-pack.md) gera um arquivo `*.nupkg`, em vez de assemblies.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

A maneira mais antiga de criar um pacote do NuGet é com um arquivo `*.nuspec` e a ferramenta de linha de comando `nuget.exe`. Um arquivo nuspec dá excelente controle, mas você deve especificar com cuidado quais assemblies e destinos incluir no pacote final do NuGet. É fácil cometer um erro ou alguém se esquecer de atualizar o nuspec ao fazer alterações. A vantagem de um nuspec é que você pode usá-lo criar pacotes do NuGet para estruturas que ainda não dão suporte a um arquivo de projeto de estilo do SDK.

**✔️ CONSIDERE** usar um arquivo de projeto no estilo SDK para criar o pacote do NuGet.

**✔️ CONSIDERE** configurar SourceLink para adicionar metadados de controle do código-fonte aos seus assemblies e pacote do NuGet.

## <a name="package-dependencies"></a>Dependências do pacote

Dependências de pacotes NuGet são abordadas detalhadamente no artigo [Dependências](./dependencies.md).

## <a name="important-nuget-package-metadata"></a>Metadados de pacote do NuGet importantes

Um pacote do NuGet dá suporte a muitas [propriedades de metadados](/nuget/reference/nuspec). A tabela a seguir contém os principais metadados que cada projeto de software livre deve fornecer:

| Nome da Propriedade do MSBuild              | Nome Nuspec              | Descrição  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | O identificador do pacote. Um prefixo do identificador poderá ser reservado se ele cumprir os [critérios](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Versão do pacote NuGet. Para obter mais informações, veja [Controle de versão de pacote do NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Um título amigável a humanos do pacote. Usa como padrão `PackageId`.             |
| `Description`                      | `description`              | Uma descrição longa do pacote exibida na interface do usuário.             |
| `Authors`                          | `authors`                  | Uma lista separada por vírgulas de autores de pacote que correspondem aos nomes de perfil em nuget.org.             |
| `PackageTags`                      | `tags`                     | Uma lista delimitada por espaço de marcas e palavras-chave que descrevem o pacote. Marcas são usadas ao pesquisar pacotes.             |
| `PackageIconUrl`                   | `iconUrl`                  | Uma URL para uma imagem a ser usada como o ícone para o pacote. A URL deve ser HTTPS e a imagem deve ser 64 x 64 e ter um segundo plano transparente.             |
| `PackageProjectUrl`                | `projectUrl`               | Uma URL para o repositório de origem ou página inicial do projeto.             |
| `PackageLicenseUrl`                | `licenseUrl`               | Uma URL para a licença do projeto. Pode ser a URL para o arquivo `LICENSE` no controle do código-fonte.             |

**✔️ CONSIDERE** escolher um nome de pacote do NuGet com um prefixo que cumpra os [critérios](/nuget/reference/id-prefix-reservation) de reserva de prefixo do NuGet.

**✔️ CONSIDERE** usar o arquivo `LICENSE` no controle do código-fonte como o `LicenseUrl`. Por exemplo, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).

> [!IMPORTANT]
> Um projeto sem uma licença usa como padrão [direitos autorais exclusivo](https://choosealicense.com/no-permission/), tornando impossível que outras pessoas o usem.

**✔️ FAÇA** uso de um href HTTPS com o ícone do pacote.

> Sites, como o NuGet.org são executados com HTTPS habilitado e exibir uma imagem não HTTPS criará um aviso de conteúdo misto.

**✔️ FAÇA** uso de uma imagem de ícone do pacote de 64 x 64 e com um segundo plano transparente para melhor visualização dos resultados.

## <a name="pre-release-packages"></a>Pacotes de pré-lançamento

Pacotes do NuGet com um sufixo de versão são considerados [pré-lançamento](/nuget/create-packages/prerelease-packages). Por padrão, a interface do usuário do Gerenciador de Pacotes do NuGet mostra versões estáveis, a menos que um usuário aceite pacotes de pré-lançamento, tornando os pacotes de pré-lançamento ideais para testes de usuários limitados.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Um pacote estável não pode depender de um pacote de pré-lançamento. Você deve criar seu próprio pacote de pré-lançamento ou depender de uma versão estável mais antiga.

![Dependência de pacote de pré-lançamento do NuGet](./media/nuget/nuget-prerelease-package.png "Dependência de pacote de pré-lançamento do NuGet")

**✔️ FAÇA** a publicação de um pacote de pré-lançamento ao testar, visualizar ou experimentar.

**✔️ FAÇA** a publicação de um pacote estável quando ele estiver pronto para que outros pacotes estáveis possam fazer referência a ele.

## <a name="symbol-packages"></a>Pacotes de símbolo

Arquivos de símbolo (`*.pdb`) são produzidos pelo compilador do .NET junto com assemblies. Arquivos de símbolo mapeiam locais de execução para o código-fonte original para que você possa percorrer o código-fonte conforme ele é executado usando um depurador. O NuGet dá suporte para [gerar um pacote de símbolos separado](/nuget/create-packages/symbol-packages) contendo arquivos de símbolo junto com o pacote principal contendo assemblies do .NET. A ideia de pacotes de símbolos é que eles estão hospedados em um servidor de símbolos e são baixados somente por uma ferramenta como o Visual Studio sob demanda.

No momento, o principal host público para símbolos – [SymbolSource](http://www.symbolsource.org/) – não dá suporte a novos [arquivos de símbolo portáteis](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) criados por projetos no estilo SDK e pacotes de símbolos não são úteis. Até que haja um host recomendado para pacotes de símbolos, arquivos de símbolo podem ser inseridos no pacote NuGet principal. Se você estiver criando seu pacote do NuGet usando um projeto de estilo do SDK, poderá inserir arquivos de símbolo definindo a propriedade `AllowedOutputExtensionsInPackageBuildOutputFolder`: 

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

**✔️ CONSIDERE** inserir arquivos de símbolo no pacote NuGet principal.

**❌ EVITE** criar um pacote de símbolos contendo arquivos de símbolo.

>[!div class="step-by-step"]
[Anterior](./strong-naming.md)
[Próximo](./dependencies.md)
