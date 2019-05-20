---
title: Pacote de distribuição do .NET Core
description: Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: b961d84053dc41e75e002c8c12419fdef99ded4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585252"
---
# <a name="net-core-distribution-packaging"></a>Pacote de distribuição do .NET Core

À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele. Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET. Este artigo é útil para usuários que estão:

* Tentando criar o .NET Core com base na origem.
* Querendo fazer alterações à CLI do .NET Core que poderiam afetar o layout resultante ou os pacotes produzidos.

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
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** O host (também conhecido como o "muxer") tem duas funções distintas: ativar um tempo de execução para iniciar um aplicativo e ativar um SDK para enviar comandos a ele. O host é um executável nativo (`dotnet.exe`).

Embora haja um único host, a maioria dos outros componentes está em diretórios com controle de versão (2,3,5,6). Isso significa que várias versões podem estar presentes no sistema, pois são instaladas lado a lado.

- (2) **host/fxr/\<versão do fxr>** contém a lógica de resolução do framework usada pelo host. O host usa o hostfxr mais recente instalado. O hostfxr é responsável por selecionar o tempo de execução apropriado ao executar um aplicativo .NET Core. Por exemplo, um aplicativo criado para o tempo de execução do .NET Core 2.0.0 usa o 2.0.5 quando ele está disponível. Da mesma forma, o hostfxr seleciona o SDK adequado durante o desenvolvimento.

- (3) **sdk/\<versão do sdk>** O SDK (também conhecido como "as ferramentas") é um conjunto de ferramentas gerenciadas usado para escrever e compilar aplicativos e bibliotecas do .NET Core. O SDK inclui a CLI (interface de linha de comando) do .NET Core, os compiladores de linguagens gerenciadas, o MSBuild, tarefas e destinos de compilação associados, o NuGet, novos modelos de projeto e assim por diante.

- (4) **sdk/NuGetFallbackFolder** contém um cache de pacotes do NuGet usados por um SDK durante a operação de restauração, como ao executar `dotnet restore` ou `dotnet build /t:Restore`.

A pasta **compartilhada** contém estruturas. Uma estrutura compartilhada fornece um conjunto de bibliotecas em um local central para que elas possam ser usadas por aplicativos diferentes.

- (5) **shared/Microsoft.NETCore.App/\<versão do tempo de execução>** Essa estrutura contém o tempo de execução do .NET Core e as bibliotecas gerenciadas que dão suporte a ele.

