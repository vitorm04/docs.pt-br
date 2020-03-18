---
title: Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core
description: Saiba mais sobre o Pacote de Compatibilidade do Windows e como você pode usá-lo para portar o código .NET Framework existente para .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733615"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="12c2b-103">Usar o Pacote de Compatibilidade do Windows para fazer a portabilidade pra o .NET Core</span><span class="sxs-lookup"><span data-stu-id="12c2b-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="12c2b-104">Alguns dos problemas mais comuns encontrados ao portar o código existente para o .NET Core são dependências de APIs e tecnologias que só são encontradas no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12c2b-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="12c2b-105">O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, portanto, é muito mais fácil compilar aplicativos .NET Core e bibliotecas do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="12c2b-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="12c2b-106">O pacote de compatibilidade é uma extensão lógica [do .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta significativamente o conjunto de API.</span><span class="sxs-lookup"><span data-stu-id="12c2b-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="12c2b-107">O código existente compila quase nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="12c2b-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="12c2b-108">Para manter sua promessa de "o conjunto de APIs que todas as implementações .NET fornecem", o .NET Standard não inclui tecnologias que não podem funcionar em todas as plataformas, como registro, Instrumentação de Gerenciamento do Windows (WMI) ou APIs de reflexão.</span><span class="sxs-lookup"><span data-stu-id="12c2b-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="12c2b-109">O Pacote de Compatibilidade do Windows fica em cima do .NET Standard e fornece acesso a essas tecnologias somente para Windows.</span><span class="sxs-lookup"><span data-stu-id="12c2b-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="12c2b-110">É especialmente útil para clientes que querem mudar para o .NET Core, mas planejam permanecer no Windows, pelo menos como um primeiro passo.</span><span class="sxs-lookup"><span data-stu-id="12c2b-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="12c2b-111">Nesse cenário, poder usar tecnologias somente para Windows remove o obstáculo de migração.</span><span class="sxs-lookup"><span data-stu-id="12c2b-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="12c2b-112">Conteúdo do pacote</span><span class="sxs-lookup"><span data-stu-id="12c2b-112">Package contents</span></span>

<span data-ttu-id="12c2b-113">O Pacote de Compatibilidade do Windows é fornecido através do [pacote Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado a partir de projetos que visam .NET Core ou .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="12c2b-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="12c2b-114">Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:</span><span class="sxs-lookup"><span data-stu-id="12c2b-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="12c2b-115">Páginas de código</span><span class="sxs-lookup"><span data-stu-id="12c2b-115">Code Pages</span></span>
- <span data-ttu-id="12c2b-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="12c2b-116">CodeDom</span></span>
- <span data-ttu-id="12c2b-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="12c2b-117">Configuration</span></span>
- <span data-ttu-id="12c2b-118">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="12c2b-118">Directory Services</span></span>
- <span data-ttu-id="12c2b-119">Desenho</span><span class="sxs-lookup"><span data-stu-id="12c2b-119">Drawing</span></span>
- <span data-ttu-id="12c2b-120">ODBCODBC</span><span class="sxs-lookup"><span data-stu-id="12c2b-120">ODBC</span></span>
- <span data-ttu-id="12c2b-121">Permissões</span><span class="sxs-lookup"><span data-stu-id="12c2b-121">Permissions</span></span>
- <span data-ttu-id="12c2b-122">Portas</span><span class="sxs-lookup"><span data-stu-id="12c2b-122">Ports</span></span>
- <span data-ttu-id="12c2b-123">ACL (Listas de Controle de Acesso) do Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="12c2b-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="12c2b-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="12c2b-125">Criptografia do Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-125">Windows Cryptography</span></span>
- <span data-ttu-id="12c2b-126">EventLog do Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-126">Windows EventLog</span></span>
- <span data-ttu-id="12c2b-127">WMI (Instrumentação de Gerenciamento do Windows)</span><span class="sxs-lookup"><span data-stu-id="12c2b-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="12c2b-128">Contadores de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-128">Windows Performance Counters</span></span>
- <span data-ttu-id="12c2b-129">Registro do Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-129">Windows Registry</span></span>
- <span data-ttu-id="12c2b-130">Cache do Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="12c2b-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="12c2b-131">Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="12c2b-131">Windows Services</span></span>

<span data-ttu-id="12c2b-132">Para obter mais informações, confira a [especificação do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="12c2b-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="12c2b-133">Introdução</span><span class="sxs-lookup"><span data-stu-id="12c2b-133">Get started</span></span>

1. <span data-ttu-id="12c2b-134">Antes de portar, certifique-se de dar uma olhada no [processo de portação](index.md).</span><span class="sxs-lookup"><span data-stu-id="12c2b-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="12c2b-135">Ao portar o código existente para .NET Core ou .NET Standard, instale o [pacote NuGet microsoft.windows.compatibilidade](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="12c2b-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="12c2b-136">Caso deseje permanecer no Windows, você estará pronto.</span><span class="sxs-lookup"><span data-stu-id="12c2b-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="12c2b-137">Se desejar executar o aplicativo .NET Core ou a biblioteca .NET Standard no Linux ou macOS, use o [Analisador de API](../../standard/analyzers/api-analyzer.md) para localizar o uso de APIs que não funcionarão com multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="12c2b-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="12c2b-138">Remova os usos dessas APIs, substitua-os por alternativas de multiplataforma ou proteja-os usando uma verificação de plataforma, como:</span><span class="sxs-lookup"><span data-stu-id="12c2b-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="12c2b-139">Para ver uma demonstração, confira o [vídeo do Channel 9 sobre o Pacote de Compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="12c2b-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
