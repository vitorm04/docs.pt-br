---
title: Pacote de distribuição do .NET Core
description: Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 41e8729d3058c2e3e1ea1cab9a8f28b3062bb93c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145641"
---
# <a name="net-core-distribution-packaging"></a>Pacote de distribuição do .NET Core

À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele. Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET.

## <a name="disk-layout"></a>Layout de disco

Quando instalado, o .NET Core consiste em vários componentes que estão dispostos no sistema de arquivos conforme demonstrado a seguir:

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

Embora haja um único host, a maioria dos outros componentes está em diretórios com controle de versão (2,3,5,6). Isso significa que muitas versões podem estar presentes no sistema, já que elas são instaladas lado a lado.

- (2) **host/fxr/\<versão do fxr>** contém a lógica de resolução do framework usada pelo host. O host usa o hostfxr mais recente instalado. O hostfxr é responsável por selecionar o tempo de execução apropriado ao executar um aplicativo .NET Core. Por exemplo, um aplicativo compilado para .NET Core 2.0.0 usará o tempo de execução 2.0.5 quando ele estiver disponível. Da mesma forma, o hostfxr seleciona o SDK adequado durante o desenvolvimento.

- (3) **sdk/\<versão do SDK>** (também conhecido como "as ferramentas") é um conjunto de ferramentas gerenciadas que pode ser usado para gravar e compilar bibliotecas e aplicativos do .NET Core. O SDK inclui a CLI, o compilador Roslyn, MSBuild e tarefas de compilação e direcionamentos associados, o NuGet, novos modelos de projeto etc.

- (4) **sdk/NuGetFallbackFolder** contém um cache de pacotes do NuGet usados por um SDK durante a etapa `dotnet restore`.

A pasta **compartilhada** contém estruturas. Uma estrutura compartilhada fornece um conjunto de bibliotecas em um local central para que elas possam ser usadas por aplicativos diferentes.

- (5) **shared/Microsoft.NETCore.App/\<versão do tempo de execução>** Essa estrutura contém o tempo de execução do .NET Core e as bibliotecas gerenciadas que dão suporte a ele.

- (6,7) **shared/Microsoft.AspNetCore.{App,All}/\<versão do aspnetcore>** contém as bibliotecas do ASP.NET Core. As bibliotecas em `Microsoft.AspNetCore.App` são desenvolvidas e têm suporte como parte do projeto .NET Core. As bibliotecas em `Microsoft.AspNetCore.All` são um superconjunto que também contém bibliotecas de terceiros.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** são a licença do .NET Core e licenças de bibliotecas de terceiros usadas no .NET Core.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` é a página de manual do dotnet. `dotnet` é um symlink ao host(1) dotnet. Esses arquivos são instalados em locais bem conhecidos para a integração do sistema.

## <a name="recommended-packages"></a>Pacotes recomendados

O controle de versão do .NET Core é baseado nos números de versão `[major].[minor]` do componente de tempo de execução.
A versão do SDK usa os mesmos `[major].[minor]` e tem um `[patch]` independente que combina as semânticas de recurso e de patch para o SDK.
Por exemplo: o SDK versão 2.2.302 é a 2ª versão de patch da versão da 3ª versão do recurso do SDK que é compatível com o tempo de execução 2.2.

Alguns pacotes incluem parte do número de versão no nome deles. Isso permite que o usuário final instale uma versão específica.
O restante da versão não está incluído no nome da versão. Isso permite que gerenciador de pacotes do sistema operacional atualize os pacotes (por exemplo, instalar automaticamente correções de segurança).

As tabelas a seguir mostra os pacotes recomendados.

| Nome                                    | Exemplo                | Caso de uso: instalar...           | Contém           | Dependências                                   | Versão            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[principal]                      | dotnet-sdk-2           | SDK mais recente para a versão principal do tempo de execução    |                    | dotnet-sdk-[principal].[secundáriamaisrecente]               | \<versão do SDK>     |
| dotnet-sdk-[principal].[secundária]              | dotnet-sdk-2.1         | SDK mais recente para o tempo de execução específico |                    | dotnet-sdk-[principal].[secundária].[recurso mais recente do SDK]xx | \<versão do SDK>     |
| dotnet-sdk-[principal].[secundária].[recurso do SDK]xx | dotnet-sdk-2.1.3xx     | Versão específica do recurso de SDK    | (3),(4)            | aspnetcore-runtime-[principal].[secundária]             | \<versão do SDK>     |
| aspnetcore-runtime-[principal].[secundária]      | aspnetcore-runtime-2.1 | Tempo de execução específico do ASP.NET Core   | (6),[(7)]          | dotnet-runtime-[principal].[secundária]                 | \<versão de tempo de execução> |
| dotnet-runtime-[principal].[secundária]          | dotnet-runtime-2.1     | Tempo de execução específico                | (5)                | host fxr:\<versão de tempo de execução>+                   | \<versão de tempo de execução> |
| dotnet-host-fxr                         | dotnet-host-fxr        | _dependência_                    | (2)                | host:\<versão de tempo de execução>+                       | \<versão de tempo de execução> |
| dotnet-host                             | dotnet-host            | _dependência_                    | (1),(8),(9),(10)   |                                                | \<versão de tempo de execução> |

A maioria das distribuições exigem que todos os artefatos sejam compilados da origem. Isso tem algum impacto nos pacotes:

- As bibliotecas de terceiros sob `shared/Microsoft.AspNetCore.All` não podem ser criadas da origem com facilidade. Portanto, essa pasta é omitida do pacote `aspnetcore-runtime`.

- O `NuGetFallbackFolder` é populado usando os artefatos binários de `nuget.org`. Ele deve permanecer vazio.

Vários pacotes `dotnet-sdk` podem fornecer os mesmos arquivos para o `NuGetFallbackFolder`. Para evitar problemas com o gerenciador de pacotes, esses arquivos devem ser idênticos (soma de verificação, data de modificação, etc.).

#### <a name="preview-versions"></a>Versões prévias

Os mantenedores do pacote podem decidir fornecer versões prévias da estrutura compartilhada e do SDK. É possível fornecer versões prévias usando os pacotes `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]` e `dotnet-runtime-[major].[minor]`. Para versões prévias, a versão principal do pacote deve ser definida como zero. Dessa forma, a versão final será instalada como uma atualização do pacote.

#### <a name="patch-packages"></a>Pacotes de patch

Já que uma versão de patch de um pacote pode causar uma alteração significativa, é conveniente que um mantenedor de pacote forneça _pacotes de patch_. Esses pacotes permitem instalar uma versão de patch específica, que não é atualizada automaticamente. Pacotes de patch deverão ser usados somente em circunstâncias raras, já que elas não serão atualizadas com correções (de segurança).

A tabela a seguir mostra os pacotes e **pacotes de patch** recomendados.

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
