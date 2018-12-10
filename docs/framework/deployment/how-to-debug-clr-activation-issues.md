---
title: Como depurar problemas de ativação do CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89724e9a322f2f28dbe5d18ae697acbdd0a32d8e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149725"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="abea4-102">Como depurar problemas de ativação do CLR</span><span class="sxs-lookup"><span data-stu-id="abea4-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="abea4-103">Se você encontrar problemas em fazer com que seu aplicativo seja executado com a versão correta do CLR (Common Language Runtime), poderá exibir e depurar os logs de ativação do CLR.</span><span class="sxs-lookup"><span data-stu-id="abea4-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="abea4-104">Esses logs podem ser muito úteis para determinar a causa raiz de um problema de ativação, quando o aplicativo carrega uma versão do CLR diferente da esperada ou não carrega o CLR de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="abea4-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="abea4-105">O [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) (Erros de inicialização do .NET Framework: gerenciando a experiência do usuário) discute a experiência quando nenhum CLR é encontrado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abea4-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="abea4-106">O registro em log de ativação do CLR pode ser habilitado em todo o sistema usando uma chave do Registro HKEY_LOCAL_MACHINE ou uma variável de ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="abea4-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="abea4-107">O log será gerado até que a entrada do Registro ou a variável de ambiente seja removida.</span><span class="sxs-lookup"><span data-stu-id="abea4-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="abea4-108">Como alternativa, você pode usar uma variável de ambiente local de processo ou usuário para habilitar o registro em log com uma duração e um escopo diferente.</span><span class="sxs-lookup"><span data-stu-id="abea4-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="abea4-109">Os logs de ativação do CLR não devem ser confundidos com os [logs de associação de assembly](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), que são totalmente diferentes.</span><span class="sxs-lookup"><span data-stu-id="abea4-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="abea4-110">Para habilitar o registro em log de ativação do CLR</span><span class="sxs-lookup"><span data-stu-id="abea4-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="abea4-111">Usando o Registro</span><span class="sxs-lookup"><span data-stu-id="abea4-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="abea4-112">No Editor de Registro, navegue até a pasta HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (em um computador de 32 bits) ou a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework (em um computador de 64 bits).</span><span class="sxs-lookup"><span data-stu-id="abea4-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="abea4-113">Adicione um valor de cadeia de caracteres chamado `CLRLoadLogDir` e defina-o como o caminho completo de um diretório existente no qual você deseja armazenar os logs de ativação do CLR.</span><span class="sxs-lookup"><span data-stu-id="abea4-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="abea4-114">O registro em log da ativação continua habilitada até que você remova o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="abea4-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="abea4-115">Usando uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="abea4-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="abea4-116">Defina a variável de ambiente `COMPLUS_CLRLoadLogDir` para uma cadeia de caracteres que represente o caminho completo de um diretório existente em que você gostaria de armazenar os logs de ativação do CLR.</span><span class="sxs-lookup"><span data-stu-id="abea4-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="abea4-117">Como você define a variável de ambiente determina seu escopo:</span><span class="sxs-lookup"><span data-stu-id="abea4-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="abea4-118">Se você a definir no nível do sistema, o registro em log da ativação estará habilitado para todos os aplicativos do .NET Framework nesse computador até a variável de ambiente ser removida.</span><span class="sxs-lookup"><span data-stu-id="abea4-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="abea4-119">Se você a definir no nível do usuário, o registro em log da ativação estará habilitado apenas para a conta de usuário atual.</span><span class="sxs-lookup"><span data-stu-id="abea4-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="abea4-120">O registro em log continua até a variável de ambiente ser removida.</span><span class="sxs-lookup"><span data-stu-id="abea4-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="abea4-121">Se você a definir de dentro do processo antes de carregar o CLR, o registro em log da ativação estará habilitado até que o processo seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="abea4-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="abea4-122">Se você a definir em um prompt de comando antes de executar um aplicativo, o registro em log da ativação estará habilitado para qualquer aplicativo executado desse prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="abea4-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="abea4-123">Por exemplo, para armazenar logs de ativação no diretório c:\clrloadlogs com escopo do nível de processo, abra uma janela de Prompt de Comando e digite o seguinte antes de executar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="abea4-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="abea4-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abea4-124">Example</span></span>  
 <span data-ttu-id="abea4-125">Os logs de ativação do CLR fornecem uma grande quantidade de dados sobre a ativação do CLR e o uso das APIs de hospedagem do CLR.</span><span class="sxs-lookup"><span data-stu-id="abea4-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="abea4-126">A maioria desses dados é usada internamente pela Microsoft, mas alguns dos dados também podem ser úteis para os desenvolvedores, conforme descrito neste artigo.</span><span class="sxs-lookup"><span data-stu-id="abea4-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="abea4-127">O log reflete a ordem na qual as APIs de hospedagem do CLR foram chamadas.</span><span class="sxs-lookup"><span data-stu-id="abea4-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="abea4-128">Ele também inclui dados úteis sobre o conjunto de tempos de execução instalados detectados no computador.</span><span class="sxs-lookup"><span data-stu-id="abea4-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="abea4-129">O formato de log de ativação do CLR não está documentado, mas pode ser usado para auxiliar os desenvolvedores que precisam resolver problemas de ativação do CLR.</span><span class="sxs-lookup"><span data-stu-id="abea4-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abea4-130">Não é possível abrir um log de ativação até que o processo que usa o CLR seja finalizado.</span><span class="sxs-lookup"><span data-stu-id="abea4-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abea4-131">Logs de ativação do CLR não são localizados, eles são gerados sempre em inglês.</span><span class="sxs-lookup"><span data-stu-id="abea4-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="abea4-132">No exemplo a seguir de um log de ativação, as informações mais úteis são realçadas e descritas após o log.</span><span class="sxs-lookup"><span data-stu-id="abea4-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
```  
  
-   <span data-ttu-id="abea4-133">**CLR Loading log** fornece o caminho para o executável que iniciou o processo que carregou o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="abea4-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="abea4-134">Observe que isso poderia ser um host nativo.</span><span class="sxs-lookup"><span data-stu-id="abea4-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="abea4-135">**Installed Runtime** é o conjunto das versões do CLR instaladas no computador que são candidatas para a solicitação de ativação.</span><span class="sxs-lookup"><span data-stu-id="abea4-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="abea4-136">**built with version** é a versão do CLR que foi usada para criar o binário que foi fornecido para um método como [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="abea4-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="abea4-137">**feature-on-demand installation** refere-se a habilitar o .NET Framework 3.5 no Windows 8.</span><span class="sxs-lookup"><span data-stu-id="abea4-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="abea4-138">Consulte [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) (Erros de inicialização do .NET Framework: gerenciando a experiência do usuário) para obter mais informações sobre esse cenário.</span><span class="sxs-lookup"><span data-stu-id="abea4-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="abea4-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abea4-139">See Also</span></span>  
- [<span data-ttu-id="abea4-140">Implantação</span><span class="sxs-lookup"><span data-stu-id="abea4-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
- [<span data-ttu-id="abea4-141">Como configurar um aplicativo para oferecer suporte ao .NET Framework 4 ou 4.5</span><span class="sxs-lookup"><span data-stu-id="abea4-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
