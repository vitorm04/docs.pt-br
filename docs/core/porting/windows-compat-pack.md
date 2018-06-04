---
title: Portando para o .NET Core – usando o Pacote de Compatibilidade do Windows
description: Saiba mais sobre o Pacote de Compatibilidade do Windows e como você pode usá-lo para portar um código existente do .NET Framework para o .NET Core
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.openlocfilehash: 51b96d7828285964c1b0cbb835b8eb5ed92c47d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566167"
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="d5002-103">Usando o Pacote de Compatibilidade do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-103">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="d5002-104">Um dos problemas mais comuns que os desenvolvedores enfrentam ao portar seus códigos existentes para o .NET Core é que eles dependem de APIs e tecnologias que existem somente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5002-104">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="d5002-105">O *Pacote de Compatibilidade do Windows* fornece muitas dessas tecnologias, de modo que a criação de aplicativos .NET Core, bem como bibliotecas .NET Standard, seja muito mais viável para o código existente.</span><span class="sxs-lookup"><span data-stu-id="d5002-105">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="d5002-106">Esse pacote é uma [extensão lógica do .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) que aumenta consideravelmente o conjunto de APIs e o código existente é compilado quase sem modificações.</span><span class="sxs-lookup"><span data-stu-id="d5002-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="d5002-107">No entanto, para manter a promessa do .NET Standard (“é o conjunto de APIs fornecido por todas as implementações do .NET”), isso não inclui tecnologias que não funcionam em todas as plataformas, como o Registro, o WMI (Instrumentação de Gerenciamento do Windows) ou as APIs de emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="d5002-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="d5002-108">O *Pacote de Compatibilidade do Windows* se baseia no .NET Standard e fornece acesso às tecnologias somente Windows.</span><span class="sxs-lookup"><span data-stu-id="d5002-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="d5002-109">É especialmente útil para os clientes que desejam migrar para o .NET Core, mas pretendem permanecer no Windows como uma primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="d5002-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="d5002-110">Nesse cenário, não conseguir usar as tecnologias somente Windows é apenas um obstáculo de migração sem nenhum benefício de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="d5002-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="d5002-111">Conteúdo do pacote</span><span class="sxs-lookup"><span data-stu-id="d5002-111">Package contents</span></span>

<span data-ttu-id="d5002-112">O *Pacote de Compatibilidade do Windows* é fornecido por meio do Pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado em projetos direcionados ao .NET Core ou .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d5002-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="d5002-113">Ele fornece cerca de 20.000 APIs, incluindo APIs somente Windows, bem como APIs de multiplataforma das seguintes áreas de tecnologia:</span><span class="sxs-lookup"><span data-stu-id="d5002-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="d5002-114">Páginas de código</span><span class="sxs-lookup"><span data-stu-id="d5002-114">Code Pages</span></span>
* <span data-ttu-id="d5002-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="d5002-115">CodeDom</span></span>
* <span data-ttu-id="d5002-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="d5002-116">Configuration</span></span>
* <span data-ttu-id="d5002-117">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="d5002-117">Directory Services</span></span>
* <span data-ttu-id="d5002-118">Desenho</span><span class="sxs-lookup"><span data-stu-id="d5002-118">Drawing</span></span>
* <span data-ttu-id="d5002-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="d5002-119">ODBC</span></span>
* <span data-ttu-id="d5002-120">Permissões</span><span class="sxs-lookup"><span data-stu-id="d5002-120">Permissions</span></span>
* <span data-ttu-id="d5002-121">Portas</span><span class="sxs-lookup"><span data-stu-id="d5002-121">Ports</span></span>
* <span data-ttu-id="d5002-122">ACL (Listas de Controle de Acesso) do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="d5002-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d5002-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="d5002-124">Criptografia do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-124">Windows Cryptography</span></span>
* <span data-ttu-id="d5002-125">EventLog do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-125">Windows EventLog</span></span>
* <span data-ttu-id="d5002-126">WMI (Instrumentação de Gerenciamento do Windows)</span><span class="sxs-lookup"><span data-stu-id="d5002-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="d5002-127">Contadores de Desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-127">Windows Performance Counters</span></span>
* <span data-ttu-id="d5002-128">Registro do Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-128">Windows Registry</span></span>
* <span data-ttu-id="d5002-129">Cache do Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="d5002-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="d5002-130">Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="d5002-130">Windows Services</span></span>

<span data-ttu-id="d5002-131">Para obter mais informações, consulte as [especificações do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d5002-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="d5002-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="d5002-132">Get started</span></span>

1. <span data-ttu-id="d5002-133">Antes da portabilidade, examine o [Processo de portabilidade](index.md).</span><span class="sxs-lookup"><span data-stu-id="d5002-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="d5002-134">Ao portar um código existente para o .NET Core ou .NET Standard, instale o pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="d5002-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="d5002-135">Caso deseje permanecer no Windows, você estará pronto.</span><span class="sxs-lookup"><span data-stu-id="d5002-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="d5002-136">Se desejar executar o aplicativo .NET Core ou a biblioteca .NET Standard no Linux ou macOS, use o [Analisador de API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) para localizar o uso de APIs que não funcionarão com multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="d5002-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="d5002-137">Remova os usos dessas APIs, substitua-os por alternativas de multiplataforma ou proteja-os usando uma verificação de plataforma, como:</span><span class="sxs-lookup"><span data-stu-id="d5002-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="d5002-138">Para ver uma demonstração, confira o [vídeo do Channel 9 sobre o Pacote de Compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="d5002-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

