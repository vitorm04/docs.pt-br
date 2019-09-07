---
title: Pacote de distribuição do .NET Core
description: Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394154"
---
# <a name="net-core-distribution-packaging"></a>Pacote de distribuição do .NET Core

À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele. Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET. Este artigo é útil para usuários que estão:

- Tentando criar o .NET Core com base na origem.
- Querendo fazer alterações à CLI do .NET Core que poderiam afetar o layout resultante ou os pacotes produzidos.

## <a name="disk-layout"></a>Layout de disco

Quando instalado, o .NET Core consiste em vários componentes que são dispostos da seguinte maneira no sistema de arquivos:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** O host (também conhecido como o "muxer") tem duas funções distintas: ativar um tempo de execução para iniciar um aplicativo e ativar um SDK para enviar comandos a ele. O host é um executável nativo (`dotnet.exe`).

Embora haja um único host, a maioria dos outros componentes está em diretórios com controle de versão (2,3,5,6). Isso significa que várias versões podem estar presentes no sistema, pois são instaladas lado a lado.

- (2) **host/fxr/\<versão do fxr>** contém a lógica de resolução do framework usada pelo host. O host usa o hostfxr mais recente instalado. O hostfxr é responsável por selecionar o tempo de execução apropriado ao executar um aplicativo .NET Core. Por exemplo, um aplicativo criado para o tempo de execução do .NET Core 2.0.0 usa o 2.0.5 quando ele está disponível. Da mesma forma, o hostfxr seleciona o SDK adequado durante o desenvolvimento.

- (3) **sdk/\<versão do sdk>** O SDK (também conhecido como "as ferramentas") é um conjunto de ferramentas gerenciadas usado para escrever e compilar aplicativos e bibliotecas do .NET Core. O SDK inclui a CLI (interface de linha de comando) do .NET Core, os compiladores de linguagens gerenciadas, o MSBuild, tarefas e destinos de compilação associados, o NuGet, novos modelos de projeto e assim por diante.

- (4) **sdk/NuGetFallbackFolder** contém um cache de pacotes do NuGet usados por um SDK durante a operação de restauração, como ao executar `dotnet restore` ou `dotnet build /t:Restore`. Esta pasta é usada somente antes do .NET Core 3,0. Ele não pode ser compilado da origem, pois contém ativos binários pré-criados do `nuget.org`.

A pasta **compartilhada** contém estruturas. Uma estrutura compartilhada fornece um conjunto de bibliotecas em um local central para que elas possam ser usadas por aplicativos diferentes.

- (5) **shared/Microsoft.NETCore.App/\<versão do tempo de execução>** Essa estrutura contém o tempo de execução do .NET Core e as bibliotecas gerenciadas que dão suporte a ele.

- (6) **Shared/Microsoft. AspNetCore. { O aplicativo, All}\</aspnetcore versão >** contém as bibliotecas de ASP.NET Core. As bibliotecas em `Microsoft.AspNetCore.App` são desenvolvidas e têm suporte como parte do projeto .NET Core. As bibliotecas em `Microsoft.AspNetCore.All` são um superconjunto que também contém bibliotecas de terceiros.

