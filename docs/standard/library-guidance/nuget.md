---
title: Bibliotecas do NuGet e .NET
description: Práticas recomendadas para o empacotamento com o NuGet para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: d0ea462a7f52dd9a6b2f14be9ed5770160bf66b1
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374478"
---
# <a name="nuget"></a>NuGet

NuGet é um Gerenciador de pacotes para o ecossistema do .NET e é os principal dos desenvolvedores descobrir e adquirem as bibliotecas de código-fonte aberto do .NET. [NuGet.org](https://www.nuget.org/), um serviço gratuito, fornecido pela Microsoft para hospedar pacotes do NuGet, é o host primário para os pacotes do NuGet públicos, mas você pode publicar em serviços personalizados do NuGet, como [MyGet](https://www.myget.org/) e [artefatos do Azure ](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Criar um pacote do NuGet

Um pacote do NuGet (`*.nupkg`) é um arquivo zip que contém os assemblies do .NET e os metadados associados.

Há duas maneiras principais de criar um pacote do NuGet. A maneira recomendada e mais recente é criar um pacote de um projeto de estilo do SDK (arquivo de projeto cujo conteúdo é iniciado com `<Project Sdk="Microsoft.NET.Sdk">`). Assemblies e destinos são automaticamente adicionados ao pacote e o restante de metadados é adicionada ao arquivo MSBuild, como o número de versão e o nome do pacote. Compilar com o [ `dotnet pack` ](../../core/tools/dotnet-pack.md) saídas de comando um `*.nupkg` arquivo em vez de assemblies.

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

A maneira mais antiga da criação de um pacote do NuGet é com um `*.nuspec` arquivo e o `nuget.exe` ferramenta de linha de comando. Um arquivo nuspec lhe dá controle excelente, mas você deve especificar cuidadosamente quais assemblies e destinos para incluir no pacote do NuGet final. É fácil cometer um erro ou que alguém se esqueça de atualizar o nuspec ao fazer alterações. A vantagem de um nuspec é que você pode usá-la criar pacotes do NuGet para estruturas que ainda não dão suporte a um arquivo de projeto de estilo do SDK.

**Considere a possibilidade de ✔️** usando um arquivo de projeto de estilo do SDK para criar o pacote do NuGet.

**Considere a possibilidade de ✔️** Configurando SourceLink para adicionar metadados de controle do código-fonte para seus assemblies e o pacote do NuGet.

## <a name="package-dependencies"></a>Dependências do pacote

Dependências de pacotes NuGet são abordadas detalhadamente os [dependências](./dependencies.md) artigo.

## <a name="important-nuget-package-metadata"></a>Metadados de pacote do NuGet importantes

Um pacote do NuGet dá suporte a muitos [propriedades de metadados](/nuget/reference/nuspec). A tabela a seguir contém os metadados de núcleo que cada projeto de código-fonte aberto deve fornecer:

| Nome da propriedade do MSBuild              | Nome de NuSpec              | Descrição  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | O identificador de pacote. Um prefixo do identificador pode ser reservado se ele atende a [critérios](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Versão do pacote do NuGet. Para obter mais informações, consulte [versão do pacote NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Um título amigável a humanos do pacote. O padrão é o `PackageId`.             |
| `Description`                      | `description`              | Uma descrição longa do pacote exibido na interface do usuário.             |
| `Authors`                          | `authors`                  | Uma lista separada por vírgulas de autores de pacote, a correspondência de nomes de perfil em nuget.org.             |
| `PackageTags`                      | `tags`                     | Uma lista delimitada por espaço de marcas e palavras-chave que descrevem o pacote. Marcas são usadas ao procurar pacotes.             |
| `PackageIconUrl`                   | `iconUrl`                  | Uma URL para uma imagem a ser usado como o ícone para o pacote. URL deve ser HTTPS e a imagem deve ser 64 x 64 e ter um plano de fundo transparente.             |
| `PackageProjectUrl`                | `projectUrl`               | Uma URL para o repositório de home page ou a fonte do projeto.             |
| `PackageLicenseUrl`                | `licenseUrl`               | Uma URL para a licença do projeto. Pode ser a URL para o `LICENSE` arquivo no controle de origem.             |

**Considere a possibilidade de ✔️** escolher um nome de pacote do NuGet com um prefixo que atenda a reserva de prefixo do NuGet [critérios](/nuget/reference/id-prefix-reservation).

**✔️ CONSIDERE** usando o `LICENSE` arquivo no controle do código-fonte como o `LicenseUrl`. Por exemplo, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).

> [!IMPORTANT]
> Um projeto sem o padrão é uma licença [copyright exclusivo](https://choosealicense.com/no-permission/), tornando impossível para que outras pessoas usem.

**FAZER ✔️** usar um href HTTPS com o ícone do pacote.

> Sites, como o NuGet.org executam com habilitadas para HTTPS e exibir uma imagem não HTTPS criará um aviso de conteúdo misto.

**FAZER ✔️** usar uma imagem de ícone do pacote que é 64 x 64 e tem um plano de fundo transparente para melhor visualização dos resultados.

## <a name="pre-release-packages"></a>Pacotes de pré-lançamento

Pacotes do NuGet com um sufixo de versão são considerados [pré-lançamento](/nuget/create-packages/prerelease-packages). Por padrão, a UI do Gerenciador de pacotes do NuGet mostra versões estáveis, a menos que um usuário aceita-in de pré-lançamento em pacotes, tornando os pacotes de pré-lançamento ideal para testes de usuário limitado.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Um pacote estável não pode depender de um pacote de pré-lançamento. Você deve fazer seu próprio pacote de pré-lançamento ou dependem de uma versão estável mais antiga.

![Dependência de pacote de pré-lançamento do NuGet](./media/nuget/nuget-prerelease-package.png "dependência de pacote de pré-lançamento do NuGet")

**FAZER ✔️** publicar um pacote de pré-lançamento ao testar, visualizar ou testar.

**FAZER ✔️** publicar um pacote estável quando seu pronto para os outros pacotes estáveis podem fazer referência a ela.

## <a name="symbol-packages"></a>Pacotes de símbolos

O NuGet dá suporte a [gerar um pacote de símbolos separados](/nuget/create-packages/symbol-packages) contendo depurar arquivos PDB junto com o pacote principal que contém os assemblies do .NET. A ideia de pacotes de símbolos é que eles estão hospedados em um servidor de símbolos e são baixados somente por uma ferramenta como o Visual Studio sob demanda.

No momento, o principal público do host para símbolos - [SymbolSource](http://www.symbolsource.org/) -não dá suporte as PDBs portáteis criados pelo SDK do estilo projetos e pacotes de símbolos não são úteis.

**Considere a possibilidade de ✔️** inserindo PDBs no pacote NuGet principal.

**❌ Evite** criando um pacote de símbolos com PDBs.

>[!div class="step-by-step"]
[Anterior](./strong-naming.md)
[Próximo](./dependencies.md)
