---
title: Funções de hospedagem CLR reprovadas
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504362"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="2156b-102">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="2156b-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="2156b-103">Esta seção descreve as funções estáticas globais não gerenciadas que as versões anteriores da API de hospedagem usavam.</span><span class="sxs-lookup"><span data-stu-id="2156b-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="2156b-104">Com exceção das funções de infraestrutura ( `_Cor*` funções), que são usadas somente pelo .NET Framework, essas funções foram preteridas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2156b-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="2156b-105">Funções de ativação</span><span class="sxs-lookup"><span data-stu-id="2156b-105">Activation functions</span></span>  
 [<span data-ttu-id="2156b-106">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="2156b-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="2156b-107">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-107">Deprecated.</span></span> <span data-ttu-id="2156b-108">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="2156b-109">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="2156b-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="2156b-110">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2156b-110">Obsolete.</span></span> <span data-ttu-id="2156b-111">Para inicializar o Common Language Runtime (CLR), use [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="2156b-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="2156b-112">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="2156b-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="2156b-113">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-113">Deprecated.</span></span> <span data-ttu-id="2156b-114">Garante que o mecanismo de execução do CLR seja carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="2156b-115">Em vez disso, use o método [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2156b-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="2156b-116">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="2156b-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="2156b-117">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-117">Deprecated.</span></span> <span data-ttu-id="2156b-118">Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="2156b-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="2156b-119">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="2156b-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="2156b-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-120">Deprecated.</span></span> <span data-ttu-id="2156b-121">Permite que hosts não gerenciados carreguem o CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="2156b-122">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="2156b-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="2156b-123">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-123">Deprecated.</span></span> <span data-ttu-id="2156b-124">Carrega o CLR em um processo usando informações de versão lidas de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="2156b-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="2156b-125">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="2156b-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="2156b-126">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-126">Deprecated.</span></span> <span data-ttu-id="2156b-127">Permite que hosts não gerenciados carreguem o CLR em um processo e permite que você defina sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="2156b-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="2156b-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2156b-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="2156b-129">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-129">Deprecated.</span></span> <span data-ttu-id="2156b-130">Permite que os hosts carreguem uma versão especificada do CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="2156b-131">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="2156b-132">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-132">Deprecated.</span></span> <span data-ttu-id="2156b-133">Obtém o número de versão do CLR necessário.</span><span class="sxs-lookup"><span data-stu-id="2156b-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="2156b-134">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="2156b-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="2156b-135">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-135">Deprecated.</span></span> <span data-ttu-id="2156b-136">Retorna o diretório de instalação do CLR que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="2156b-137">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="2156b-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="2156b-138">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-138">Deprecated.</span></span> <span data-ttu-id="2156b-139">Obtém o endereço da função especificada que é exportada da última versão instalada do CLR.</span><span class="sxs-lookup"><span data-stu-id="2156b-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="2156b-140">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="2156b-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="2156b-141">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-141">Deprecated.</span></span> <span data-ttu-id="2156b-142">Obtém informações de versão e diretório sobre o CLR solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2156b-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="2156b-143">Funções de versão do CLR</span><span class="sxs-lookup"><span data-stu-id="2156b-143">CLR version functions</span></span>  
 <span data-ttu-id="2156b-144">As funções nesta seção retornam uma versão do CLR; Eles não ativam o CLR.</span><span class="sxs-lookup"><span data-stu-id="2156b-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="2156b-145">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="2156b-146">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-146">Deprecated.</span></span> <span data-ttu-id="2156b-147">Retorna o número de versão do CLR que está sendo executado no processo atual.</span><span class="sxs-lookup"><span data-stu-id="2156b-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="2156b-148">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="2156b-149">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-149">Deprecated.</span></span> <span data-ttu-id="2156b-150">Obtém as informações de versão do CLR do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="2156b-151">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="2156b-152">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-152">Deprecated.</span></span> <span data-ttu-id="2156b-153">Obtém o número de versão do CLR solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="2156b-154">Se essa versão não estiver instalada, o obterá a versão mais recente instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="2156b-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="2156b-155">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="2156b-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="2156b-156">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-156">Deprecated.</span></span> <span data-ttu-id="2156b-157">Obtém as informações de versão do CLR apropriadas para a classe com o CLSID especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="2156b-158">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="2156b-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="2156b-159">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-159">Deprecated.</span></span> <span data-ttu-id="2156b-160">Obtém o número de versão do CLR associado ao identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="2156b-161">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="2156b-162">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-162">Deprecated.</span></span> <span data-ttu-id="2156b-163">Permite que o host determine qual versão do CLR será usada dentro do processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="2156b-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="2156b-164">Funções de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2156b-164">Hosting functions</span></span>  
 [<span data-ttu-id="2156b-165">Função CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="2156b-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="2156b-166">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-166">Deprecated.</span></span> <span data-ttu-id="2156b-167">Faz uma chamada para a função que tem o nome e os parâmetros especificados na biblioteca especificada.</span><span class="sxs-lookup"><span data-stu-id="2156b-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="2156b-168">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="2156b-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="2156b-169">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-169">Deprecated.</span></span> <span data-ttu-id="2156b-170">Descarrega um assembly COM do processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="2156b-171">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="2156b-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="2156b-172">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-172">Deprecated.</span></span> <span data-ttu-id="2156b-173">Desliga o processo atual não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2156b-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="2156b-174">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="2156b-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="2156b-175">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-175">Deprecated.</span></span> <span data-ttu-id="2156b-176">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2156b-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="2156b-177">Função CorMarkThreadInThreadPool</span><span class="sxs-lookup"><span data-stu-id="2156b-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="2156b-178">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-178">Deprecated.</span></span> <span data-ttu-id="2156b-179">Marca o thread do pool de threads em execução no momento para a execução do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2156b-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="2156b-180">A partir do .NET Framework versão 2,0, essa função não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="2156b-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="2156b-181">Ela não é necessária e pode ser removida do seu código.</span><span class="sxs-lookup"><span data-stu-id="2156b-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="2156b-182">Função CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="2156b-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="2156b-183">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2156b-183">Obsolete.</span></span> <span data-ttu-id="2156b-184">O CLR não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="2156b-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="2156b-185">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="2156b-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="2156b-186">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2156b-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="2156b-187">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="2156b-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="2156b-188">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-188">Deprecated.</span></span> <span data-ttu-id="2156b-189">Cria um objeto [ICorDebug](../debugging/icordebug-interface.md) com base nas informações de versão especificadas.</span><span class="sxs-lookup"><span data-stu-id="2156b-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="2156b-190">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="2156b-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="2156b-191">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-191">Deprecated.</span></span> <span data-ttu-id="2156b-192">Cria um objeto [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="2156b-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="2156b-193">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="2156b-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="2156b-194">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-194">Deprecated.</span></span> <span data-ttu-id="2156b-195">Destrói um objeto [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="2156b-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="2156b-196">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="2156b-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="2156b-197">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-197">Deprecated.</span></span> <span data-ttu-id="2156b-198">Aponta para uma função que o CLR chama para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2156b-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="2156b-199">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="2156b-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="2156b-200">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-200">Deprecated.</span></span> <span data-ttu-id="2156b-201">Aponta para uma função que o CLR chama para notificar o host de que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="2156b-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="2156b-202">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="2156b-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="2156b-203">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-203">Deprecated.</span></span> <span data-ttu-id="2156b-204">Obtém um ponteiro para uma interface que permite que o CLR gerencie identidades.</span><span class="sxs-lookup"><span data-stu-id="2156b-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="2156b-205">Função LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="2156b-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="2156b-206">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-206">Deprecated.</span></span> <span data-ttu-id="2156b-207">Carrega uma versão especificada de uma .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="2156b-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="2156b-208">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="2156b-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="2156b-209">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-209">Deprecated.</span></span> <span data-ttu-id="2156b-210">Traduz um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.</span><span class="sxs-lookup"><span data-stu-id="2156b-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="2156b-211">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="2156b-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="2156b-212">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-212">Deprecated.</span></span> <span data-ttu-id="2156b-213">Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="2156b-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="2156b-214">Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="2156b-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="2156b-215">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-215">Deprecated.</span></span> <span data-ttu-id="2156b-216">Aponta para uma função que notifica o host quando uma e/s sobreposta (ou seja, assíncrona) para um dispositivo for concluída.</span><span class="sxs-lookup"><span data-stu-id="2156b-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="2156b-217">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="2156b-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="2156b-218">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-218">Deprecated.</span></span> <span data-ttu-id="2156b-219">Aponta para uma função que notifica o host que um thread começou a ser executado.</span><span class="sxs-lookup"><span data-stu-id="2156b-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="2156b-220">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="2156b-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="2156b-221">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-221">Deprecated.</span></span> <span data-ttu-id="2156b-222">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="2156b-223">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="2156b-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="2156b-224">Preterido.</span><span class="sxs-lookup"><span data-stu-id="2156b-224">Deprecated.</span></span> <span data-ttu-id="2156b-225">Aponta para uma função que notifica o host de que um identificador de espera foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2156b-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="2156b-226">Funções de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="2156b-226">Infrastructure functions</span></span>  
 <span data-ttu-id="2156b-227">As funções nesta seção são para uso apenas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2156b-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="2156b-228">Função _CorDllMain</span><span class="sxs-lookup"><span data-stu-id="2156b-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="2156b-229">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="2156b-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="2156b-230">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="2156b-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="2156b-231">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="2156b-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="2156b-232">Função _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="2156b-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="2156b-233">Executa o ponto de entrada no código mapeado de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="2156b-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="2156b-234">Essa função é chamada pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2156b-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="2156b-235">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="2156b-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="2156b-236">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="2156b-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="2156b-237">Função _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="2156b-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="2156b-238">Valida as imagens de módulo gerenciado e notifica o carregador do sistema operacional depois que elas tiverem sido carregadas.</span><span class="sxs-lookup"><span data-stu-id="2156b-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2156b-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="2156b-239">See also</span></span>

- [<span data-ttu-id="2156b-240">.NET Framework 4 hospedando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="2156b-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
