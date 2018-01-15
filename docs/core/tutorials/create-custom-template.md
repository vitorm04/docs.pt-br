---
title: Criar um modelo personalizado para dotnet new
description: Saiba como criar um modelo personalizado para o comando dotnet new neste divertido tutorial.
keywords: .NET, .NET Core, modelo, modelagem, tutorial, dotnet new
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.workload: dotnetcore
ms.openlocfilehash: 44b4ff6b870a6515f623c690ad722917c9ea5bd3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Criar um modelo personalizado para dotnet new

Este tutorial mostra como:

- Criar um modelo básico com base em um projeto existente ou em um novo projeto de aplicativo de console.
- Empacotar o modelo para distribuição em nuget.org ou de um arquivo *nupkg* local.
- Instalar o modelo do nuget.org, de um arquivo *nupkg* local ou do sistema de arquivos local.
- Desinstalar o modelo.

Se você preferir acompanhar o tutorial com um exemplo completo, baixe o [exemplo de modelo de projeto](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). O exemplo de modelo é configurado para distribuição no NuGet.

Se você desejar usar o exemplo baixado com a distribuição do sistema de arquivos, faça o seguinte:

- Mova o conteúdo da pasta *conteúdo* do exemplo um nível para cima para a pasta *GarciaSoftware.ConsoleTemplate.CSharp*.
- Exclua a pasta *conteúdo* vazia.
- Exclua o arquivo *nuspec*.

## <a name="prerequisites"></a>Pré-requisitos

