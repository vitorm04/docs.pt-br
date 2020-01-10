---
title: Compilar Build .NET Core da origem
description: Saiba como compilar o .NET Core e a CLI do .NET Core no código-fonte.
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740924"
---
# <a name="build-net-core-from-source"></a>Compilar Build .NET Core da origem

A capacidade de criar o .NET Core do seu código-fonte é importante de várias maneiras: facilita compatibilizar o .NET Core com novas plataformas, permite contribuições e correções no produto e permite a criação de versões personalizadas do .NET.
Este artigo fornece orientações para desenvolvedores que desejam criar e distribuir suas próprias versões do .NET Core.

## <a name="build-the-clr-from-source"></a>Compilar o CLR da fonte

O código-fonte para o CoreCLR do .NET pode ser encontrado no repositório [dotnet/tempo de execução](https://github.com/dotnet/runtime/) no github.

O build atualmente depende dos seguintes pré-requisitos:

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- um compilador C++.

Depois de instalar esses pré-requisitos, você pode criar o CLR invocando o script de compilação (`build.cmd` no Windows ou `build.sh` no Linux e no macOS) na base do repositório [dotnet/tempo de execução](https://github.com/dotnet/runtime/) .

A instalação dos componentes será diferente dependendo do sistema operacional (SO). Confira as instruções de build do seu sistema operacional específico:

- [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Não há nenhuma compilação cruzada entre sistemas operacionais (apenas para ARM, que é criado em X64).  
Você precisa estar na plataforma específica para criar essa plataforma.  

O build tem dois `buildTypes` principais:

- Debug (padrão) – compila o runtime com otimizações mínimas e verificações de runtime adicionais (declarações). Essa redução no nível de otimização e as verificações adicionais tornam a execução do runtime mais lenta, mas são importantes para a depuração. Essa é a configuração recomendada para ambientes de desenvolvimento e teste.
- Versão – compila o runtime com otimizações completas e sem verificações de runtime adicionais. Isso produzirá um desempenho muito mais rápido em tempo de execução, mas pode levar um pouco mais para compilar e pode ser difícil de depurar. Passe `release` para o script de build para selecionar este tipo de build.

Além disso, por padrão, o build não só cria os executáveis de runtime, mas também compila todos os testes.
Há alguns testes, tomando a uma quantidade significativa de tempo que não é necessária se quiser apenas experimentar as alterações.
Você pode ignorar os builds de testes, adicionando o argumento `skiptests` ao script de build, como no exemplo a seguir (substitua `.\build` por `./build.sh` em computadores UNIX):

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

Há duas técnicas básicas para usar o novo runtime:

 1. **Use dotnet.exe e NuGet para compor um aplicativo**.
    Confira [Usando sua compilação](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) para obter instruções sobre como criar um programa que usa o novo runtime usando pacotes de NuGet que acabaram de ser criados e a interface de linha de comando 'dotnet' (CLI). Essa técnica é a maneira esperada com que desenvolvedores que não sejam de runtime provavelmente consumirão o novo runtime.

 2. **Use corerun.exe para executar um aplicativo usando DLLs não empacotadas**.
    Esse repositório também define um host simples chamado corerun.exe que NÃO tem nenhuma dependência do NuGet.
    É necessário informar ao host onde obter as DLLs necessárias que você realmente usa, além de reuni-las manualmente.
    Essa técnica é usada por todos os testes no repositório [dotnet/tempo de execução](https://github.com/dotnet/runtime) e é útil para o loop "Edit-compile-debug" local rápido, como o teste de unidade preliminar.
    Consulte [Executando aplicativos do .NET Core com CoreRun.exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) para obter detalhes sobre como usar essa técnica.

## <a name="build-the-cli-from-source"></a>Compilar a CLI da fonte

O código-fonte para a CLI do .NET Core pode ser encontrado no repositório [dotnet/cli](https://github.com/dotnet/cli/) no GitHub.

Para criar a CLI do .NET Core, será necessário os seguintes itens instalados em seu computador.

- Windows e Linux:
  - git no CAMINHO
- macOS:
  - git no CAMINHO
  - Xcode
  - Openssl

Para criar, execute `build.cmd` no Windows ou `build.sh` no Linux e macOS da raiz. Se não desejar executar testes, execute `build.cmd -t:Compile` ou `./build.sh -t:Compile`. Para criar a CLI em macOS Sierra, é necessário definir a variável de ambiente DOTNET_RUNTIME_ID executando `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Usando seu build

Use o `dotnet` executável de *artefatos/{os}-{arch}/stage2* para testar a CLI recém-criada. Se você deseja usar a saída de build ao invocar `dotnet` do console atual, também é possível adicionar *artefatos/{os}-{arch}/stage2* ao CAMINHO.

## <a name="see-also"></a>Veja também

- [Tempo de execução do .NET](https://github.com/dotnet/runtime/blob/master/README.md)
- [Guia do Desenvolvedor da CLI do .NET Core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [Pacote de distribuição do .NET Core](./distribution-packaging.md)
