---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto do .NET Core ou uma solução em um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156992"
---
# <a name="dotnet-publish"></a>dotnet publish

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet publish` – publica o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>DESCRIÇÃO

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório. A saída inclui os seguintes ativos:

- Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.
- Um arquivo *. deps. JSON* que inclui todas as dependências do projeto.
- Um arquivo *. runtimeconfig. JSON* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).
- As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.

A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução. É a única maneira com suporte oficial de preparar o aplicativo para implantação. Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.

## <a name="arguments"></a>Argumentos

- **`PROJECT|SOLUTION`**

  O projeto ou solução a ser publicada.
  
  * `PROJECT` é o caminho e o nome de [C#](csproj.md)arquivo F#de um Visual Basic de projeto, ou, ou o caminho para um diretório que C#contém F#um arquivo de projeto, ou Visual Basic. Se o diretório não for especificado, o padrão será o diretório atual.

  * `SOLUTION` é o caminho e o nome do arquivo de uma solução (extensão *. sln* ) ou o caminho para um diretório que contém um arquivo de solução. Se o diretório não for especificado, o padrão será o diretório atual. **Disponível a partir do SDK do .NET Core 3,0.** 

## <a name="options"></a>Opções

- **`-c|--configuration <CONFIGURATION>`**

  Define a configuração da compilação. O padrão para a maioria dos projetos é `Debug`, mas você pode substituir as definições de configuração de compilação em seu projeto.

- **`-f|--framework <FRAMEWORK>`**

  Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada. Especifique a estrutura de destino no arquivo de projeto.

- **`--force`**

  Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--interactive`** **disponível a partir do SDK do .NET Core 3,0.**

  Permite que o comando pare e aguarde entrada ou ação do usuário. Por exemplo, para concluir a autenticação. 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo. O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md). Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.

- **`--no-build`**

  Não compila o projeto antes da publicação. Também define o sinalizador `--no-restore` implicitamente.

- **`--no-dependencies`**

  Ignora as referências projeto a projeto e só restaura o projeto raiz.

- **`--nologo`** **disponível a partir do SDK do .NET Core 3,0.**

  Não exibe a faixa de inicialização nem a mensagem de direitos autorais. 

- **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Especifica o caminho para o diretório de saída. Se não for especificado, o padrão será *./bin/[Configuration]/[Framework]/Publish/* para um executável dependente de tempo de execução e binários de plataforma cruzada. O padrão é *./bin/[Configuration]/[Framework]/[Runtime]/Publish/* para um executável independente.

  Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.

- **`--self-contained [true|false]`**

  Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino. O padrão será `true` se um identificador de tempo de execução for especificado. Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).

- **`--no-self-contained`** **disponível a partir do SDK do .NET Core 3,0.**

  Equivalente a `--self-contained false`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publica o aplicativo para um determinado runtime. Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md). Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.

## <a name="examples"></a>Exemplos

- Crie um [binário de plataforma cruzada dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:

  ```dotnetcli
  dotnet publish
  ```

  A partir do SDK do .NET Core 3,0, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.

- Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, para um tempo de execução específico:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  O RID deve estar no arquivo de projeto.

- Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  O RID deve estar no arquivo de projeto. Este exemplo se aplica ao SDK do .NET Core 3,0 e versões posteriores.

- Publicar o projeto no diretório atual, para um tempo de execução e estrutura de destino específicos:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publicar o arquivo de projeto especificado:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publicar o aplicativo atual, mas não restaurar referências ponto a projeto (P2P), apenas o projeto raiz durante a operação de restauração:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Confira também

- [Visão geral da publicação de aplicativos do .NET Core](../deploying/index.md)
- [Publicar aplicativos .NET Core com o CLI do .NET Core](../deploying/deploy-with-cli.md)
- [Estruturas de destino](../../standard/frameworks.md)
- [Catálogo de RID (Identificador de Runtime)](../rid-catalog.md)
- [Trabalhando com o notarization Catalina do MacOS](../install/macos-notarization-issues.md) Para obter mais informações, consulte os seguintes recursos:
- [Estrutura de diretórios de um aplicativo publicado](/aspnet/core/hosting/directory-structure)
