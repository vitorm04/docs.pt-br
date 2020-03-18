---
title: Solucionar problemas de uso da ferramenta .NET Core
description: Descubra os problemas comuns ao executar ferramentas do .NET Core e possíveis soluções.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146444"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Solucionar problemas de uso da ferramenta .NET Core

Você pode encontrar problemas ao tentar instalar ou executar uma ferramenta .NET Core, que pode ser uma ferramenta global ou uma ferramenta local. Este artigo descreve as causas básicas comuns e algumas soluções possíveis.

## <a name="installed-net-core-tool-fails-to-run"></a>A ferramenta .NET Core instalada não é executada

Quando uma ferramenta .NET Core falha em ser executada, provavelmente você encontrou um dos seguintes problemas:

* O arquivo executável da ferramenta não foi encontrado.
* A versão correta do tempo de execução do .NET Core não foi encontrada.

### <a name="executable-file-not-found"></a>Arquivo executável não encontrado

Se o arquivo executável não for encontrado, você verá uma mensagem semelhante à seguinte:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

O nome do executável determina como você invoca a ferramenta. A tabela a seguir descreve o formato:

| Formato de nome executável  | Formato de invocação   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Ferramentas globais

  Ferramentas globais podem ser instaladas no diretório padrão ou em um local específico. Os diretórios padrão são:

  | Sistema operacional          | Caminho                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  Se você está tentando executar uma ferramenta `PATH` global, verifique se a variável de ambiente em sua máquina contém o caminho onde você instalou a ferramenta global e se o executável está nesse caminho.

  O .NET Core CLI tenta adicionar o local padrão à variável ambiente PATH em seu primeiro uso. No entanto, existem alguns cenários em que o local pode não ser adicionado automaticamente ao PATH:

  * Se você estiver usando o Linux e tiver instalado o .NET Core SDK usando arquivos *.tar.gz* e não apt-get ou rpm.
  * Se você estiver usando o macOS 10.15 "Catalina" ou versões posteriores.
  * Se você estiver usando macOS 10.14 "Mojave" ou versões anteriores, e você instalou o .NET Core SDK usando arquivos *.tar.gz* e não *.pkg*.
  * Se você instalou o .NET Core 3.0 SDK `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` e definiu `false`a variável de ambiente para .
  * Se você instalou o .NET Core 2.2 SDK ou versões anteriores, e definiu a `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` variável de ambiente para `true`.

  Nesses cenários ou se `--tool-path` você especificou a opção, a `PATH` variável de ambiente na sua máquina não contém automaticamente o caminho onde você instalou a ferramenta global. Nesse caso, anexar a localização da `$HOME/.dotnet/tools`ferramenta (por exemplo, ) à variável `PATH` ambiente usando qualquer método que seu shell forneça para atualizar variáveis do ambiente. Para obter mais informações, consulte [as ferramentas .NET Core](global-tools.md).

* Ferramentas locais

  Se você está tentando executar uma ferramenta local, verifique se há um arquivo manifesto chamado *dotnet-tools.json* no diretório atual ou em qualquer um de seus diretórios-pai. Este arquivo também pode viver em uma pasta chamada *.config* em qualquer lugar na hierarquia da pasta do projeto, em vez da pasta raiz. Se *o dotnet-tools.json* existir, abra-o e verifique se há a ferramenta que você está tentando executar. Se o arquivo não contiver `"isRoot": true`uma entrada para, então verifique também a hierarquia do arquivo para obter arquivos de manifesto de ferramentas adicionais.

  Se você está tentando executar uma ferramenta .NET Core que foi instalada com um caminho especificado, você precisa incluir esse caminho ao usar a ferramenta. Um exemplo de uso de uma ferramenta instalada de caminho de ferramenta é:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Tempo de execução não encontrado

