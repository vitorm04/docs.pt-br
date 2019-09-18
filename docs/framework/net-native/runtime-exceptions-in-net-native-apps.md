---
title: Exceções em tempo de execução em aplicativos do .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27a2e0906343d115c47230c726efb74cd51d4c93
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049168"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="dc11a-102">Exceções em tempo de execução em aplicativos do .NET Native</span><span class="sxs-lookup"><span data-stu-id="dc11a-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="dc11a-103">É importante testar os builds de versão do seu aplicativo da Plataforma Universal do Windows nas respectivas plataformas de destino, porque as configurações de depuração e de lançamento são completamente diferentes.</span><span class="sxs-lookup"><span data-stu-id="dc11a-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="dc11a-104">Por padrão, a configuração de depuração usa o tempo de execução do .Net Core para compilar seu aplicativo, mas a configuração de lançamento usa .NET Native para compilar seu aplicativo em código nativo.</span><span class="sxs-lookup"><span data-stu-id="dc11a-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dc11a-105">Para obter informações sobre como lidar com as exceções [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)e [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) que você pode encontrar ao testar as versões de lançamento do seu aplicativo, consulte a "etapa 4: Resolver manualmente os metadados ausentes: no tópico [introdução](getting-started-with-net-native.md) , bem como referência de arquivo de configuração de [reflexão e .net Native](reflection-and-net-native.md) e [diretivas de tempo de execução (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="dc11a-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="dc11a-106">Builds de depuração e de versão</span><span class="sxs-lookup"><span data-stu-id="dc11a-106">Debug and release builds</span></span>  
 <span data-ttu-id="dc11a-107">Quando o build de depuração é executado no tempo de execução do .Net Core, ele não foi compilado para código nativo.</span><span class="sxs-lookup"><span data-stu-id="dc11a-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="dc11a-108">Isso torna todos os serviços normalmente fornecidos pelo tempo de execução disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc11a-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="dc11a-109">Por outro lado, o build de versão é compilado em código nativo para suas plataformas de destino, remove a maioria das dependências de bibliotecas e tempos de execução externos e otimiza muito o código para obter o máximo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="dc11a-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="dc11a-110">Quando você depura builds de versão que são compilados usando o .NET Native:</span><span class="sxs-lookup"><span data-stu-id="dc11a-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="dc11a-111">Você usa o mecanismo de depuração do .NET Native, que é diferente das ferramentas de depuração normais do .NET.</span><span class="sxs-lookup"><span data-stu-id="dc11a-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="dc11a-112">O tamanho de seu executável é reduzido tanto quanto possível.</span><span class="sxs-lookup"><span data-stu-id="dc11a-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="dc11a-113">Uma das maneiras pelas quais o .NET Native reduz o tamanho de um executável é cortando significativamente as mensagens de exceção de tempo de execução, um tópico discutido em maiores detalhes na seção [Mensagens de exceção de tempo de execução](#Messages).</span><span class="sxs-lookup"><span data-stu-id="dc11a-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="dc11a-114">Seu código é altamente otimizado.</span><span class="sxs-lookup"><span data-stu-id="dc11a-114">Your code is heavily optimized.</span></span> <span data-ttu-id="dc11a-115">Isso significa que inlining é usado sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="dc11a-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="dc11a-116">(O inlining move código de rotinas externas para a rotina chamadora.)   O fato de que o .NET Native fornece um tempo de execução especializado e implementa inlining agressivo afeta a pilha de chamadas que é exibida durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="dc11a-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="dc11a-117">Para obter mais informações, consulte a seção [Pilha de chamadas de tempo de execução](#CallStack).</span><span class="sxs-lookup"><span data-stu-id="dc11a-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc11a-118">Você pode controlar se os builds de depuração e de versão são compilados com a cadeia de ferramentas do .NET Native, marcando ou desmarcando a caixa **Compilar com cadeia de ferramentas do .NET Native**.</span><span class="sxs-lookup"><span data-stu-id="dc11a-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="dc11a-119">No entanto, observe que a Windows Store sempre compilará a versão de produção do seu aplicativo com a cadeia de ferramentas do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dc11a-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="dc11a-120">Mensagens de exceção de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dc11a-120">Runtime exception messages</span></span>  
 <span data-ttu-id="dc11a-121">Para minimizar o tamanho do executável do aplicativo, o .NET Native não inclui o texto completo das mensagens de exceção.</span><span class="sxs-lookup"><span data-stu-id="dc11a-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="dc11a-122">Como resultado, exceções de tempo de execução geradas em builds de versão podem não exibir o texto completo das mensagens de exceção.</span><span class="sxs-lookup"><span data-stu-id="dc11a-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="dc11a-123">Em vez disso, o texto pode conter uma subcadeia de caracteres junto com um link para mais informações.</span><span class="sxs-lookup"><span data-stu-id="dc11a-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="dc11a-124">Por exemplo, as informações de exceção podem aparecer como:</span><span class="sxs-lookup"><span data-stu-id="dc11a-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="dc11a-125">Se você precisar que a mensagem de exceção completa, execute o build de depuração em vez disso.</span><span class="sxs-lookup"><span data-stu-id="dc11a-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="dc11a-126">Por exemplo, as informações de exceção anteriores do build de versão podem aparecer da seguinte maneira no build de depuração:</span><span class="sxs-lookup"><span data-stu-id="dc11a-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="dc11a-127">Pilha de chamadas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dc11a-127">Runtime call stack</span></span>  
 <span data-ttu-id="dc11a-128">Devido ao inlining e outras otimizações, a pilha de chamadas exibida por um aplicativo compilado pela cadeia de ferramentas do .NET Native pode não lhe ajudar a identificar claramente o caminho para uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dc11a-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="dc11a-129">Para obter a pilha completa, execute o build de depuração em vez disso.</span><span class="sxs-lookup"><span data-stu-id="dc11a-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc11a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc11a-130">See also</span></span>

- [<span data-ttu-id="dc11a-131">Depurando .NET Native aplicativos Windows universal</span><span class="sxs-lookup"><span data-stu-id="dc11a-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="dc11a-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="dc11a-132">Getting Started</span></span>](getting-started-with-net-native.md)
