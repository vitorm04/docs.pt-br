---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto ou solução .NET Core para um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: 26dda33d04f3f7a23805627708b55233ef4e87ef
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242836"
---
# <a name="dotnet-publish"></a>dotnet publish

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet publish`- Publica o aplicativo e suas dependências para uma pasta para implantação em um sistema de hospedagem.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-p:PublishReadyToRun] [-p:PublishSingleFile]
    [-p:PublishTrimmed] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Descrição

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório. A saída inclui os seguintes ativos:

- Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.
- Um arquivo *.deps.json* que inclui todas as dependências do projeto.
- Um arquivo *.runtimeconfig.json* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).
- As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.

A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução. É a única maneira com suporte oficial de preparar o aplicativo para implantação. Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado. Para obter mais informações, consulte [Publicar os aplicativos .NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).

### <a name="msbuild"></a>MSBuild

O comando `dotnet publish` chama MSBuild, que invoca o destino `Publish`. Quaisquer parâmetros passados para `dotnet publish` são passados para o MSBuild. Os parâmetros `-c` e `-o` mapeiam as propriedades `Configuration` e `OutputPath` do MSBuild, respectivamente.

O `dotnet publish` comando aceita opções de `-p` MSBuild, `-l` como para definir propriedades e definir um logger. Por exemplo, você pode definir uma propriedade MSBuild usando o formato: `-p:<NAME>=<VALUE>`. Você também pode definir propriedades relacionadas à publicação referindo-se a um arquivo *.pubxml,* por exemplo:

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

Para saber mais, consulte os recursos a seguir:

- [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Argumentos

- **`PROJECT|SOLUTION`**

  O projeto ou solução para publicar.
  
  * `PROJECT`é o caminho e o nome de arquivo de um arquivo de projeto [C#,](csproj.md)F#ou Visual Basic, ou o caminho para um diretório que contém um arquivo de projeto C#, F#ou Visual Basic. Se o diretório não for especificado, ele será padrão para o diretório atual.

  * `SOLUTION`é o caminho e o nome de arquivo de um arquivo de solução (extensão *.sln)* ou o caminho para um diretório que contém um arquivo de solução. Se o diretório não for especificado, ele será padrão para o diretório atual. Disponível desde o SDK do .NET Core 3.0.

## <a name="options"></a>Opções

- **`-c|--configuration <CONFIGURATION>`**

  Define a configuração da compilação. O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.

- **`-f|--framework <FRAMEWORK>`**

  Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada. Especifique a estrutura de destino no arquivo de projeto.

- **`--force`**

  Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--interactive`**

  Permite que o comando pare e aguarde entrada ou ação do usuário. Por exemplo, para concluir a autenticação. Disponível desde o SDK do .NET Core 3.0.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo. O arquivo manifesto faz parte [ `dotnet store` ](dotnet-store.md)da saída do comando . Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.

- **`--no-build`**

  Não compila o projeto antes da publicação. Também define o sinalizador `--no-restore` implicitamente.

- **`--no-dependencies`**

  Ignora as referências projeto a projeto e só restaura o projeto raiz.

- **`--nologo`**

  Não exibe a faixa de inicialização nem a mensagem de direitos autorais. Disponível desde o SDK do .NET Core 3.0.

