---
title: Movimentando para .NET Core - usando o pacote de compatibilidade do Windows
description: "Saiba mais sobre o pacote de compatibilidade do Windows e como você pode usá-lo ao portar código do .NET Framework existente para .NET Core"
keywords: ".NET, o núcleo do .NET, Windows, compatibilidade"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="a3bec-104">Usando o pacote de compatibilidade do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="a3bec-105">Um dos problemas mais comuns que os desenvolvedores enfrentam ao portar seu código existente para .NET Core é que eles dependem de APIs e tecnologias que existem somente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3bec-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="a3bec-106">O *pacote de compatibilidade do Windows* é fornecer muitas dessas tecnologias para que a criação de aplicativos .NET Core, bem como bibliotecas .NET padrão se torna muito mais viável para o código existente.</span><span class="sxs-lookup"><span data-stu-id="a3bec-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="a3bec-107">Este pacote é uma lógica [extensão do .NET 2.0 padrão](../whats-new/index.md#api-changes-and-library-support) que significativamente o conjunto de APIs aumenta e o código existente compila quase sem modificações.</span><span class="sxs-lookup"><span data-stu-id="a3bec-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="a3bec-108">Mas, para manter a promessa de .NET padrão ("é o conjunto de APIs que fornecem todas as implementações de .NET"), isso não inclui tecnologias que não funcionam em todas as plataformas, como o registro, o Windows Management Instrumentation (WMI), ou a emissão de reflexão APIs.</span><span class="sxs-lookup"><span data-stu-id="a3bec-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="a3bec-109">O *pacote de compatibilidade do Windows* assenta sobre .NET padrão e fornece acesso às tecnologias Windows somente.</span><span class="sxs-lookup"><span data-stu-id="a3bec-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="a3bec-110">É especialmente útil para os clientes que desejarem mover para o .NET Core, mas plano permaneça no Windows como uma primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="a3bec-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="a3bec-111">Nesse cenário, a não ser capaz de usar tecnologias somente do Windows é apenas uma barreira de migração com zero benefícios da arquitetura.</span><span class="sxs-lookup"><span data-stu-id="a3bec-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="a3bec-112">Conteúdo do pacote</span><span class="sxs-lookup"><span data-stu-id="a3bec-112">Package contents</span></span>

<span data-ttu-id="a3bec-113">O *pacote de compatibilidade do Windows* é fornecido por meio do pacote do NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) e pode ser referenciado de projetos direcionados .NET Core ou .NET padrão.</span><span class="sxs-lookup"><span data-stu-id="a3bec-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="a3bec-114">Ele fornece cerca de 20.000 APIs, incluindo APIs somente do Windows, bem como entre plataformas de áreas de tecnologia a seguir:</span><span class="sxs-lookup"><span data-stu-id="a3bec-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="a3bec-115">Páginas de código</span><span class="sxs-lookup"><span data-stu-id="a3bec-115">Code Pages</span></span>
* <span data-ttu-id="a3bec-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="a3bec-116">CodeDom</span></span>
* <span data-ttu-id="a3bec-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="a3bec-117">Configuration</span></span>
* <span data-ttu-id="a3bec-118">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="a3bec-118">Directory Services</span></span>
* <span data-ttu-id="a3bec-119">desenho</span><span class="sxs-lookup"><span data-stu-id="a3bec-119">Drawing</span></span>
* <span data-ttu-id="a3bec-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="a3bec-120">ODBC</span></span>
* <span data-ttu-id="a3bec-121">Permissões</span><span class="sxs-lookup"><span data-stu-id="a3bec-121">Permissions</span></span>
* <span data-ttu-id="a3bec-122">Portas</span><span class="sxs-lookup"><span data-stu-id="a3bec-122">Ports</span></span>
* <span data-ttu-id="a3bec-123">Listas de controle de acesso (ACL) do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="a3bec-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="a3bec-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="a3bec-125">Criptografia do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-125">Windows Cryptography</span></span>
* <span data-ttu-id="a3bec-126">Log de eventos do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-126">Windows EventLog</span></span>
* <span data-ttu-id="a3bec-127">WMI (Instrumentação de Gerenciamento do Windows)</span><span class="sxs-lookup"><span data-stu-id="a3bec-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="a3bec-128">Contadores de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-128">Windows Performance Counters</span></span>
* <span data-ttu-id="a3bec-129">Registro do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-129">Windows Registry</span></span>
* <span data-ttu-id="a3bec-130">Cache de tempo de execução do Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="a3bec-131">Serviços Windows</span><span class="sxs-lookup"><span data-stu-id="a3bec-131">Windows Services</span></span>

<span data-ttu-id="a3bec-132">Para obter mais informações, consulte o [especificações do pacote de compatibilidade](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a3bec-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="a3bec-133">Introdução</span><span class="sxs-lookup"><span data-stu-id="a3bec-133">Get started</span></span>

1. <span data-ttu-id="a3bec-134">Antes de portar, certifique-se de examinar o [processo movimentando](index.md).</span><span class="sxs-lookup"><span data-stu-id="a3bec-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="a3bec-135">Ao portar código existente para .NET Core ou padrão do .NET, instale o pacote NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="a3bec-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="a3bec-136">Se você deseja manter no Windows, você esteja pronto.</span><span class="sxs-lookup"><span data-stu-id="a3bec-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="a3bec-137">Se você quiser executar o aplicativo de núcleo do .NET ou biblioteca .NET padrão em Linux ou macOS, use o [API analisador](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) para localizar o uso de APIs que não funcionará entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="a3bec-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="a3bec-138">Remova os usos dessas APIs, substituí-las por alternativas de plataforma cruzada ou protegê-los usando uma verificação de plataforma, como:</span><span class="sxs-lookup"><span data-stu-id="a3bec-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="a3bec-139">Para ver uma demonstração, confira o [vídeo do Channel 9 do pacote de compatibilidade do Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="a3bec-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