- (6,7) **shared/Microsoft.AspNetCore.{App,All}/\<versão do aspnetcore>** contém as bibliotecas do ASP.NET Core. As bibliotecas em `Microsoft.AspNetCore.App` são desenvolvidas e têm suporte como parte do projeto .NET Core. As bibliotecas em `Microsoft.AspNetCore.All` são um superconjunto que também contém bibliotecas de terceiros.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** são a licença do .NET Core e licenças de bibliotecas de terceiros usadas no .NET Core, respectivamente.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` é a página de manual do dotnet. `dotnet` é um symlink ao host(1) dotnet. Esses arquivos são instalados em locais bem conhecidos para a integração do sistema.

## <a name="recommended-packages"></a>Pacotes recomendados

O controle de versão do .NET Core é baseado nos números de versão `[major].[minor]` do componente de tempo de execução.
A versão do SDK usa o mesmo `[major].[minor]` e tem um `[patch]` independente que combina as semânticas de recurso e de patch para o SDK.
Por exemplo: O SDK versão 2.2.302 é a segunda versão de patch da terceira versão do recurso do SDK que dá suporte ao tempo de execução 2.2. Para obter mais informações sobre como o controle de versão funciona, veja [Visão geral do controle de versão do .NET Core](../versions/index.md).

Alguns pacotes incluem parte do número de versão no nome deles. Isso permite que você instale uma versão específica.
O restante da versão não está incluído no nome da versão. Isso permite ao gerenciador de pacotes de SO atualize os pacotes (por exemplo, instalando automaticamente correções de segurança). Gerenciadores de pacotes com suporte são específicos do Linux.

A tabela a seguir mostra os pacotes recomendados:

| Nome                                    | Exemplo                | Caso de uso: Instalar...           | Contém           | Dependências                                   | Versão            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[principal]                      | dotnet-sdk-2           | SDK mais recente para a versão principal do tempo de execução    |                    | dotnet-sdk-[principal].[secundáriamaisrecente]               | \<versão do SDK>     |
| dotnet-sdk-[principal].[secundária]              | dotnet-sdk-2.1         | SDK mais recente para o tempo de execução específico |                    | dotnet-sdk-[principal].[secundária].[recurso mais recente do SDK]xx | \<versão do SDK>     |
| dotnet-sdk-[principal].[secundária].[recurso do SDK]xx | dotnet-sdk-2.1.3xx     | Versão específica do recurso de SDK    | (3),(4)            | aspnetcore-runtime-[principal].[secundária]             | \<versão do SDK>     |
| aspnetcore-runtime-[principal].[secundária]      | aspnetcore-runtime-2.1 | Tempo de execução específico do ASP.NET Core   | (6),[(7)]          | dotnet-runtime-[principal].[secundária]                 | \<versão de tempo de execução> |
| dotnet-runtime-[principal].[secundária]          | dotnet-runtime-2.1     | Tempo de execução específico                | (5)                | host fxr:\<versão de tempo de execução>+                   | \<versão de tempo de execução> |
| dotnet-host-fxr                         | dotnet-host-fxr        | _dependência_                    | (2)                | host:\<versão de tempo de execução>+                       | \<versão de tempo de execução> |
| dotnet-host                             | dotnet-host            | _dependência_                    | (1),(8),(9),(10)   |                                                | \<versão de tempo de execução> |

A maioria das distribuições exigem que todos os artefatos sejam compilados da origem. Isso tem algum impacto nos pacotes:

- As bibliotecas de terceiros em `shared/Microsoft.AspNetCore.All` não podem ser criadas facilmente usando o código-fonte. Portanto, essa pasta é omitida do pacote `aspnetcore-runtime`.

- O `NuGetFallbackFolder` é populado usando os artefatos binários de `nuget.org`. Ele deve permanecer vazio.

Vários pacotes `dotnet-sdk` podem fornecer os mesmos arquivos para o `NuGetFallbackFolder`. Para evitar problemas com o gerenciador de pacotes, esses arquivos devem ser idênticos (soma de verificação, data de modificação e assim por diante).

### <a name="preview-versions"></a>Versões prévias

Os mantenedores do pacote podem decidir fornecer versões prévias da estrutura compartilhada e do SDK. Versões prévias podem ser fornecidas usando os pacotes `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]` ou `dotnet-runtime-[major].[minor]`. Para versões prévias, a versão principal do pacote deve ser definida como zero. Dessa forma, a versão final é instalada como uma atualização do pacote.

### <a name="patch-packages"></a>Pacotes de patch

Uma vez que uma versão de patch de um pacote pode causar uma alteração da falha, um mantenedor de pacote pode desejar fornecer _pacotes de patch_. Esses pacotes permitem que você instale uma versão de patch específica que não é atualizada automaticamente. Só use pacotes de patch em circunstâncias raras, pois eles não são atualizados com correções (de segurança).

A tabela a seguir mostra os pacotes recomendados e os **pacotes de patch**:

| Nome                                           | Exemplo                  | Contém         | Dependências                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[principal]                             | dotnet-sdk-2             |                  | dotnet-sdk-[principal].[secundária mais recente do sdk]                     |
| dotnet-sdk-[principal].[secundária]                     | dotnet-sdk-2.1           |                  | dotnet-sdk-[principal].[secundária].[recurso mais recente do SDK]xx            |
| dotnet-sdk-[principal].[secundária].[recurso do SDK]xx        | dotnet-sdk-2.1.3xx       |                  | dotnet-sdk-[principal].[secundária].[patch mais recente do sdk]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore-runtime-[principal].[secundária].[patch de tempo de execução do sdk]    |
| aspnetcore-runtime-[principal].[secundária]             | aspnetcore-runtime-2.1   |                  | aspnetcore-runtime-[principal].[secundária].[patch de tempo de execução mais recente] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[principal].[secundária]                 | dotnet-runtime-2.1       |                  | dotnet-runtime-[principal].[secundária].[patch de tempo de execução mais recente]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host fxr:\<versão de tempo de execução>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | host:\<versão de tempo de execução>+                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

Uma alternativa ao uso de pacotes de patch é _fixar_ os pacotes para uma versão específica usando o gerenciador de pacotes. Para evitar afetar outros aplicativos/usuários, esses aplicativos podem ser compilados e implantados em um contêiner.

## <a name="building-packages"></a>Compilando pacotes

O repositório [dotnet/source-build](https://github.com/dotnet/source-build) fornece instruções sobre como compilar um tarball de origem do SDK do .NET Core e todos os seus componentes. A saída do repositório de build de origem corresponde o layout descrito na primeira seção deste artigo.