- **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Especifica o caminho para o diretório de saída.
  
  Se não especificado, ele é padrão para *[project_file_folder]./bin/[configuração]/[framework]/publish/* para binários executáveis e multiplataformas dependentes de tempo de execução. Ele é padrão para *[project_file_folder]/bin/[configuração]/[framework]/[runtime]/publish/* para um executável independente.

  Em um projeto web, se a pasta de `dotnet publish` saída estiver na pasta do projeto, comandos sucessivos resultarão em pastas de saída aninhadas. Por exemplo, se a pasta do projeto for *myproject*, e a `dotnet publish` pasta de saída publicar for *myproject/publish*, e você for executado duas vezes, a segunda execução coloca arquivos de conteúdo como *arquivos .config* e *.json* no *myproject/publish/publish*. Para evitar o ninho de pastas de publicação, especifique uma pasta de publicação que não esteja diretamente sob a pasta do projeto ou exclua a pasta de publicação do projeto. Para excluir uma pasta de publicação chamada *publishoutput*, adicione o seguinte elemento a um `PropertyGroup` elemento no arquivo *.csproj:*

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3.x SDK e posterior
  
    Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo ao diretório de trabalho atual, não à localização do arquivo do projeto.

    Se um caminho relativo for especificado ao publicar uma solução, toda a saída para todos os projetos entrará na pasta especificada em relação ao diretório de trabalho atual. Para fazer a saída de publicação ir para pastas separadas para `PublishDir` cada projeto, especifique um caminho relativo usando a propriedade msbuild em vez da `--output` opção. Por exemplo, `dotnet publish -p:PublishDir=.\publish` envia a saída `publish` de publicação de cada projeto para uma pasta sob a pasta que contém o arquivo do projeto.

  - .NET Core 2.x SDK
  
    Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo à localização do arquivo do projeto, não ao diretório de trabalho atual.

    Se um caminho relativo for especificado ao publicar uma solução, a saída de cada projeto será colocada em uma pasta separada em relação ao local do arquivo do projeto. Se um caminho absoluto for especificado ao publicar uma solução, todas as saídas de publicação para todos os projetos serão colocadas na pasta especificada.

- **`-p:PublishReadyToRun`**

  Compila conjuntos de aplicativos como formato ReadyToRun (R2R). R2R é uma forma de compilação antecipada (AOT). Para obter mais informações, consulte [imagens ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images). Disponível desde o SDK do .NET Core 3.0.

  Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando. Para mais informações, consulte [MSBuild](#msbuild).

- **`-p:PublishSingleFile`**

  Empacota o aplicativo em um executável de arquivo único específico da plataforma. O executável é auto-extraindo e contém todas as dependências (incluindo nativas) que são necessárias para executar o aplicativo. Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build. A inicialização é mais rápida quando o aplicativo é executado novamente. O aplicativo não precisa se extrair uma segunda vez, a menos que uma nova versão seja usada. Disponível desde o SDK do .NET Core 3.0.

  Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

  Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando. Para mais informações, consulte [MSBuild](#msbuild).

- **`-p:PublishTrimmed`**

  Apara bibliotecas não utilizadas para reduzir o tamanho de implantação de um aplicativo ao publicar um executável independente. Para obter mais informações, consulte [Trim implantações e executáveis independentes](../deploying/trim-self-contained.md). Disponível desde o SDK do .NET Core 3.0.

  Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando. Para mais informações, consulte [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino. O `true` padrão é se um identificador de tempo de execução for especificado e o projeto for um projeto executável (não um projeto de biblioteca). Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).

  Se essa opção for `true` usada `false`sem `true`especificar ou, o padrão será . Nesse caso, não coloque a solução ou o `--self-contained`argumento `true` `false` do projeto imediatamente depois, porque ou é esperado nessa posição.

- **`--no-self-contained`**

  Equivalente a `--self-contained false`. Disponível desde o SDK do .NET Core 3.0.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publica o aplicativo para um determinado runtime. Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md). Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.

## <a name="examples"></a>Exemplos

- Crie um [binário multiplataforma dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:

  ```dotnetcli
  dotnet publish
  ```

  Começando com o .NET Core 3.0 SDK, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.

- Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, por um tempo de execução específico:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  O RID deve estar no arquivo do projeto.

- Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  O RID deve estar no arquivo do projeto. Este exemplo se aplica ao .NET Core 3.0 SDK e versões posteriores.

- Publique o projeto no diretório atual, para obter um tempo de execução específico e uma estrutura de destino:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publicar o arquivo de projeto especificado:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publique o aplicativo atual, mas não restaure as referências p2P (project-to-project), apenas o projeto raiz durante a operação de restauração:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Confira também

- [Visão geral da publicação de aplicativos .NET Core](../deploying/index.md)
- [Publique os aplicativos .NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md)
- [Frameworks de destino](../../standard/frameworks.md)
- [Catálogo de identificadores de execução (RID)](../rid-catalog.md)
- [Trabalhando com nota nota notardo pelo macOS Catalina](../install/macos-notarization-issues.md)
- [Estrutura do diretório de um aplicativo publicado](/aspnet/core/hosting/directory-structure)
- [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk.Tarefas](https://aka.ms/dotnet-illink)