- (7) **Shared/Microsoft. desktop. app/\<desktop versão do aplicativo >** contém as bibliotecas da área de trabalho do Windows. Isso não está incluído em plataformas não Windows.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** são a licença do .NET Core e licenças de bibliotecas de terceiros usadas no .NET Core, respectivamente.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` é a página de manual do dotnet. `dotnet` é um symlink ao host(1) dotnet. Esses arquivos são instalados em locais bem conhecidos para a integração do sistema.

- (11, 12) **Microsoft. NetCore. app. ref, Microsoft. AspNetCore. app. ref** descreve a API de uma `x.y` versão do .NET Core e ASP.NET Core respectivamente. Esses pacotes são usados durante a compilação para essas versões de destino.

- (13) **Microsoft. NetCore. app. host.\< o RID >** contém um binário nativo para `rid`a plataforma. Esse binário é um modelo ao compilar um aplicativo .NET Core em um binário nativo para essa plataforma.

- (14) **Microsoft. WindowsDesktop. app. ref** descreve a API da `x.y` versão dos aplicativos da área de trabalho do Windows. Esses arquivos são usados durante a compilação para esse destino. Isso não é fornecido em plataformas não Windows.

- (15) **netstandard. library. ref** descreve a API do `x.y` netpadrão. Esses arquivos são usados durante a compilação para esse destino.

- (16) **/etc/dotnet/install_location** é um arquivo que contém o caminho completo para a pasta que contém o `dotnet` binário do host. O caminho pode ser encerrado com uma nova linha. Não é necessário adicionar esse arquivo quando a raiz é `/usr/share/dotnet`.

- (17) **modelos** contém os modelos usados pelo SDK. Por exemplo, `dotnet new` localiza modelos de projeto aqui.

## <a name="recommended-packages"></a>Pacotes recomendados

O controle de versão do .NET Core é baseado nos números de versão `[major].[minor]` do componente de tempo de execução.
A versão do SDK usa o mesmo `[major].[minor]` e tem um `[patch]` independente que combina as semânticas de recurso e de patch para o SDK.
Por exemplo: O SDK versão 2.2.302 é a segunda versão de patch da terceira versão do recurso do SDK que dá suporte ao tempo de execução 2.2. Para obter mais informações sobre como o controle de versão funciona, veja [Visão geral do controle de versão do .NET Core](../versions/index.md).

Alguns pacotes incluem parte do número de versão no nome deles. Isso permite que você instale uma versão específica.
O restante da versão não está incluído no nome da versão. Isso permite ao gerenciador de pacotes de SO atualize os pacotes (por exemplo, instalando automaticamente correções de segurança). Gerenciadores de pacotes com suporte são específicos do Linux.

Veja a seguir uma lista dos pacotes recomendados:

- `dotnet-sdk-[major].[minor]`-Instala o SDK mais recente para tempo de execução específico
  - **Versão:** \<versão de tempo de execução >
  - **Exemplo:** dotnet-sdk-2,1
  - **Terá** (3),(4)
  - **Dependências:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-Instala um tempo de execução de ASP.NET Core específico
  - **Versão:** \<> a versão de tempo de execução aspnetcore
  - **Exemplo:** aspnetcore-runtime-2,1
  - **Terá** (6)
  - **Dependências:** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(Opcional)_ -instala as dependências para executar aplicativos independentes
  - **Versão:** \<versão de tempo de execução >
  - **Exemplo:** dotnet-Runtime-deps-2,1
  - **Dependências:** _dependências específicas do distribuição_

- `dotnet-runtime-[major].[minor]`-Instala um tempo de execução específico
  - **Versão:** \<versão de tempo de execução >
  - **Exemplo:** dotnet-tempo de execução-2,1
  - **Terá** (5)
  - **Dependências:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr`-dependência
  - **Versão:** \<versão de tempo de execução >
  - **Exemplo:** dotnet-hostfxr
  - **Terá** (2)
  - **Dependências:** `host:<runtime version>+`

- `dotnet-host`-dependência
  - **Versão:** \<versão de tempo de execução >
  - **Exemplo:** dotnet-host
  - **Terá** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-dependência
  - **Versão:** \<versão de tempo de execução >
  - **Terá** 13

- `dotnet-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente
  - **Versão:** \<versão de tempo de execução >
  - **Terá** 12

- `aspnetcore-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente
  - **Versão:** \<> a versão de tempo de execução aspnetcore
  - **Terá** 11

- `netstandard-targeting-pack-[major].[minor]`-Permite direcionar uma versão do netstandard
  - **Versão:** \<versão do SDK >
  - **Terá** 15

- `dotnet-templates-[major].[minor]`
  - **Versão:** \<versão do SDK >
  - **Terá** 15

O `dotnet-runtime-deps-[major].[minor]` requer a compreensão das _dependências específicas do distribuição_. Como o sistema de compilação distribuição pode ser capaz de derivar isso automaticamente, o pacote é opcional; nesse caso, essas dependências são adicionadas diretamente ao `dotnet-runtime-[major].[minor]` pacote.

Quando o conteúdo do pacote está sob uma pasta com versão, o `[major].[minor]` nome do pacote corresponde ao nome da pasta com versão. Para todos os pacotes, exceto `netstandard-targeting-pack-[major].[minor]`o, isso também corresponde à versão do .NET Core.

As dependências entre os pacotes devem usar um requisito _igual ou maior que_ a versão. Por exemplo, `dotnet-sdk-2.2:2.2.401` requer `aspnetcore-runtime-2.2 >= 2.2.6`. Isso possibilita que o usuário Atualize sua instalação por meio de um pacote raiz (por exemplo, `dnf update dotnet-sdk-2.2`).

A maioria das distribuições exigem que todos os artefatos sejam compilados da origem. Isso tem algum impacto nos pacotes:

- As bibliotecas de terceiros em `shared/Microsoft.AspNetCore.All` não podem ser criadas facilmente usando o código-fonte. Portanto, essa pasta é omitida do pacote `aspnetcore-runtime`.

- O `NuGetFallbackFolder` é populado usando os artefatos binários de `nuget.org`. Ele deve permanecer vazio.

Vários pacotes `dotnet-sdk` podem fornecer os mesmos arquivos para o `NuGetFallbackFolder`. Para evitar problemas com o gerenciador de pacotes, esses arquivos devem ser idênticos (soma de verificação, data de modificação e assim por diante).

## <a name="building-packages"></a>Compilando pacotes

O repositório [dotnet/source-build](https://github.com/dotnet/source-build) fornece instruções sobre como compilar um tarball de origem do SDK do .NET Core e todos os seus componentes. A saída do repositório de build de origem corresponde o layout descrito na primeira seção deste artigo.
