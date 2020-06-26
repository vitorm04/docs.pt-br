---
title: Depuração, rastreamento e criação de perfil
description: Leia sobre depuração, rastreamento e criação de perfil no .NET. Consulte os artigos que abordam depuração JIT (just-in-time), rastreamento e instrumentação de aplicativos e muito mais.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 745f16652c02e3409e7fa7a48beacbf7e777e924
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415973"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="06047-104">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="06047-104">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="06047-105">Para depurar um aplicativo do .NET Framework, o compilador e o ambiente de runtime devem ser configurados para habilitar um depurador a anexar ao aplicativo e gerar símbolos e mapas de linha, se possível, para o aplicativo a respectiva MSIL (Microsoft Intermediate Language) correspondente.</span><span class="sxs-lookup"><span data-stu-id="06047-105">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="06047-106">Após um aplicativo gerenciado ter sido depurado, o perfil dele pode ser criado para aprimorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="06047-106">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="06047-107">A criação de perfil avalia e descreve as linhas do código-fonte que geram o código executado com mais frequência e quanto tempo demora para executá-las.</span><span class="sxs-lookup"><span data-stu-id="06047-107">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="06047-108">Aplicativos do .NET framework são depurados facilmente usando o Visual Studio, que lida com muitos dos detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="06047-108">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="06047-109">Se o Visual Studio não estiver instalado, você poderá examinar e melhorar o desempenho de aplicativos do .NET Framework por meio das classes de depuração do namespace <xref:System.Diagnostics> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06047-109">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="06047-110">Este namespace inclui as classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.TraceSource> para rastreamento de fluxo de execução e as classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> e <xref:System.Diagnostics.PerformanceCounter> para criação de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="06047-110">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06047-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="06047-111">In This Section</span></span>  
 [<span data-ttu-id="06047-112">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="06047-112">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="06047-113">Mostra como configurar o Registro para anexação JIT de um mecanismo de depuração para um aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06047-113">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="06047-114">Facilitar a depuração de uma imagem</span><span class="sxs-lookup"><span data-stu-id="06047-114">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="06047-115">Mostra como ligar o acompanhamento JIT e desligar a otimização para facilitar a depuração de um assembly.</span><span class="sxs-lookup"><span data-stu-id="06047-115">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="06047-116">Rastreamento e instrumentação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="06047-116">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="06047-117">Descreve como monitorar a execução de seu aplicativo enquanto ele está em execução e como instrumentá-lo para exibir quão bem ele está executando ou se algo deu errado.</span><span class="sxs-lookup"><span data-stu-id="06047-117">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="06047-118">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="06047-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="06047-119">Descreve os MDAs (Assistentes de Depuração Gerenciados), que são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="06047-119">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="06047-120">Melhorando a depuração com os atributos de exibição do depurador</span><span class="sxs-lookup"><span data-stu-id="06047-120">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="06047-121">Descreve como o desenvolvedor de um tipo pode especificar qual será a aparência desse tipo quando ele for exibido em um depurador.</span><span class="sxs-lookup"><span data-stu-id="06047-121">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="06047-122">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="06047-122">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="06047-123">Descreve os contadores que você pode usar para controlar o desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06047-123">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06047-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="06047-124">Related Sections</span></span>  
 [<span data-ttu-id="06047-125">Depurar aplicativos ASP.NET ou ASP.NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="06047-125">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="06047-126">Fornece os pré-requisitos e as instruções sobre como depurar um aplicativo ASP.NET durante o desenvolvimento ou depois da implantação.</span><span class="sxs-lookup"><span data-stu-id="06047-126">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="06047-127">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="06047-127">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="06047-128">Fornece um guia para todas as principais áreas de tecnologia e tarefas para o desenvolvimento de aplicativos, incluindo a criação, a configuração, a depuração, a proteção e a implantação de seu aplicativo, bem como informações sobre programação dinâmica, interoperabilidade, extensibilidade, gerenciamento de memória e threading.</span><span class="sxs-lookup"><span data-stu-id="06047-128">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
