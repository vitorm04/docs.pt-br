---
title: Modelos personalizados para dotnet new
description: Saiba mais sobre modelos personalizados para qualquer tipo de projeto ou de arquivos do .NET.
author: guardrex
ms.date: 08/11/2017
ms.openlocfilehash: e37fb692640c25d7a91904b0802f97ebfab75851
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679054"
---
# <a name="custom-templates-for-dotnet-new"></a>Modelos personalizados para dotnet new

O [SDK do .NET Core](https://www.microsoft.com/net/download/core) vem com muitos modelos pré-instalados a serem usados com o [comando`dotnet new`](dotnet-new.md). A partir do .NET Core 2.0, é possível criar seus próprios modelos personalizados para qualquer tipo de projeto, como um aplicativo, serviço, ferramenta ou biblioteca de classes. É possível, inclusive, criar um modelo que gere um ou mais arquivos independentes, como um arquivo de configuração.

É possível instalar modelos personalizados de um pacote NuGet em qualquer feed do NuGet, referenciando um arquivo *nupkg* do NuGet diretamente ou especificando um diretório de sistema de arquivos que contenha o modelo. O mecanismo de modelo oferece recursos que permitem substituir valores, incluir e excluir arquivos e regiões de arquivos e executar operações de processamento personalizadas quando seu modelo é usado.

O mecanismo de modelo é um software livre e o repositório de código online fica em [dotnet/modelagem](https://github.com/dotnet/templating/) no GitHub. Acesse o repositório [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) para obter exemplos de modelos. Mais modelos, incluindo modelos de terceiros, são encontrados em [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (Modelos disponíveis para dotnet new) no GitHub. Para obter mais informações sobre a criação e o uso de modelos personalizados, consulte [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) (Como criar seus próprios modelos para dotnet new) e o [Wiki do repositório GitHub dotnet/modelagem](https://github.com/dotnet/templating/wiki).

Para seguir um passo a passo e criar um modelo, consulte o tutorial [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new).

## <a name="configuration"></a>Configuração

O modelo é composto pelos seguintes componentes:

- Arquivos e pastas de origem
- Um arquivo de configuração (*template.json*)

### <a name="source-files-and-folders"></a>Arquivos e pastas de origem

Os arquivos e pastas de origem incluem os arquivos e pastas que você desejar que o mecanismo de modelo use quando o comando `dotnet new <TEMPLATE>` é executado. O mecanismo de modelo foi desenvolvido para usar *projetos executáveis* como código-fonte para produzir os projetos. Isso tem várias vantagens:

- O mecanismo de modelo não exige que você insira tokens especiais no código-fonte do seu projeto.
- Os arquivos de código não são arquivos especiais nem modificados de nenhuma maneira para trabalhar com o mecanismo de modelo. Portanto, as ferramentas que você normalmente usa ao trabalhar com projetos também funcionam com o conteúdo do modelo.
- Compile, execute e depurar seus projetos de modelo assim como você faz com quaisquer outros projetos.
- É possível criar rapidamente um modelo com base em um projeto existente simplesmente adicionando um arquivo de configuração *template.json* ao projeto.

Os arquivos e pastas armazenados no modelo não são limitados aos tipos de projeto .NET formais, como soluções .NET Core ou .NET Framework. Talvez os arquivos e pastas de origem sejam compostos por qualquer conteúdo que você deseje criar quando o modelo é usado, mesmo se o mecanismo do modelo produzir apenas um arquivo para sua saída, como um arquivo de solução ou de configuração. Por exemplo, é possível criar um modelo que contenha um arquivo de origem *web.config* e crie um arquivo *web.config* modificado para projetos em que o modelo é usado. As modificações nos arquivos de origem são baseadas na lógica e nas configurações fornecidas no arquivo de configuração *template.json* juntamente com os valores fornecidos pelo usuário passados como opções para o comando `dotnet new <TEMPLATE>`.

### <a name="templatejson"></a>template.json

O arquivo *template.json* é colocado em uma pasta *.template.config* no diretório raiz do modelo. O arquivo fornece informações de configuração para o mecanismo de modelo. A configuração mínima requer os membros mostrados na tabela a seguir, suficiente para criar um modelo funcional.

| Membro            | Tipo          | Descrição |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | O esquema JSON do arquivo *template.json*. Os editores que dão suporte a esquemas JSON habilitam recursos de edição de JSON quando o esquema é especificado. Por exemplo, o [Visual Studio Code](https://code.visualstudio.com/) requer que esse membro habilite o IntelliSense. Use um valor de `http://json.schemastore.org/template`. |
| `author`          | cadeia de caracteres        | O autor do modelo. |
| `classifications` | array(string) | Zero ou mais características do modelo que um usuário pode usar para localizá-lo ao procurá-lo. As classificações também são exibidas na coluna *Marcas* quando ela é exibida em uma lista de modelos produzida usando o comando <code>dotnet new -l&#124;--list</code>. |
| `identity`        | cadeia de caracteres        | Um nome exclusivo para este modelo. |
| `name`            | cadeia de caracteres        | O nome do modelo que os usuários devem ver. |
| `shortName`       | cadeia de caracteres        | Uma abreviação padrão para selecionar o modelo aplicável aos ambientes em que o nome do modelo é especificado pelo usuário, não selecionado por uma GUI. Por exemplo, o nome curto é útil ao usar os modelos em um prompt de comando com comandos CLI. |

#### <a name="example"></a>Exemplo:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

O esquema completo do arquivo *template.json* é encontrado no [Repositório de Esquema JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Modelos padrão do .NET

Quando você instala o [SDK do .NET Core](https://www.microsoft.com/net/download/core), você recebe dezenas de modelos internos para criar projetos e arquivos, incluindo aplicativos de console, bibliotecas de classes, projetos de teste de unidade, aplicativos ASP.NET Core (incluindo projetos [Angulares](https://angular.io/) e de [Reação](https://facebook.github.io/react/)) e arquivos de configuração. Para listar os modelos internos, execute o comando `dotnet new` com a opção `-l|--list`:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Empacotamento de um modelo em um pacote NuGet (arquivo nupkg)

No momento, um modelo personalizado é fornecido no Windows com [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (não [dotnet pack](dotnet-pack.md)). Para o empacotamento de plataforma cruzada, considere usar o [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

O conteúdo da pasta do projeto, junto com seu arquivo *.template.config/template.json*, são colocados em uma pasta chamada *conteúdo*. Ao lado da pasta *conteúdo*, adicione um arquivo [*nuspec*](/nuget/create-packages/creating-a-package), que é um arquivo de manifesto XML que descreve o conteúdo de um pacote e orienta o processo de criação do pacote NuGet. Dentro de um elemento **\<packageTypes>** no arquivo *nuspec*, inclua um elemento **\<packageType>** com um valor de atributo `name` de `Template`. Tanto a pasta *conteúdo* quanto o arquivo *nuspec* devem residir no mesmo diretório. A tabela mostra os elementos mínimos do arquivo *nuspec* necessários para produzir um modelo como um pacote NuGet.

| Elemento            | Tipo   | Descrição |
| ------------------ | ------ | ----------- |
| **\<authors>**     | cadeia de caracteres | Uma lista separada por vírgulas de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Os autores são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores. |
| **\<description>** | cadeia de caracteres | Uma descrição longa do pacote para exibição de interface do usuário. |
| **\<id>**          | cadeia de caracteres | O identificador do pacote que não diferencia maiúsculas de minúsculas, que deve ser exclusivo no nuget.org ou qualquer galeria na qual o pacote resida. As IDs não podem conter espaços nem caracteres que não sejam válidos para uma URL e geralmente seguem as regras de namespace do .NET. Consulte [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) (Escolhendo um identificador de pacote único e definindo o número de versão) para obter orientação. |
| **\<packageType>** | cadeia de caracteres | Coloque esse elemento dentro de um elemento **\<packageTypes>** entre os elementos **\<metadata>**. Defina o atributo `name` do elemento **\<packageType>** como `Template`. |
| **\<version>**     | cadeia de caracteres | A versão do pacote, seguindo o padrão principal.secundário.patch. Os números de versão podem incluir um sufixo de pré-lançamento, conforme descrito no tópico [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning) (Versões de pré-lançamento). |

Consulte o esquema de arquivo completo [nuspec](/nuget/schema/nuspec) na *referência do .nuspec*. Um arquivo *nuspec* de exemplo para um modelo é exibido no tutorial [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new).

[Crie um pacote](/nuget/create-packages/creating-a-package#creating-the-package) usando o comando `nuget pack <PATH_TO_NUSPEC_FILE>`.

## <a name="installing-a-template"></a>Instalação de um modelo

Instale um modelo personalizado de um pacote NuGet em qualquer feed do NuGet, referenciando um arquivo *nupkg* diretamente ou especificando um diretório de sistema de arquivos que contenha a configuração de modelagem. Use a opção `-i|--install` com o comando [dotnet new](dotnet-new.md).

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Para instalar um modelo de um pacote NuGet armazenado em nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Para instalar um modelo de um arquivo nupkg local

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Para instalar um modelo de um diretório de sistema de arquivos

O `FILE_SYSTEM_DIRECTORY` é a pasta de projeto que contém o projeto e a pasta *.template.config*:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Desinstalação de um modelo

Desinstale um modelo personalizado referenciando um pacote NuGet por seu `id` ou especificando um diretório de sistema de arquivos que contenha uma configuração de modelagem. Use a opção de instalação `-u|--uninstall` com o comando [dotnet new](dotnet-new.md).

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Para desinstalar um modelo de um pacote NuGet armazenado em nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Para desinstalar um modelo de um arquivo nupkg local

Para desinstalar o modelo, não tente usar o caminho para o arquivo *nupkg*. A tentativa de desinstalar um modelo usando `dotnet new -u <PATH_TO_NUPKG_FILE>` falha. Referencie o pacote por seu `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Para desinstalar um modelo de um diretório de sistema de arquivos

O `FILE_SYSTEM_DIRECTORY` é a pasta de projeto que contém o projeto e a pasta *.template.config*. O caminho fornecido deve ser o caminho absoluto. A tentativa de desinstalar um modelo usando um caminho relativo falha. Para saber mais, confira o artigo [dotnet new](dotnet-new.md).

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Criar um projeto usando um modelo personalizado

Depois que um modelo é instalado, use o modelo executando o comando `dotnet new <TEMPLATE>` como você faria com qualquer outro modelo pré-instalado. Também é possível especificar [opções](dotnet-new.md#options) para o comando `dotnet new`, incluindo opções específicas do modelo definidas nas configurações de modelo. Forneça o nome curto do modelo diretamente no comando:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Consulte também

- [Criar um modelo personalizado para dotnet new (tutorial)](../tutorials/create-custom-template.md)
- [Wiki do repositório GitHub dotnet/modelagem](https://github.com/dotnet/templating/wiki)
- [Repositório do GitHub de dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Como criar seus próprios modelos para dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [Esquema *template.json* no Repositório de Esquema JSON](http://json.schemastore.org/template)