As ferramentas .NET Core são [aplicativos dependentes de framework,](../deploying/index.md#publish-runtime-dependent)o que significa que eles dependem de um tempo de execução do .NET Core instalado na máquina. Se o tempo de execução esperado não for encontrado, eles seguirão as regras normais de andamento do .NET Core, como:

* Um aplicativo efetua roll forward até a versão de patch mais recente da versão principal e secundária especificadas.
* Se não houver tempo de execução correspondente com um número de versão maior e menor correspondente, a próxima versão menor superior é usada.
* O roll forward não ocorre entre versões prévias do runtime ou entre versões prévias e versões de lançamento. Assim, as ferramentas .NET Core criadas usando versões de pré-visualização devem ser reconstruídas e republicadas pelo autor e reinstaladas.

O roll-forward não ocorrerá por padrão em dois cenários comuns:

* Apenas versões inferiores do tempo de execução estão disponíveis. O roll-forward só seleciona versões posteriores do tempo de execução.
* Apenas versões principais mais altas do tempo de execução estão disponíveis. Roll-forward não ultrapassa os principais limites da versão.

Se um aplicativo não consegue encontrar um tempo de execução apropriado, ele falha ao executar e relata um erro.

Você pode descobrir quais tempos de execução do .NET Core estão instalados na sua máquina usando um dos seguintes comandos:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Se você acha que a ferramenta deve suportar a versão em tempo de execução que você instalou atualmente, você pode entrar em contato com o autor da ferramenta e ver se eles podem atualizar o número da versão ou o multi-alvo. Uma vez que eles tenham recompilado e republicado seu pacote de ferramentas para NuGet com um número de versão atualizado, você pode atualizar sua cópia. Enquanto isso não acontece, a solução mais rápida para você é instalar uma versão do tempo de execução que funcionaria com a ferramenta que você está tentando executar. Para baixar uma versão específica do .NET Core runtime, visite a [página de download do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

Se você instalar o .NET Core SDK em um local não `DOTNET_ROOT` padrão, você precisará `dotnet` definir a variável de ambiente para o diretório que contém o executável.

## <a name="net-core-tool-installation-fails"></a>Falha na instalação da ferramenta .NET Core

Há uma série de razões pelas quais a instalação de uma ferramenta global ou local do .NET Core pode falhar. Quando a instalação da ferramenta falhar, você verá uma mensagem semelhante à seguinte:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Para ajudar a diagnosticar essas falhas, as mensagens NuGet são mostradas diretamente ao usuário, juntamente com a mensagem anterior. A mensagem NuGet pode ajudá-lo a identificar o problema.

### <a name="package-naming-enforcement"></a>Aplicação de nomeação de pacotes

A Microsoft mudou sua orientação sobre o ID do pacote para ferramentas, resultando em uma série de ferramentas não encontradas com o nome previsto. A nova orientação é que todas as ferramentas da Microsoft sejam prefixadas com "Microsoft". Este prefixo é reservado e só pode ser usado para pacotes assinados com um certificado autorizado pela Microsoft.

Durante a transição, algumas ferramentas da Microsoft terão a forma antiga do ID do pacote, enquanto outras terão a nova forma:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

À medida que os IDs do pacote são atualizados, você precisará mudar para o novo ID do pacote para obter as atualizações mais recentes. Os pacotes com o nome da ferramenta simplificada serão depreciados.

### <a name="preview-releases"></a>Versões de pré-visualização

* Você está tentando instalar uma versão de pré-visualização e não usou a `--version` opção de especificar a versão.

As ferramentas .NET Core que estão em pré-visualização devem ser especificadas com uma parte do nome para indicar que estão em pré-visualização. Você não precisa incluir toda a pré-visualização. Supondo que os números da versão estejam no formato esperado, você pode usar algo como o seguinte exemplo:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>O pacote não é uma ferramenta .NET Core

* Um pacote NuGet com esse nome foi encontrado, mas não era uma ferramenta .NET Core.

Se você tentar instalar um pacote NuGet que seja um pacote NuGet normal e não uma ferramenta .NET Core, você verá um erro semelhante ao seguinte:

> NU1212: Combinação inválida de `<ToolName>`pacote de projeto para . O estilo de projeto DotnetToolReference só pode conter referências do tipo DotnetTool.

### <a name="nuget-feed-cant-be-accessed"></a>O feed NuGet não pode ser acessado

* O feed NuGet necessário não pode ser acessado, talvez por causa de um problema de conexão à Internet.

A instalação da ferramenta requer acesso ao feed NuGet que contém o pacote da ferramenta. Falha se a ração não estiver disponível. Você pode alterar `nuget.config`feeds com, solicitar um arquivo `nuget.config` específico `--add-source` ou especificar feeds adicionais com o switch. Por padrão, nuGet lança um erro para qualquer feed que não possa se conectar. A `--ignore-failed-sources` bandeira pode pular essas fontes não alcançáveis.

### <a name="package-id-incorrect"></a>ID do pacote incorreto

* Você digitou mal o nome da ferramenta.

Uma razão comum para o fracasso é que o nome da ferramenta não está correto. Isso pode acontecer por causa da mistyping, ou porque a ferramenta se moveu ou foi preterida. Para ferramentas no NuGet.org, uma maneira de garantir que você tenha o nome correto é procurar a ferramenta em NuGet.org e copiar o comando de instalação.

## <a name="see-also"></a>Confira também

* [.NET Core ferramentas](global-tools.md)
