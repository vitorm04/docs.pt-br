---
title: 'Como: Determinar quais versões do .NET Framework estão instaladas'
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b7c7704c4f417ef16d3a79fa6d955265e42cf14
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262446"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="f912a-102">Como: Determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="f912a-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="f912a-103">Os usuários podem [instalar](https://docs.microsoft.com/dotnet/framework/install) e executar várias versões do .NET Framework em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="f912a-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="f912a-104">Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="f912a-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> 

<span data-ttu-id="f912a-105">O .NET Framework consiste em dois componentes principais, que têm o controle de versão feito separadamente:</span><span class="sxs-lookup"><span data-stu-id="f912a-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="f912a-106">Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f912a-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="f912a-107">O .NET Framework e assemblies que compartilham o mesmo número de versão.</span><span class="sxs-lookup"><span data-stu-id="f912a-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="f912a-108">O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f912a-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="f912a-109">O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="f912a-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  

> [!NOTE]
> <span data-ttu-id="f912a-110">Cada nova versão do .NET Framework retém recursos de versões anteriores e adiciona novos recursos.</span><span class="sxs-lookup"><span data-stu-id="f912a-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="f912a-111">Você pode carregar várias versões do .NET Framework em um único computador ao mesmo tempo, o que significa que você pode instalar o .NET Framework sem precisar desinstalar as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f912a-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="f912a-112">Em geral, você não deve desinstalar as versões anteriores do .NET Framework, porque um aplicativo que você usa pode depender de uma versão específica e pode ser interrompido caso essa versão seja removida.</span><span class="sxs-lookup"><span data-stu-id="f912a-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="f912a-113">Há uma diferença entre a versão do .NET Framework e a versão do CLR:</span><span class="sxs-lookup"><span data-stu-id="f912a-113">There is a difference between the .NET Framework version and the CLR version:</span></span> 
> - <span data-ttu-id="f912a-114">A versão do .NET Framework baseia-se no conjunto de assemblies que forma a biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f912a-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="f912a-115">Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="f912a-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> 
>- <span data-ttu-id="f912a-116">A versão do CLR baseia-se no tempo de execução no qual os aplicativos .NET Framework são executados.</span><span class="sxs-lookup"><span data-stu-id="f912a-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="f912a-117">Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f912a-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="f912a-118">Por exemplo, o CLR versão 4.0.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2; o CLR versão 4.0.30319.42000 dá suporte a versões do .NET Framework que começam no .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="f912a-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2 and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> 
>
> <span data-ttu-id="f912a-119">Para obter mais informações sobre as versões, confira [Versões e dependências do .NET Framework](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="f912a-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>


<span data-ttu-id="f912a-120">Para obter uma lista das versões do .NET Framework instaladas em um computador, acesse o Registro.</span><span class="sxs-lookup"><span data-stu-id="f912a-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="f912a-121">Use o Editor do Registro para exibir o Registro ou use o código para consultá-lo:</span><span class="sxs-lookup"><span data-stu-id="f912a-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>
 
- <span data-ttu-id="f912a-122">Encontre versões mais recentes do .NET Framework (4.5 e posterior):</span><span class="sxs-lookup"><span data-stu-id="f912a-122">Find newer .NET Framework versions (4.5 and later):</span></span> 
     - [<span data-ttu-id="f912a-123">Usar o Editor do Registro para encontrar versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f912a-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)  
     - [<span data-ttu-id="f912a-124">Usar o código para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="f912a-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)  
     - [<span data-ttu-id="f912a-125">Usar o PowerShell para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="f912a-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
 - <span data-ttu-id="f912a-126">Encontre versões mais antigas do .NET Framework (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="f912a-126">Find older .NET Framework versions (1&#8211;4):</span></span>
     - [<span data-ttu-id="f912a-127">Usar o Editor do Registro para encontrar versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f912a-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
     - [<span data-ttu-id="f912a-128">Usar o código para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="f912a-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)   

<span data-ttu-id="f912a-129">Para obter uma lista das versões do CLR instaladas em um computador, use uma ferramenta ou o código:</span><span class="sxs-lookup"><span data-stu-id="f912a-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>  
  
 - [<span data-ttu-id="f912a-130">Usar a ferramenta Clrver</span><span class="sxs-lookup"><span data-stu-id="f912a-130">Use the Clrver tool</span></span>](#clr_a)  
 - [<span data-ttu-id="f912a-131">Usar o código para consultar a classe Environment</span><span class="sxs-lookup"><span data-stu-id="f912a-131">Use code to query the Environment class</span></span>](#clr_b)  

<span data-ttu-id="f912a-132">Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, confira [Como: Determinar quais atualizações do .NET Framework estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="f912a-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span> 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="f912a-133">Encontrar versões mais recentes do .NET Framework (4.5 e posterior)</span><span class="sxs-lookup"><span data-stu-id="f912a-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="f912a-134">Encontrar versões 4.5 do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="f912a-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="f912a-135">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="f912a-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="f912a-136">Você precisará ter credenciais administrativas para executar o REGEDIT.</span><span class="sxs-lookup"><span data-stu-id="f912a-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="f912a-137">No Editor do Registro, abrir a seguinte subchave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="f912a-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="f912a-138">Se a subchave **Full** não estiver presente, você não terá o .NET Framework 4.5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="f912a-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f912a-139">A pasta **NET Framework Setup** no Registro não começa com um ponto.</span><span class="sxs-lookup"><span data-stu-id="f912a-139">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

3. <span data-ttu-id="f912a-140">Verifique se há uma entrada DWORD chamada **Release**.</span><span class="sxs-lookup"><span data-stu-id="f912a-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="f912a-141">Se ela existir, você terá o .NET Framework 4.5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="f912a-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="f912a-142">Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f912a-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="f912a-143">Na figura a seguir, por exemplo, o valor da entrada **Release** é *378389*, que é a chave de versão do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f912a-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="f912a-144">![Entrada do Registro para o .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span><span class="sxs-lookup"><span data-stu-id="f912a-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="f912a-145">A tabela a seguir lista o valor mínimo da entrada **Release** para cada versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f912a-145">The following table lists the minimum value of the **Release** entry for each .NET Framework version.</span></span> <span data-ttu-id="f912a-146">Use esses valores da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f912a-146">You can use these values as follows:</span></span>

- <span data-ttu-id="f912a-147">Para determinar se uma versão mínima do .NET Framework está presente, teste se o valor DWORD **Release** encontrado no Registro é *superior ou igual* ao valor listado na tabela.</span><span class="sxs-lookup"><span data-stu-id="f912a-147">To determine whether a minimum .NET Framework version is present, test whether the **Release** DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="f912a-148">Por exemplo, se o aplicativo exigir o .NET Framework 4.7 ou posterior, você testará um valor de chave de versão mínima igual a *460798*.</span><span class="sxs-lookup"><span data-stu-id="f912a-148">For example, if your application requires the .NET Framework 4.7 or later, you test for a minimum release key value of *460798*.</span></span>

- <span data-ttu-id="f912a-149">Para testar várias versões, comece com a versão mais recente do .NET Framework e, em seguida, teste cada versão anterior sucessiva.</span><span class="sxs-lookup"><span data-stu-id="f912a-149">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="f912a-150">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f912a-150">.NET Framework version</span></span>|<span data-ttu-id="f912a-151">Valor da liberação de DWORD</span><span class="sxs-lookup"><span data-stu-id="f912a-151">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="f912a-152">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f912a-152">.NET Framework 4.5</span></span>|<span data-ttu-id="f912a-153">378389</span><span class="sxs-lookup"><span data-stu-id="f912a-153">378389</span></span>|
|<span data-ttu-id="f912a-154">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="f912a-154">.NET Framework 4.5.1</span></span>|<span data-ttu-id="f912a-155">378675</span><span class="sxs-lookup"><span data-stu-id="f912a-155">378675</span></span>|
|<span data-ttu-id="f912a-156">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="f912a-156">.NET Framework 4.5.2</span></span>|<span data-ttu-id="f912a-157">379893</span><span class="sxs-lookup"><span data-stu-id="f912a-157">379893</span></span>|
|<span data-ttu-id="f912a-158">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="f912a-158">.NET Framework 4.6</span></span>|<span data-ttu-id="f912a-159">393295</span><span class="sxs-lookup"><span data-stu-id="f912a-159">393295</span></span>|
|<span data-ttu-id="f912a-160">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="f912a-160">.NET Framework 4.6.1</span></span>|<span data-ttu-id="f912a-161">394254</span><span class="sxs-lookup"><span data-stu-id="f912a-161">394254</span></span>|
|<span data-ttu-id="f912a-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f912a-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="f912a-163">394802</span><span class="sxs-lookup"><span data-stu-id="f912a-163">394802</span></span>|
|<span data-ttu-id="f912a-164">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="f912a-164">.NET Framework 4.7</span></span>|<span data-ttu-id="f912a-165">460798</span><span class="sxs-lookup"><span data-stu-id="f912a-165">460798</span></span>|
|<span data-ttu-id="f912a-166">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="f912a-166">.NET Framework 4.7.1</span></span>|<span data-ttu-id="f912a-167">461308</span><span class="sxs-lookup"><span data-stu-id="f912a-167">461308</span></span>|
|<span data-ttu-id="f912a-168">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="f912a-168">.NET Framework 4.7.2</span></span>|<span data-ttu-id="f912a-169">461808</span><span class="sxs-lookup"><span data-stu-id="f912a-169">461808</span></span>|

<span data-ttu-id="f912a-170">Para ver uma tabela completa de chaves de versão para o .NET Framework para versões específicas do sistema operacional Windows, consulte [Chaves de versão do .NET Framework e versões do sistema operacional Windows](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f912a-170">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="f912a-171">Encontrar versões 4.5 e posteriores do .NET Framework com código</span><span class="sxs-lookup"><span data-stu-id="f912a-171">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="f912a-172">Use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="f912a-172">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="f912a-173">A existência da entrada DWORD **Release** na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** indica que o .NET Framework 4.5 ou posterior está instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="f912a-173">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span> 

2. <span data-ttu-id="f912a-174">Verifique o valor da entrada **Release** para determinar a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="f912a-174">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="f912a-175">Para compatibilidade com a versão atual, verifique se há um valor superior ou igual ao valor listado na [tabela de versões do .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="f912a-175">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="f912a-176">O seguinte exemplo verifica o valor da entrada **Release** no Registro para encontrar o .NET Framework 4.5 e versões posteriores que estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="f912a-176">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="f912a-177">Este exemplo segue a prática recomendada para a verificação de versão:</span><span class="sxs-lookup"><span data-stu-id="f912a-177">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="f912a-178">Ele verifica se o valor da entrada **Release** é *superior ou igual* ao valor das chaves de versão conhecidas.</span><span class="sxs-lookup"><span data-stu-id="f912a-178">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="f912a-179">Ele verifica na ordem da versão mais recente para a versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="f912a-179">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="f912a-180">Verificar se há uma versão mínima necessária do .NET Framework (4.5 e posterior) com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="f912a-180">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="f912a-181">Use comandos do PowerShell para verificar o valor da entrada **Release** da subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="f912a-181">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="f912a-182">Os exemplos a seguir verificam o valor da entrada **Release** para determinar se o .NET Framework 4.6.2 ou posterior está instalado.</span><span class="sxs-lookup"><span data-stu-id="f912a-182">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="f912a-183">Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.</span><span class="sxs-lookup"><span data-stu-id="f912a-183">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
```

<span data-ttu-id="f912a-184">Para verificar se há uma versão mínima necessária do .NET Framework, substitua *394802* nesses exemplos por um valor de **Release** da [tabela de versões do .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="f912a-184">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="f912a-185">Encontrar versões mais antigas do .NET Framework (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="f912a-185">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="f912a-186">Encontrar as versões 1&#8211;4 do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="f912a-186">Find .NET Framework versions 1&#8211;4 in the registry</span></span> 
  
1. <span data-ttu-id="f912a-187">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="f912a-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>
  
    <span data-ttu-id="f912a-188">Você precisará ter credenciais administrativas para executar o REGEDIT.</span><span class="sxs-lookup"><span data-stu-id="f912a-188">You must have administrative credentials to run regedit.</span></span>  

2. <span data-ttu-id="f912a-189">No Editor do Registro, abrir a seguinte subchave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="f912a-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>  

    - <span data-ttu-id="f912a-190">Para as versões 1.1 a 3.5 do .NET Framework, cada versão instalada é listada como uma subchave na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**.</span><span class="sxs-lookup"><span data-stu-id="f912a-190">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="f912a-191">Por exemplo, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="f912a-191">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="f912a-192">O número de versão é armazenado como um valor na entrada **Version** da subchave da versão.</span><span class="sxs-lookup"><span data-stu-id="f912a-192">The version number is stored as a value in the version subkey's **Version** entry.</span></span> 
     
    - <span data-ttu-id="f912a-193">Para o .NET Framework 4, a entrada **Version** está localizada na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** ou em ambas as subchaves.</span><span class="sxs-lookup"><span data-stu-id="f912a-193">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f912a-194">A pasta **NET Framework Setup** no Registro não começa com um ponto.</span><span class="sxs-lookup"><span data-stu-id="f912a-194">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="f912a-195">A figura a seguir mostra a subchave e sua entrada **Version** para o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="f912a-195">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="f912a-196">![A entrada do Registro para o .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 e versões anteriores")</span><span class="sxs-lookup"><span data-stu-id="f912a-196">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="f912a-197">Encontrar as versões 1&#8211;4 do .NET Framework com o código</span><span class="sxs-lookup"><span data-stu-id="f912a-197">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="f912a-198">Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="f912a-198">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="f912a-199">O seguinte exemplo localiza as versões 1&#8211;4 do .NET Framework que estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="f912a-199">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a><span data-ttu-id="f912a-200">Encontrar versões do CLR</span><span class="sxs-lookup"><span data-stu-id="f912a-200">Find CLR versions</span></span>
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="f912a-201">Localizar a versão atual do CLR com Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="f912a-201">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="f912a-202">Use a [ferramenta de Versão do CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador:</span><span class="sxs-lookup"><span data-stu-id="f912a-202">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="f912a-203">Em um [Prompt de Comando do Desenvolvedor para o Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), insira `clrver`.</span><span class="sxs-lookup"><span data-stu-id="f912a-203">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="f912a-204">Saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="f912a-204">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="f912a-205">Localizar a versão atual do CLR com a classe Environment</span><span class="sxs-lookup"><span data-stu-id="f912a-205">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f912a-206">Para o .NET Framework 4.5 e versões posteriores, não use a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="f912a-206">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="f912a-207">Em vez disso, consulte o Registro, conforme descrito em [Encontrar versões 4.5 e posteriores do .NET Framework com o código](#net_d).</span><span class="sxs-lookup"><span data-stu-id="f912a-207">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="f912a-208">Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="f912a-208">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span> 

    <span data-ttu-id="f912a-209">O objeto `System.Version` retornado identifica a versão do tempo de execução que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="f912a-209">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="f912a-210">Ele não retorna versões de assembly nem outras versões do tempo de execução que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="f912a-210">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="f912a-211">Para as versões 4, 4.5, 4.5.1 e 4.5.2 do .NET Framework, a representação de cadeia de caracteres do objeto <xref:System.Version> retornado tem o formato 4.0.30319.*xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="f912a-211">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*.</span></span> <span data-ttu-id="f912a-212">Para o .NET Framework 4.6 e versões posteriores, ele tem o formato 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="f912a-212">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>    

2. <span data-ttu-id="f912a-213">Depois de ter o objeto `Version`, consulte-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f912a-213">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="f912a-214">Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f912a-214">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="f912a-215">Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f912a-215">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="f912a-216">Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f912a-216">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f912a-217">Esse método retorna um único valor que reflete a versão do tempo de execução que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="f912a-217">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="f912a-218">Ele não retorna versões de assembly nem outras versões do tempo de execução que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="f912a-218">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>



<span data-ttu-id="f912a-219">O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:</span><span class="sxs-lookup"><span data-stu-id="f912a-219">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="f912a-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f912a-220">See also</span></span>

- [<span data-ttu-id="f912a-221">Como: Determinar quais atualizações do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="f912a-221">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="f912a-222">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="f912a-222">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="f912a-223">Versões e dependências do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f912a-223">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
