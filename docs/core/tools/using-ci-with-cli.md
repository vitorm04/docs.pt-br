---
title: "Usando ferramentas e SDK do .NET Core na CI (Integração Contínua) | Microsoft Docs"
description: "Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 0579d59e8da24428d9e174baf0cc865d62c08195
ms.lasthandoff: 03/07/2017

---

# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)

## <a name="overview"></a>Visão Geral
Este documento descreve o uso do SDK do .NET Core e suas ferramentas no servidor de build. Em geral, em um servidor de build de CI, você deseja automatizar a instalação de alguma forma. O ideal é que a automação não exija privilégios administrativos, se possível. 

Há várias opções para soluções SaaS CI. Este documento abordará duas delas muito populares, [TravisCI](https://travis-ci.org/) e [AppVeyor](https://www.appveyor.com/). Certamente há muitos outros serviços, mas os mecanismos de uso e instalação devem ser semelhantes a esses.

## <a name="installation-options-for-ci-build-servers"></a>Opções de instalação para servidores de build de CI

## <a name="using-the-native-installers"></a>Usando os instaladores nativos
Se usar os instaladores que exigem privilégios administrativos não for algo que representa um problema, os instaladores nativos de cada plataforma poderão ser usados para configurar o servidor de build. Essa abordagem, especialmente no caso de servidores de build do Linux, trazem a vantagem de instalação automática das dependências necessárias para o SDK ser executado. Os instaladores nativos também instalarão uma versão de todo o sistema do SDK, o que pode ser desejável; caso contrário, examine o [uso de script do instalador](#using-the-installer-script) descrito abaixo. 

É muito simples usar essa abordagem. Para o Linux, há a opção de usar um gerenciador de pacotes baseado no feed, tal como `apt-get` para Ubuntu ou `yum` para CentOS ou usando os pacotes em si (ou seja, DEB ou RPM). O primeiro requer configurar o feed que contém os pacotes.

Para plataformas Windows, você pode usar o MSI. 

Todos os binários podem ser encontrados na [página de Introdução ao .NET Core](https://aka.ms/dotnetcoregs) que aponta para as versões estáveis mais recentes. Se você quiser usar versões mais recentes (e possivelmente instáveis) ou a versão mais recente, use os links do [repositório da CLI](https://github.com/dotnet/cli). 

## <a name="using-the-installer-script"></a>Usando o script do instalador
Usar o script do instalador permite usar instalação não administrativa no seu servidor de build. Ele também proporciona uma automação muito fácil. O próprio script baixará e descompactará os arquivos ZIP/tarball necessários. Ele também adicionará o local de instalação no computador local para o PATH para que as ferramentas sejam disponibilizadas para invocação imediatamente após a instalação. 

O script do instalador pode ser automatizado facilmente no início do build para buscar e instalar a versão necessária do SDK. A “versão necessária” é qualquer uma que o aplicativo da versão que está sendo compilada necessitar. Você pode escolher o caminho de instalação para instalar o SDK localmente e apagá-lo após o término do build. Isso traz atomicidade e encapsulamento adicional para o processo de build. 

A referência do script de instalação pode ser encontrada no documento [dotnet-install](dotnet-install-script.md). 

### <a name="dealing-with-the-dependencies"></a>Lidando com as dependências
Usar o script do instalador significa que as dependências nativas não são instaladas automaticamente e que você precisará instalá-las se o sistema operacional que você está instalando já não as contiver. Você pode ver a lista de pré-requisitos no [repositório da CLI](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). 

## <a name="ci-services-setup-examples"></a>Exemplos de configuração de serviços de CI
As seções abaixo mostram exemplos de configurações usando as ofertas de SaaS CI mencionadas. 

### <a name="travisci"></a>TravisCI

O [travis-ci](https://travis-ci.org/) pode ser configurado para instalar o SDK do .NET Core usando a linguagem `csharp` e a chave `dotnet`.

Basta usar:

```yaml
dotnet: 1.0.0-preview2-003121
```

O Travis pode executar trabalhos `osx` (SO X 10.11) e `linux` (Ubuntu 14.04) em uma matriz de build, consulte [exemplo de .travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) para obter mais informações.

### <a name="appveyor"></a>AppVeyor

O [appveyor.com ci](https://www.appveyor.com/) tem a Visualização 2 do SDK do .NET Core já instalada na imagem do trabalho de build `Visual Studio 2015`.

Basta usar:

```yaml
os: Visual Studio 2015
```

É possível instalar uma versão específica do SDK do .NET Core, veja o [exemplo de appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) para obter mais informações. 

No exemplo, os binários do SDK do .NET Core são baixados, descompactados em um subdiretório e adicionados ao `PATH` env var.

Uma matriz de build pode ser adicionada para executar testes de integração com várias versões do SDK do .NET Core.

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.0-preview2-003121
    - CLI_VERSION: Latest

install:
  # .NET Core SDK binaries
  - ps: $url = "https://dotnetcli.blob.core.windows.net/dotnet/preview/Binaries/$($env:CLI_VERSION)/dotnet-dev-win-x64.$($env:CLI_VERSION.ToLower()).zip"
  # follow normal installation from binaries
```
