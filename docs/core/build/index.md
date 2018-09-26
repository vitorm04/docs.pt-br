---
title: Compilar Build .NET Core da origem
description: Saiba como compilar o .NET Core e a CLI do .NET Core no código-fonte.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: fa9c193ea4088f04745bdadc6040552e18c0858a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47188983"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="e889f-103">Compilar Build .NET Core da origem</span><span class="sxs-lookup"><span data-stu-id="e889f-103">Build .NET Core from source</span></span>

<span data-ttu-id="e889f-104">A capacidade de criar o .NET Core do seu código-fonte é importante de várias maneiras: facilita compatibilizar o .NET Core com novas plataformas, permite contribuições e correções no produto e permite a criação de versões personalizadas do .NET.</span><span class="sxs-lookup"><span data-stu-id="e889f-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="e889f-105">Este artigo fornece orientações para desenvolvedores que desejam criar e distribuir suas próprias versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e889f-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="e889f-106">Compilar o CLR da fonte</span><span class="sxs-lookup"><span data-stu-id="e889f-106">Build the CLR from source</span></span>

<span data-ttu-id="e889f-107">O código-fonte para o .NET CoreCLR pode ser encontrado no repositório [dotnet/coreclr](https://github.com/dotnet/coreclr/) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="e889f-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="e889f-108">O build atualmente depende dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="e889f-108">The build currently depends on the following prerequisites:</span></span>

* [<span data-ttu-id="e889f-109">Git</span><span class="sxs-lookup"><span data-stu-id="e889f-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="e889f-110">CMake</span><span class="sxs-lookup"><span data-stu-id="e889f-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="e889f-111">Python</span><span class="sxs-lookup"><span data-stu-id="e889f-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="e889f-112">um compilador C++.</span><span class="sxs-lookup"><span data-stu-id="e889f-112">a C++ compiler.</span></span>

<span data-ttu-id="e889f-113">Após instalar esses pré-requisitos, você poderá compilar o CLR ao invocar o script de build (`build.cmd` no Windows ou `build.sh` no Linux e no macOS) na base do repositório [dotnet/coreclr](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="e889f-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="e889f-114">A instalação dos componentes será diferente dependendo do sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="e889f-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="e889f-115">Consulte as instruções de build do seu sistema operacional específico:</span><span class="sxs-lookup"><span data-stu-id="e889f-115">See the build instructions for your specific OS:</span></span>

* [<span data-ttu-id="e889f-116">Windows</span><span class="sxs-lookup"><span data-stu-id="e889f-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [<span data-ttu-id="e889f-117">Linux</span><span class="sxs-lookup"><span data-stu-id="e889f-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [<span data-ttu-id="e889f-118">macOS</span><span class="sxs-lookup"><span data-stu-id="e889f-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [<span data-ttu-id="e889f-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="e889f-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [<span data-ttu-id="e889f-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="e889f-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="e889f-121">Não há nenhuma compilação cruzada entre sistemas operacionais (apenas para ARM, que é criado em X64).</span><span class="sxs-lookup"><span data-stu-id="e889f-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="e889f-122">Você precisa estar na plataforma específica para criar essa plataforma.</span><span class="sxs-lookup"><span data-stu-id="e889f-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="e889f-123">O build tem dois `buildTypes` principais:</span><span class="sxs-lookup"><span data-stu-id="e889f-123">The build has two main `buildTypes`:</span></span>

* <span data-ttu-id="e889f-124">Debug (padrão) – compila o tempo de execução com otimizações mínimas e verificações de tempo de execução adicionais (declarações).</span><span class="sxs-lookup"><span data-stu-id="e889f-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="e889f-125">Essa redução no nível de otimização e as verificações adicionais tornam a execução do tempo de execução mais lenta, mas são importantes para a depuração.</span><span class="sxs-lookup"><span data-stu-id="e889f-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="e889f-126">Essa é a configuração recomendada para ambientes de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="e889f-126">This is the recommended setting for development and testing environments.</span></span>
* <span data-ttu-id="e889f-127">Versão – compila o tempo de execução com otimizações completas e sem verificações de tempo de execução adicionais.</span><span class="sxs-lookup"><span data-stu-id="e889f-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="e889f-128">Isso produzirá um desempenho muito mais rápido no tempo de execução, mas pode demorar um pouco mais para compilar e pode ser difícil de depurar.</span><span class="sxs-lookup"><span data-stu-id="e889f-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="e889f-129">Passe `release` para o script de build para selecionar este tipo de build.</span><span class="sxs-lookup"><span data-stu-id="e889f-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="e889f-130">Além disso, por padrão, o build não só cria os executáveis de tempo de execução, mas também compila todos os testes.</span><span class="sxs-lookup"><span data-stu-id="e889f-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="e889f-131">Há alguns testes, tomando a uma quantidade significativa de tempo que não é necessária se quiser apenas experimentar as alterações.</span><span class="sxs-lookup"><span data-stu-id="e889f-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="e889f-132">Você pode ignorar os builds de testes, adicionando o argumento `skiptests` ao script de build, como no exemplo a seguir (substitua `.\build` por `./build.sh` em computadores Unix):</span><span class="sxs-lookup"><span data-stu-id="e889f-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="e889f-133">O exemplo anterior mostrou como compilar o tipo `Debug`, que tem verificações de tempo de desenvolvimento (declarações) habilitadas e otimizações desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="e889f-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="e889f-134">Para criar o tipo de versão (velocidade total), faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e889f-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="e889f-135">É possível encontrar mais opções de build com build usando a opção -?</span><span class="sxs-lookup"><span data-stu-id="e889f-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="e889f-136">ou o qualificador -help.</span><span class="sxs-lookup"><span data-stu-id="e889f-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="e889f-137">Usando seu Build</span><span class="sxs-lookup"><span data-stu-id="e889f-137">Using Your Build</span></span>

<span data-ttu-id="e889f-138">O build coloca todos os arquivos gerados sob o diretório `bin` na base do repositório.</span><span class="sxs-lookup"><span data-stu-id="e889f-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="e889f-139">Há um diretório *bin\Log* que contém os arquivos de log gerados durante o build (mais útil quando o build falha).</span><span class="sxs-lookup"><span data-stu-id="e889f-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="e889f-140">A saída real é colocada em um diretório *bin\Product\[plataforma]. [ Arquitetura de CPU]. [tipo de build]* , como *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="e889f-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="e889f-141">Embora a saída “bruta” do build, às vezes, seja útil, normalmente, você só está interessado nos pacotes NuGet, que são colocados no subdiretório `.nuget\pkg` do diretório de saída anterior.</span><span class="sxs-lookup"><span data-stu-id="e889f-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="e889f-142">Há duas técnicas básicas para usar o novo tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="e889f-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="e889f-143">**Use dotnet.exe e NuGet para compor um aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="e889f-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="e889f-144">Consulte [Usando sua compilação](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) para obter instruções sobre como criar um programa que usa o novo tempo de execução usando pacotes de NuGet que acabaram de ser criados e a interface de linha de comando 'dotnet' (CLI).</span><span class="sxs-lookup"><span data-stu-id="e889f-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="e889f-145">Essa técnica é a maneira esperada com que desenvolvedores que não sejam de tempo de execução provavelmente consumirão o novo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e889f-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="e889f-146">**Use corerun.exe para executar um aplicativo usando DLLs desagrupadas**.</span><span class="sxs-lookup"><span data-stu-id="e889f-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="e889f-147">Esse repositório também define um host simples chamado corerun.exe que NÃO tem nenhuma dependência do NuGet.</span><span class="sxs-lookup"><span data-stu-id="e889f-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="e889f-148">É necessário informar ao host onde obter as DLLs necessárias que você realmente usa, além de reuni-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="e889f-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="e889f-149">Essa técnica é usada por todos os testes no repositório [dotnet/coreclr](https://github.com/dotnet/coreclr) e é útil para um loop local rápido 'edit-compile-debug', como os testes de unidade preliminar.</span><span class="sxs-lookup"><span data-stu-id="e889f-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="e889f-150">Consulte [Executando aplicativos do .NET Core com CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) para obter detalhes sobre como usar essa técnica.</span><span class="sxs-lookup"><span data-stu-id="e889f-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="e889f-151">Compilar a CLI da fonte</span><span class="sxs-lookup"><span data-stu-id="e889f-151">Build the CLI from source</span></span>

<span data-ttu-id="e889f-152">O código-fonte para a CLI do .NET Core pode ser encontrado no repositório [dotnet/cli](https://github.com/dotnet/cli/) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="e889f-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="e889f-153">Para criar a CLI do .NET Core, será necessário os seguintes itens instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e889f-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="e889f-154">Windows e Linux:</span><span class="sxs-lookup"><span data-stu-id="e889f-154">Windows & Linux:</span></span>
  * <span data-ttu-id="e889f-155">git no CAMINHO</span><span class="sxs-lookup"><span data-stu-id="e889f-155">git on the PATH</span></span>
* <span data-ttu-id="e889f-156">macOS:</span><span class="sxs-lookup"><span data-stu-id="e889f-156">macOS:</span></span>
  * <span data-ttu-id="e889f-157">git no CAMINHO</span><span class="sxs-lookup"><span data-stu-id="e889f-157">git on the PATH</span></span>
  * <span data-ttu-id="e889f-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="e889f-158">Xcode</span></span>
  * <span data-ttu-id="e889f-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="e889f-159">OpenSSL</span></span>

<span data-ttu-id="e889f-160">Para criar, execute `build.cmd` no Windows ou `build.sh` no Linux e macOS da raiz.</span><span class="sxs-lookup"><span data-stu-id="e889f-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="e889f-161">Se não desejar executar testes, execute `build.cmd -t:Compile` ou `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="e889f-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="e889f-162">Para criar a CLI em macOS serra, é necessário definir a variável de ambiente DOTNET_RUNTIME_ID executando `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="e889f-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="e889f-163">Usando seu build</span><span class="sxs-lookup"><span data-stu-id="e889f-163">Using your build</span></span>

<span data-ttu-id="e889f-164">Use o `dotnet` executável de *artefatos/{os}-{arch}/stage2* para testar a CLI recém-criada.</span><span class="sxs-lookup"><span data-stu-id="e889f-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="e889f-165">Se desejar usar a saída de build ao invocar `dotnet` do console atual, também é possível adicionar *artefatos/{os}-{arch}/stage2* ao CAMINHO.</span><span class="sxs-lookup"><span data-stu-id="e889f-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="e889f-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e889f-166">See also</span></span>

* [<span data-ttu-id="e889f-167">Common Language Runtime do .NET Core (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="e889f-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="e889f-168">Guia do desenvolvedor da CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e889f-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="e889f-169">Pacote de distribuição do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e889f-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
