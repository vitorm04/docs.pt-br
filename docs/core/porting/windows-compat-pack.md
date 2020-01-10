---
title: Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core
description: Saiba mais sobre o pacote de compatibilidade do Windows e como você pode usá-lo para portar o código de .NET Framework existente para o .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715476"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="c9724-103">Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core</span><span class="sxs-lookup"><span data-stu-id="c9724-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="c9724-104">Alguns dos problemas mais comuns encontrados ao portar código existente para o .NET Core são dependências de APIs e tecnologias que só são encontradas no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9724-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="c9724-105">O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, portanto, é muito mais fácil compilar aplicativos .NET Core e bibliotecas do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c9724-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="c9724-106">Esse pacote é uma [extensão lógica do .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta consideravelmente o conjunto de APIs e o código existente é compilado quase sem modificações.</span><span class="sxs-lookup"><span data-stu-id="c9724-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="c9724-107">Para manter a promessa do .NET Standard ("é o conjunto de APIs que todas as implementações do .NET fornecem"), o pacote não inclui tecnologias que não funcionam em todas as plataformas, como registro, Instrumentação de Gerenciamento do Windows (WMI) ou emissão de reflexo API.</span><span class="sxs-lookup"><span data-stu-id="c9724-107">In order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), the pack doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="c9724-108">O pacote de compatibilidade do Windows fica sobre o .NET Standard e fornece acesso a tecnologias que são somente Windows.</span><span class="sxs-lookup"><span data-stu-id="c9724-108">The Windows Compatibility Pack sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="c9724-109">É especialmente útil para os clientes que desejam migrar para o .NET Core, mas pretendem permanecer no Windows como uma primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="c9724-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="c9724-110">Nesse cenário, não ser capaz de usar tecnologias somente do Windows é apenas um obstáculo de migração sem benefícios arquitetônicos.</span><span class="sxs-lookup"><span data-stu-id="c9724-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with no architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="c9724-111">Conteúdo do pacote</span><span class="sxs-lookup"><span data-stu-id="c9724-111">Package contents</span></span>

<span data-ttu-id="c9724-112">O pacote de compatibilidade do Windows é fornecido por meio do [pacote NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado de projetos direcionados ao .NET Core ou .net Standard.</span><span class="sxs-lookup"><span data-stu-id="c9724-112">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="c9724-113">Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:</span><span class="sxs-lookup"><span data-stu-id="c9724-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="c9724-114">Páginas de código</span><span class="sxs-lookup"><span data-stu-id="c9724-114">Code Pages</span></span>
- <span data-ttu-id="c9724-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="c9724-115">CodeDom</span></span>
- <span data-ttu-id="c9724-116">Configuração do</span><span class="sxs-lookup"><span data-stu-id="c9724-116">Configuration</span></span>
- <span data-ttu-id="c9724-117">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="c9724-117">Directory Services</span></span>
- <span data-ttu-id="c9724-118">Desenho</span><span class="sxs-lookup"><span data-stu-id="c9724-118">Drawing</span></span>
- <span data-ttu-id="c9724-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="c9724-119">ODBC</span></span>
- <span data-ttu-id="c9724-120">Permissões</span><span class="sxs-lookup"><span data-stu-id="c9724-120">Permissions</span></span>
- <span data-ttu-id="c9724-121">Portas</span><span class="sxs-lookup"><span data-stu-id="c9724-121">Ports</span></span>
- <span data-ttu-id="c9724-122">ACL (Listas de Controle de Acesso) do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-122">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="c9724-123">{1&gt;{2&gt;Windows Communication Foundation (WCF)&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c9724-123">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="c9724-124">Criptografia do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-124">Windows Cryptography</span></span>
- <span data-ttu-id="c9724-125">EventLog do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-125">Windows EventLog</span></span>
- <span data-ttu-id="c9724-126">WMI (Instrumentação de Gerenciamento do Windows)</span><span class="sxs-lookup"><span data-stu-id="c9724-126">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="c9724-127">Contadores de Desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-127">Windows Performance Counters</span></span>
- <span data-ttu-id="c9724-128">Registro do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-128">Windows Registry</span></span>
- <span data-ttu-id="c9724-129">Cache do Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="c9724-129">Windows Runtime Caching</span></span>
- <span data-ttu-id="c9724-130">Serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="c9724-130">Windows Services</span></span>

<span data-ttu-id="c9724-131">Para obter mais informações, confira a [especificação do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c9724-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="c9724-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="c9724-132">Get started</span></span>

1. <span data-ttu-id="c9724-133">Antes de portar, certifique-se de dar uma olhada no [processo de portabilidade](index.md).</span><span class="sxs-lookup"><span data-stu-id="c9724-133">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="c9724-134">Ao portar código existente para .NET Core ou .NET Standard, instale o [pacote NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="c9724-134">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="c9724-135">Caso deseje permanecer no Windows, você estará pronto.</span><span class="sxs-lookup"><span data-stu-id="c9724-135">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="c9724-136">Se desejar executar o aplicativo .NET Core ou a biblioteca .NET Standard no Linux ou macOS, use o [Analisador de API](../../standard/analyzers/api-analyzer.md) para localizar o uso de APIs que não funcionarão com multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="c9724-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="c9724-137">Remova os usos dessas APIs, substitua-os por alternativas de multiplataforma ou proteja-os usando uma verificação de plataforma, como:</span><span class="sxs-lookup"><span data-stu-id="c9724-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="c9724-138">Para ver uma demonstração, confira o [vídeo do Channel 9 sobre o Pacote de Compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="c9724-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
