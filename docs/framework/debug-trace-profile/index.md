---
title: Depuração, rastreamento e criação de perfil
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff2be73b2cea563066f70ea2fe6d53840f718e75
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855277"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="86c6f-102">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="86c6f-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="86c6f-103">Para depurar um aplicativo do .NET Framework, o compilador e o ambiente de tempo de execução devem ser configurados para habilitar um depurador a anexar ao aplicativo e gerar símbolos e mapas de linha, se possível, para o aplicativo a respectiva MSIL (Microsoft Intermediate Language) correspondente.</span><span class="sxs-lookup"><span data-stu-id="86c6f-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="86c6f-104">Após um aplicativo gerenciado ter sido depurado, o perfil dele pode ser criado para aprimorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="86c6f-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="86c6f-105">A criação de perfil avalia e descreve as linhas do código-fonte que geram o código executado com mais frequência e quanto tempo demora para executá-las.</span><span class="sxs-lookup"><span data-stu-id="86c6f-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="86c6f-106">Aplicativos do .NET framework são depurados facilmente usando o Visual Studio, que lida com muitos dos detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="86c6f-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="86c6f-107">Se o Visual Studio não estiver instalado, você poderá examinar e melhorar o desempenho de aplicativos do .NET Framework por meio das classes de depuração do namespace <xref:System.Diagnostics> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86c6f-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="86c6f-108">Este namespace inclui as classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.TraceSource> para rastreamento de fluxo de execução e as classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> e <xref:System.Diagnostics.PerformanceCounter> para criação de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="86c6f-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86c6f-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="86c6f-109">In This Section</span></span>  
 [<span data-ttu-id="86c6f-110">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="86c6f-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="86c6f-111">Mostra como configurar o Registro para anexação JIT de um mecanismo de depuração para um aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86c6f-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="86c6f-112">Facilitando a depuração de uma imagem</span><span class="sxs-lookup"><span data-stu-id="86c6f-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="86c6f-113">Mostra como ligar o acompanhamento JIT e desligar a otimização para facilitar a depuração de um assembly.</span><span class="sxs-lookup"><span data-stu-id="86c6f-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="86c6f-114">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="86c6f-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="86c6f-115">Descreve como monitorar a execução de seu aplicativo enquanto ele está em execução e como instrumentá-lo para exibir quão bem ele está executando ou se algo deu errado.</span><span class="sxs-lookup"><span data-stu-id="86c6f-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="86c6f-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="86c6f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="86c6f-117">Descreve os MDAs (Assistentes de Depuração Gerenciados), que são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="86c6f-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="86c6f-118">Aprimorando a depuração com os atributos de exibição do depurador</span><span class="sxs-lookup"><span data-stu-id="86c6f-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="86c6f-119">Descreve como o desenvolvedor de um tipo pode especificar qual será a aparência desse tipo quando ele for exibido em um depurador.</span><span class="sxs-lookup"><span data-stu-id="86c6f-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="86c6f-120">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="86c6f-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="86c6f-121">Descreve os contadores que você pode usar para controlar o desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86c6f-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86c6f-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="86c6f-122">Related Sections</span></span>  
 [<span data-ttu-id="86c6f-123">Depurando aplicativos ASP.NET e AJAX</span><span class="sxs-lookup"><span data-stu-id="86c6f-123">Debugging ASP.NET and AJAX Applications</span></span>](https://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 <span data-ttu-id="86c6f-124">Fornece os pré-requisitos e as instruções sobre como depurar um aplicativo ASP.NET durante o desenvolvimento ou depois da implantação.</span><span class="sxs-lookup"><span data-stu-id="86c6f-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="86c6f-125">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="86c6f-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="86c6f-126">Fornece um guia para todas as principais áreas de tecnologia e tarefas para o desenvolvimento de aplicativos, incluindo a criação, a configuração, a depuração, a proteção e a implantação de seu aplicativo, bem como informações sobre programação dinâmica, interoperabilidade, extensibilidade, gerenciamento de memória e threading.</span><span class="sxs-lookup"><span data-stu-id="86c6f-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