- Instalar o [SDK 2.0 do .NET Core](https://www.microsoft.com/net/core) ou versões posteriores.
- Leia o tópico de referência [Custom templates for dotnet new](../tools/custom-templates.md) (Modelos personalizados para dotnet new).

## <a name="create-a-template-from-a-project"></a>Criar um modelo com base em um projeto

Use um projeto existente que você confirmou que compila e executa ou crie um novo projeto de aplicativo de console em uma pasta no disco rígido. Este tutorial pressupõe que o nome da pasta do projeto é *GarciaSoftware.ConsoleTemplate.CSharp* armazenado em *Documentos/Modelos* no perfil do usuário. O nome do modelo de projeto do tutorial está no formato *\<Nome da empresa>.\<Tipo de modelo>.\<Linguagem de programação>*, mas é livre para nomear seu projeto e o modelo que você deseja.

1. Adicione uma pasta à raiz do projeto chamado *.template.config*.
1. Dentro da pasta *.template.config*, crie um arquivo *template.json* para configurar o modelo. Para obter mais informações e definições de membro para o arquivo *template.json*, consulte o tópico [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) (Modelos personalizados para dotnet new) e o esquema [*template.json* esquema no Repositório de Esquema JSON](http://json.schemastore.org/template).

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

O modelo foi concluído. Neste momento, você tem duas opções para a distribuição de modelos. Para continuar neste tutorial, escolha um caminho ou outro:

1. [Distribuição do NuGet](#use-nuget-distribution): instale o modelo do NuGet ou do arquivo *nupkg* local e use o modelo instalado.
2. [Distribuição de sistema de arquivos](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Usar a distribuição do NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Empacotar o modelo em um pacote NuGet

1. Crie uma pasta para o pacote NuGet. Para o tutorial, o nome da pasta *GarciaSoftware.ConsoleTemplate.CSharp* é usado e a pasta é criada dentro de uma pasta *Documentos/NuGetTemplates* no perfil do usuário. Crie uma pasta chamada *conteúdo* dentro da nova pasta de modelo para guardar os arquivos de projeto.
1. Copie o conteúdo da pasta do seu projeto, juntamente com seu arquivo *.template.config/template.json* para a pasta *conteúdo* criada.
1. Ao lado da pasta *conteúdo*, adicione um arquivo [*nuspec*](/nuget/create-packages/creating-a-package). O arquivo nuspec é um arquivo de manifesto XML que descreve o conteúdo de um pacote e orienta o processo de criação do pacote NuGet.
   
   ![Estrutura de diretórios que mostra o layout do pacote NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. Dentro de um elemento **\<packageTypes>** no arquivo *nuspec*, inclua um elemento **\<packageType>** com um valor de atributo `name` de `Template`. Tanto a pasta *conteúdo* quanto o arquivo *nuspec* devem residir no mesmo diretório. A tabela mostra os elementos mínimos do arquivo *nuspec* necessários para produzir um modelo como um pacote NuGet.

   | Elemento            | Tipo   | Descrição |
   | ------------------ | ------ | ----------- |
   | **\<authors>**     | cadeia de caracteres | Uma lista separada por vírgulas de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Os autores são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores. |
   | **\<description>** | cadeia de caracteres | Uma descrição longa do pacote para exibição de interface do usuário. |
   | **\<id>**          | cadeia de caracteres | O identificador do pacote que não diferencia maiúsculas de minúsculas, que deve ser exclusivo no nuget.org ou qualquer galeria na qual o pacote resida. As IDs não podem conter espaços nem caracteres que não sejam válidos para uma URL e geralmente seguem as regras de namespace do .NET. Consulte [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) (Escolhendo um identificador de pacote único e definindo o número de versão) para obter orientação. |
   | **\<packageType>** | cadeia de caracteres | Coloque esse elemento dentro de um elemento **\<packageTypes>** entre os elementos **\<metadata>**. Defina o atributo `name` do elemento **\<packageType>** como `Template`. |
   | **\<version>**     | cadeia de caracteres | A versão do pacote, seguindo o padrão principal.secundário.patch. Os números de versão podem incluir um sufixo de pré-lançamento, conforme descrito em [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning) (Versões de pré-lançamento). |

   Consulte o esquema de arquivo completo [nuspec](/nuget/schema/nuspec) na *referência do .nuspec*.

   O arquivo *nuspec* do tutorial é chamado *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* e contém o seguinte conteúdo:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. [Crie o pacote](/nuget/create-packages/creating-a-package#creating-the-package) usando o comando `nuget pack <PATH_TO_NUSPEC_FILE>`. O comando a seguir pressupõe que a pasta que contém os ativos do NuGet está em *C:/Usuários/\<USUÁRIO> /Documentos/Templates/GarciaSoftware.ConsoleTemplate.CSharp/*. Mas sempre que você colocar a pasta em seu sistema, o comando `nuget pack` aceita o caminho para o arquivo *nuspec*:

   ```console
   nuget pack C:/Users/<USER>/Documents/NuGetTemplates/GarciaSoftware.ConsoleTemplate.CSharp/GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publicação do pacote em nuget.org

Para publicar um pacote NuGet, siga as instruções no tópico [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) (Criar e publicar um pacote). No entanto, é recomendável que você não publique o modelo de tutorial no NuGet, pois ele nunca poderá ser excluído depois de publicado, somente removido da lista. Agora que você tem o pacote NuGet na forma de um arquivo *nupkg*, sugerimos que você siga as instruções abaixo para instalar o modelo diretamente do arquivo *nupkg* local.

### <a name="install-the-template-from-a-nuget-package"></a>Instalar o modelo de um pacote NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Instalar o modelo do arquivo *nupkg* local

Para instalar o modelo do arquivo *nupkg* produzido, use o comando `dotnet new` com a opção `-i|--install` e forneça o caminho para o arquivo *nupkg*:

```console
dotnet new -i C:/Users/<USER>/GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Instalar o modelo de um pacote NuGet armazenado em nuget.org

Se você desejar instalar um modelo de um pacote do NuGet armazenado em nuget.org, use o comando `dotnet new` com a opção `-i|--install` e forneça o nome do pacote NuGet:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> O exemplo tem fins apenas demonstrativos. Não há um pacote NuGet `GarciaSoftware.ConsoleTemplate.CSharp` em nuget.org e não é recomendável que você publique e consuma modelos de teste do NuGet. Se você executar o comando, nenhum modelo será instalado. No entanto, é possível instalar um modelo que não tenha sido publicado em nuget.org referenciando o arquivo *nupkg* diretamente no seu sistema de arquivos local, conforme mostrado na seção anterior [Install the template from the local nupgk file](#install-the-template-from-the-local-nupkg-file) (Instalar o modelo do arquivo nupkg local).

Se você quiser um exemplo dinâmico de como instalar um modelo de um pacote em nuget.org, será possível usar o [modelo NUnit 3 para dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Este modelo configura um projeto para usar testes de unidade do NUnit. Use o seguinte comando para instalá-lo:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Quando você lista os modelos com `dotnet new -l`, você vê o *Projeto de teste do NUnit 3* com um nome curto de *nunit* na lista de modelos. Você está pronto para usar o modelo na próxima seção.

![Janela do console que mostra o modelo do NUnit listado com outros modelos instalados](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a>Criar um projeto com base no modelo

Depois que o modelo for instalado do NuGet, use o modelo executando o comando `dotnet new <TEMPLATE>` do diretório em que você deseja colocar a saída do mecanismo de modelo (a menos que você esteja usando a opção `-o|--output` para especificar um diretório específico). Para obter mais informações, consulte [Opções `dotnet new`](~/docs/core/tools/dotnet-new.md#options). Forneça o nome curto do modelo diretamente para o comando `dotnet new`. Para criar um projeto do modelo NUnit, execute o seguinte comando:

```console
dotnet new nunit
```

O console mostra que o projeto é criado e que os pacotes do projeto são restaurados. Depois que o comando for executado, o projeto estará pronto para uso.

![Janela do console que mostra a saída do comando dotnet new enquanto ela cria o projeto NUnit e restaura as dependências do projeto](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Para desinstalar um modelo de um pacote NuGet armazenado em nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> O exemplo tem fins apenas demonstrativos. Não há um pacote NuGet `GarciaSoftware.ConsoleTemplate.CSharp` em nuget.org ou instalado com o SDK do .NET Core. Se você executar o comando, nenhum pacote/modelo será desinstalado e você receberá a seguinte exceção:
> 
> > Não foi possível encontrar algo para desinstalar o 'GarciaSoftware.ConsoleTemplate.CSharp' chamado.

Se você tiver instalado o [modelo NUnit 3 para dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) e desejar desinstalá-lo, use o seguinte comando:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Desinstalar o modelo de um arquivo nupkg local

Quando você desejar desinstalar o modelo, não tente usar o caminho para o arquivo *nupkg*. *A tentativa de desinstalar um modelo usando `dotnet new -u <PATH_TO_NUPKG_FILE>` falha.* Referencie o pacote por seu `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Distribuição do sistema de arquivos

Para distribuir o modelo, coloque a pasta de modelos de projeto em um local acessível aos usuários em sua rede. Use o comando `dotnet new` com a opção `-i|--install` e especifique o caminho para a pasta de modelo (a pasta de projeto que contém o projeto e a pasta *.template.config*).

O tutorial pressupõe que o modelo de projeto está armazenado na pasta *Documentos/Modelos* do perfil do usuário. Nesse local, instale o modelo com o seguinte comando substituindo \<USUÁRIO> pelo nome do perfil do usuário:

```console
dotnet new -i C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Criar um projeto com base no modelo

Depois que o modelo for instalado do sistema de arquivos, use o modelo executando o comando `dotnet new <TEMPLATE>` do diretório em que você deseja colocar a saída do mecanismo de modelo (a menos que você esteja usando a opção `-o|--output` para especificar um diretório específico). Para obter mais informações, consulte [Opções `dotnet new`](~/docs/core/tools/dotnet-new.md#options). Forneça o nome curto do modelo diretamente para o comando `dotnet new`.

Em uma nova pasta de projeto criada em *C:/Usuários/\<USUÁRIO>/Documents/Projects/MyConsoleApp*, crie um projeto do modelo `garciaconsole`:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Desinstalar o modelo

Se você tiver criado o modelo no seu sistema de arquivos local em *C:/Usuários/\<USUÁRIO>/Documentos/Templates/GarciaSoftware.ConsoleTemplate.CSharp*, desinstale-o com a opção `-u|--uninstall` e com o caminho para a pasta do modelo:

```console
dotnet new -u C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Para desinstalar o modelo do seu sistema de arquivos local, você precisa qualificar totalmente o caminho. Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.
> Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.

## <a name="see-also"></a>Consulte também

[Wiki do repositório GitHub dotnet/modelagem](https://github.com/dotnet/templating/wiki)  
[Repositório do GitHub de dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)  
[Como criar seus próprios modelos para dotnet new](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[Esquema *template.json* no Repositório de Esquema JSON](http://json.schemastore.org/template)  
