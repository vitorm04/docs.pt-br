---
title: Compilar Build .NET Core da origem
description: Saiba como compilar o .NET Core e a CLI do .NET Core no código-fonte.
keywords: .NET, .NET core, fonte, build
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload:
- dotnetcore
ms.openlocfilehash: 6aa5abd071355b1c1a367b35e9521e6b1af9c945
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="build-net-core-from-source"></a>Compilar Build .NET Core da origem

A capacidade de criar o .NET Core do seu código-fonte é importante de várias maneiras: facilita compatibilizar o .NET Core com novas plataformas, permite contribuições e correções no produto e permite a criação de versões personalizadas do .NET.
Este artigo fornece orientações para desenvolvedores que desejam criar e distribuir suas próprias versões do .NET Core.

## <a name="build-the-clr-from-source"></a>Compilar o CLR da fonte

O código-fonte para o .NET CoreCLR pode ser encontrado [no `dotnet/coreclr` repositório do GitHub](https://github.com/dotnet/coreclr/).

O build atualmente depende dos seguintes pré-requisitos:
* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* um compilador C++.

Após instalar esses pré-requisitos, você pode compilar o CLR invocando o script de compilação (`build.cmd` no Windows ou `build.sh` no Linux e no macOS) na base do [repositório do CoreCLR](https://github.com/dotnet/coreclr/).

A instalação dos componentes será diferente dependendo do sistema operacional (SO). Consulte as instruções de build do seu sistema operacional específico:

 * [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Não há nenhuma compilação cruzada entre sistemas operacionais (apenas para ARM, que é criado em X64).  
Você precisa estar na plataforma específica para criar essa plataforma.  

O build tem dois `buildTypes` principais:

 * Debug (padrão) – compila o tempo de execução com otimizações mínimas e verificações de tempo de execução adicionais (declarações). Essa redução no nível de otimização e as verificações adicionais tornam a execução do tempo de execução mais lenta, mas são importantes para a depuração. Essa é a configuração recomendada para ambientes de desenvolvimento e teste.
 * Versão – compila o tempo de execução com otimizações completas e sem verificações de tempo de execução adicionais. Isso produzirá um desempenho muito mais rápido no tempo de execução, mas pode demorar um pouco mais para compilar e pode ser difícil de depurar. Passe `release` para o script de build para selecionar este tipo de build.

Além disso, por padrão, o build não só cria os executáveis de tempo de execução, mas também compila todos os testes.
Há alguns testes, tomando a uma quantidade significativa de tempo que não é necessária se quiser apenas experimentar as alterações.
Você pode ignorar os builds de testes, adicionando o argumento `skiptests` ao script de build, como no exemplo a seguir (substitua `.\build` por `./build.sh` em computadores Unix):

```bat
    .\build skiptests 
```

O exemplo anterior mostrou como compilar o tipo `Debug`, que tem verificações de tempo de desenvolvimento (declarações) habilitadas e otimizações desabilitadas. Para criar o tipo de versão (velocidade total), faça o seguinte:

```bat 
    .\build release skiptests
```

É possível encontrar mais opções de build com build usando a opção -? ou o qualificador -help.   

### <a name="using-your-build"></a>Usando seu Build

O build coloca todos os arquivos gerados sob o diretório `bin` na base do repositório.
Há um diretório *bin\Log* que contém os arquivos de log gerados durante o build (mais útil quando o build falha).
A saída real é colocada em um diretório *bin\Product\[plataforma]. [ Arquitetura de CPU]. [tipo de build]* , como *bin\Product\Windows_NT.x64.Release*.

Embora a saída “bruta” do build, às vezes, seja útil, normalmente, você só está interessado nos pacotes NuGet, que são colocados no subdiretório `.nuget\pkg` do diretório de saída anterior.

Há duas técnicas básicas para usar o novo tempo de execução:

 1. **Use dotnet.exe e NuGet para compor um aplicativo**.
    Consulte [Usando sua compilação](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) para obter instruções sobre como criar um programa que usa o novo tempo de execução usando pacotes de NuGet que acabaram de ser criados e a interface de linha de comando 'dotnet' (CLI). Essa técnica é a maneira esperada com que desenvolvedores que não sejam de tempo de execução provavelmente consumirão o novo tempo de execução.    

 2. **Use corerun.exe para executar um aplicativo usando DLLs desagrupadas**.
    Esse repositório também define um host simples chamado corerun.exe que NÃO tem nenhuma dependência do NuGet.
    É necessário informar ao host onde obter as DLLs necessárias que você realmente usa, além de reuni-las manualmente.
    Essa técnica é usada por todos os testes no [repositório do CoreCLR](https://github.com/dotnet/coreclr) e é útil para um loop local rápido 'edit-compile-debug', como os testes de unidade preliminar.
    Consulte [Executando aplicativos do .NET Core com CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) para obter detalhes sobre como usar essa técnica.

## <a name="build-the-cli-from-source"></a>Compilar a CLI da fonte

O código-fonte para a CLI do .NET Core pode ser encontrado [no `dotnet/cli` repositório no GitHub](https://github.com/dotnet/cli/).

Para criar a CLI do .NET Core, será necessário os seguintes itens instalados em seu computador.

* Windows e Linux:
    - git no CAMINHO
* macOS:
    - git no CAMINHO
    - Xcode
    - Openssl

Para criar, execute `build.cmd` no Windows ou `build.sh` no Linux e macOS da raiz. Se não desejar executar testes, execute `build.cmd /t:Compile` ou `./build.sh /t:Compile`. Para criar a CLI em macOS serra, é necessário definir a variável de ambiente DOTNET_RUNTIME_ID executando `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Usando seu build

Use o `dotnet` executável de *artefatos/{os}-{arch}/stage2* para testar a CLI recém-criada. Se desejar usar a saída de build ao invocar `dotnet` do console atual, também é possível adicionar *artefatos/{os}-{arch}/stage2* ao CAMINHO.

## <a name="see-also"></a>Consulte também

* [Common Language Runtime do .NET Core (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [Guia do desenvolvedor da CLI do .NET Core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [Pacote de distribuição do .NET Core](./distribution-packaging.md)
