---
title: "Como determinar quais versões do .NET Framework estão instaladas"
ms.date: 08/09/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
caps.latest.revision: 62
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: afb01fd47ed2ce3b9c5838f3a8f61c8d34147378
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="d9d64-102">Como determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="d9d64-102">How to: Determine Which .NET Framework Versions Are Installed</span></span>
<span data-ttu-id="d9d64-103">Você pode instalar e executar várias versões do .NET Framework em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="d9d64-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="d9d64-104">Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9d64-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="d9d64-105">Observe que o .NET Framework consiste em dois componentes, que são versões separadas:</span><span class="sxs-lookup"><span data-stu-id="d9d64-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="d9d64-106">Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d9d64-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="d9d64-107">O .NET Framework e assemblies que compartilham o mesmo número de versão.</span><span class="sxs-lookup"><span data-stu-id="d9d64-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="d9d64-108">O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d9d64-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="d9d64-109">O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="d9d64-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="d9d64-110">Para obter uma lista precisa nas versões do .NET Framework instaladas no computador, você pode ver o Registro ou consultar o Registro em código:</span><span class="sxs-lookup"><span data-stu-id="d9d64-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="d9d64-111">Visualizar o Registro (versões 1 a 4)</span><span class="sxs-lookup"><span data-stu-id="d9d64-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="d9d64-112">Visualizar o Registro (versões 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="d9d64-113">Usar o código para consultar o Registro (versões 1 a 4)</span><span class="sxs-lookup"><span data-stu-id="d9d64-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="d9d64-114">Usar o código para consultar o Registro (versões 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="d9d64-115">Uso do PowerShell para consultar o Registro (versões 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="d9d64-116">Para encontrar a versão CLR, é possível usar uma ferramenta ou código:</span><span class="sxs-lookup"><span data-stu-id="d9d64-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="d9d64-117">Usar a ferramenta Clrver</span><span class="sxs-lookup"><span data-stu-id="d9d64-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="d9d64-118">Usar o código para consultar a classe System.Environment</span><span class="sxs-lookup"><span data-stu-id="d9d64-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="d9d64-119">Para saber mais sobre como detectar as atualizações instaladas para cada versão do .NET Framework, veja [Como determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="d9d64-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="d9d64-120">Para obter mais informações sobre como instalar o .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="d9d64-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="d9d64-121">Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 1 a 4)</span><span class="sxs-lookup"><span data-stu-id="d9d64-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="d9d64-122">No menu **Iniciar**, escolha **Executar**.</span><span class="sxs-lookup"><span data-stu-id="d9d64-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="d9d64-123">Na caixa **Abrir**, insira **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="d9d64-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="d9d64-124">Você deve ter credenciais administrativas para executar o regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="d9d64-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="d9d64-125">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="d9d64-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="d9d64-126">As versões instaladas estão listadas abaixo da subchave NDP.</span><span class="sxs-lookup"><span data-stu-id="d9d64-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="d9d64-127">O número de versão é armazenado na entrada **Version**.</span><span class="sxs-lookup"><span data-stu-id="d9d64-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="d9d64-128">Para o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a entrada **Version** está sob a subchave Client ou Full (em NDP) ou em ambas as subchaves.</span><span class="sxs-lookup"><span data-stu-id="d9d64-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="d9d64-129">A pasta "NET Framework Setup” no Registro não começa por um ponto.</span><span class="sxs-lookup"><span data-stu-id="d9d64-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="d9d64-130">Para encontrar versões do .NET Framework visualizando o Registro (.NET Framework 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="d9d64-131">No menu **Iniciar**, escolha **Executar**.</span><span class="sxs-lookup"><span data-stu-id="d9d64-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="d9d64-132">Na caixa **Abrir**, insira **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="d9d64-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="d9d64-133">Você deve ter credenciais administrativas para executar o regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="d9d64-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="d9d64-134">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="d9d64-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="d9d64-135">Observe que o caminho até a subchave `Full` inclui a subchave `Net Framework` em vez de `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="d9d64-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9d64-136">Se a subchave `Full` não estiver presente, então você não terá o .NET Framework 4.5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="d9d64-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="d9d64-137">Procure um valor DWORD chamado `Release`.</span><span class="sxs-lookup"><span data-stu-id="d9d64-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="d9d64-138">A existência da DWORD `Release` indica que o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou mais recente foi instalado naquele computador.</span><span class="sxs-lookup"><span data-stu-id="d9d64-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="d9d64-139">![A entrada do Registro para o .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="d9d64-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="d9d64-140">O valor do DWORD de `Release` indica qual versão do .NET Framework está instalada.</span><span class="sxs-lookup"><span data-stu-id="d9d64-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    |<span data-ttu-id="d9d64-141">Valor da liberação de DWORD</span><span class="sxs-lookup"><span data-stu-id="d9d64-141">Value of the Release DWORD</span></span>|<span data-ttu-id="d9d64-142">Versão</span><span class="sxs-lookup"><span data-stu-id="d9d64-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="d9d64-143">378389</span><span class="sxs-lookup"><span data-stu-id="d9d64-143">378389</span></span>|<span data-ttu-id="d9d64-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d9d64-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="d9d64-145">378675</span><span class="sxs-lookup"><span data-stu-id="d9d64-145">378675</span></span>|<span data-ttu-id="d9d64-146">.NET Framework 4.5.1 instalado com Windows 8.1 ou Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d9d64-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="d9d64-147">378758</span><span class="sxs-lookup"><span data-stu-id="d9d64-147">378758</span></span>|<span data-ttu-id="d9d64-148">.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="d9d64-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="d9d64-149">379893</span><span class="sxs-lookup"><span data-stu-id="d9d64-149">379893</span></span>|<span data-ttu-id="d9d64-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="d9d64-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="d9d64-151">Em sistemas Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="d9d64-151">On Windows 10 systems: 393295</span></span><br /><br /> <span data-ttu-id="d9d64-152">Em todas as outras versões do sistema operacional: 393297</span><span class="sxs-lookup"><span data-stu-id="d9d64-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="d9d64-153">Em sistemas com a Atualização de novembro do Windows 10: 394254</span><span class="sxs-lookup"><span data-stu-id="d9d64-153">On Windows 10 November Update systems: 394254</span></span><br /><br /> <span data-ttu-id="d9d64-154">Em todas as outras versões do sistema operacional: 394271</span><span class="sxs-lookup"><span data-stu-id="d9d64-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="d9d64-155">Na Atualização de Aniversário do Windows 10: 394802</span><span class="sxs-lookup"><span data-stu-id="d9d64-155">On Windows 10 Anniversary Update: 394802</span></span><br /><br /> <span data-ttu-id="d9d64-156">Em todas as outras versões do sistema operacional: 394806</span><span class="sxs-lookup"><span data-stu-id="d9d64-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="d9d64-157">No Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="d9d64-157">On Windows 10 Creators Update: 460798</span></span><br/><br/> <span data-ttu-id="d9d64-158">Em todas as outras versões do sistema operacional: 460805</span><span class="sxs-lookup"><span data-stu-id="d9d64-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="d9d64-159">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d9d64-159">.NET Framework 4.7</span></span> |

<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="d9d64-160">Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 1 a 4)</span><span class="sxs-lookup"><span data-stu-id="d9d64-160">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="d9d64-161">Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\ em HKEY_LOCAL_MACHINE no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9d64-161">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="d9d64-162">O código a seguir mostra um exemplo dessa consulta.</span><span class="sxs-lookup"><span data-stu-id="d9d64-162">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d9d64-163">Este código não mostra como detectar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d9d64-163">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="d9d64-164">Verifique a DWORD `Release` para detectar as versões, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="d9d64-164">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="d9d64-165">Para saber o código que detecta o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou versões posteriores, veja a próxima seção deste artigo.</span><span class="sxs-lookup"><span data-stu-id="d9d64-165">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     <span data-ttu-id="d9d64-166">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9d64-166">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]</span></span>

     <span data-ttu-id="d9d64-167">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d64-167">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="d9d64-168">Para encontrar versões do .NET Framework consultando o Registro em código (.NET Framework 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-168">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="d9d64-169">A existência de DWORD `Release` indica que o .NET Framework 4.5 ou posteriores foi instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="d9d64-169">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="d9d64-170">O valor da palavra-chave indica a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="d9d64-170">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="d9d64-171">Para verificar a palavra-chave, use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> da classe <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> para acessar a subchave Software\Microsoft\NET Framework Setup\NDP\v4\Full em HKEY_LOCAL_MACHINE no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9d64-171">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="d9d64-172">Verifique o valor da palavra-chave `Release` para determinar a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="d9d64-172">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="d9d64-173">Para ser compatível direto, você pode verificar se há um valor maior ou igual aos valores listados na tabela.</span><span class="sxs-lookup"><span data-stu-id="d9d64-173">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="d9d64-174">Veja a seguir as versões e palavras-chave `Release` associadas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9d64-174">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    |<span data-ttu-id="d9d64-175">Versão</span><span class="sxs-lookup"><span data-stu-id="d9d64-175">Version</span></span>|<span data-ttu-id="d9d64-176">Valor da liberação de DWORD</span><span class="sxs-lookup"><span data-stu-id="d9d64-176">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="d9d64-177">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d9d64-177">.NET Framework 4.5</span></span>|<span data-ttu-id="d9d64-178">378389</span><span class="sxs-lookup"><span data-stu-id="d9d64-178">378389</span></span>|
    |<span data-ttu-id="d9d64-179">.NET Framework 4.5.1 instalado com Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d9d64-179">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="d9d64-180">378675</span><span class="sxs-lookup"><span data-stu-id="d9d64-180">378675</span></span>|
    |<span data-ttu-id="d9d64-181">.NET Framework 4.5.1 instalado no Windows 8, Windows 7 SP1 ou Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="d9d64-181">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="d9d64-182">378758</span><span class="sxs-lookup"><span data-stu-id="d9d64-182">378758</span></span>|
    |<span data-ttu-id="d9d64-183">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="d9d64-183">.NET Framework 4.5.2</span></span>|<span data-ttu-id="d9d64-184">379893</span><span class="sxs-lookup"><span data-stu-id="d9d64-184">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<span data-ttu-id="d9d64-185"> instalado com o Windows 10</span><span class="sxs-lookup"><span data-stu-id="d9d64-185"> installed with Windows 10</span></span>|<span data-ttu-id="d9d64-186">393295</span><span class="sxs-lookup"><span data-stu-id="d9d64-186">393295</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<span data-ttu-id="d9d64-187"> instalado em todas as outras versões do sistema operacional Windows</span><span class="sxs-lookup"><span data-stu-id="d9d64-187"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="d9d64-188">393297</span><span class="sxs-lookup"><span data-stu-id="d9d64-188">393297</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<span data-ttu-id="d9d64-189"> instalado no Windows 10</span><span class="sxs-lookup"><span data-stu-id="d9d64-189"> installed on Windows 10</span></span>|<span data-ttu-id="d9d64-190">394254</span><span class="sxs-lookup"><span data-stu-id="d9d64-190">394254</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<span data-ttu-id="d9d64-191"> instalado em todas as outras versões do sistema operacional Windows</span><span class="sxs-lookup"><span data-stu-id="d9d64-191"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="d9d64-192">394271</span><span class="sxs-lookup"><span data-stu-id="d9d64-192">394271</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<span data-ttu-id="d9d64-193"> instalado na Atualização de Aniversário do Windows 10</span><span class="sxs-lookup"><span data-stu-id="d9d64-193"> installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="d9d64-194">394802</span><span class="sxs-lookup"><span data-stu-id="d9d64-194">394802</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<span data-ttu-id="d9d64-195"> instalado em todas as outras versões do sistema operacional Windows</span><span class="sxs-lookup"><span data-stu-id="d9d64-195"> installed on all other Windows OS versions</span></span>|<span data-ttu-id="d9d64-196">394806</span><span class="sxs-lookup"><span data-stu-id="d9d64-196">394806</span></span>|
    |<span data-ttu-id="d9d64-197">.NET Framework 4.7 instalado no Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="d9d64-197">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="d9d64-198">460798</span><span class="sxs-lookup"><span data-stu-id="d9d64-198">460798</span></span>|
    |<span data-ttu-id="d9d64-199">.NET Framework 4.7 instalado em todas as outras versões do sistema operacional Windows</span><span class="sxs-lookup"><span data-stu-id="d9d64-199">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="d9d64-200">460805</span><span class="sxs-lookup"><span data-stu-id="d9d64-200">460805</span></span>|

     <span data-ttu-id="d9d64-201">A exemplo a seguir verifica o valor `Release` no Registro para determinar se o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou uma versão posterior do .NET Framework está instalada.</span><span class="sxs-lookup"><span data-stu-id="d9d64-201">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     <span data-ttu-id="d9d64-202">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9d64-202">[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]   [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]</span></span>

     <span data-ttu-id="d9d64-203">Este exemplo segue a prática recomendada para a verificação de versão:</span><span class="sxs-lookup"><span data-stu-id="d9d64-203">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="d9d64-204">Ele verifica se o valor da entrada `Release` é *maior ou igual* ao valor das chaves de versão conhecidas.</span><span class="sxs-lookup"><span data-stu-id="d9d64-204">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="d9d64-205">Ele verifica na ordem da versão mais recente para a versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="d9d64-205">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
#### <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="d9d64-206">Para verificar se há uma versão do .NET Framework mínima necessária consultando o Registro no PowerShell (.NET Framework 4.5 e versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="d9d64-206">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="d9d64-207">O exemplo a seguir verificará o valor da palavra-chave `Release` para determinar se o .NET Framework 4.6.2 ou superior estiver instalado, independentemente da versão do sistema operacional Windows (retornando `True` se ele for e `False` caso contrário).</span><span class="sxs-lookup"><span data-stu-id="d9d64-207">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "hklm:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | % { $_ -ge 394802 } 
    ```

    <span data-ttu-id="d9d64-208">É possível substituir `394802` no exemplo anterior por outro valor da tabela a seguir para verificar se há uma versão mínima necessária do .NET Framework diferente.</span><span class="sxs-lookup"><span data-stu-id="d9d64-208">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="d9d64-209">Versão</span><span class="sxs-lookup"><span data-stu-id="d9d64-209">Version</span></span>|<span data-ttu-id="d9d64-210">Valor mínimo da versão DWORD</span><span class="sxs-lookup"><span data-stu-id="d9d64-210">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="d9d64-211">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d9d64-211">.NET Framework 4.5</span></span>|<span data-ttu-id="d9d64-212">378389</span><span class="sxs-lookup"><span data-stu-id="d9d64-212">378389</span></span>|
    |<span data-ttu-id="d9d64-213">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="d9d64-213">.NET Framework 4.5.1</span></span>|<span data-ttu-id="d9d64-214">378675</span><span class="sxs-lookup"><span data-stu-id="d9d64-214">378675</span></span>|
    |<span data-ttu-id="d9d64-215">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="d9d64-215">.NET Framework 4.5.2</span></span>|<span data-ttu-id="d9d64-216">379893</span><span class="sxs-lookup"><span data-stu-id="d9d64-216">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="d9d64-217">393295</span><span class="sxs-lookup"><span data-stu-id="d9d64-217">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="d9d64-218">394254</span><span class="sxs-lookup"><span data-stu-id="d9d64-218">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="d9d64-219">394802</span><span class="sxs-lookup"><span data-stu-id="d9d64-219">394802</span></span>|
    |<span data-ttu-id="d9d64-220">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d9d64-220">.NET Framework 4.7</span></span>|<span data-ttu-id="d9d64-221">460798</span><span class="sxs-lookup"><span data-stu-id="d9d64-221">460798</span></span>|

<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="d9d64-222">Para localizar a versão de tempo de execução atual usando a ferramenta Clrver</span><span class="sxs-lookup"><span data-stu-id="d9d64-222">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="d9d64-223">Use a Ferramenta de Versão do CLR (Clrver.exe) para determinar quais versões do Common Language Runtime estão instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="d9d64-223">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="d9d64-224">Em um prompt de comando do Visual Studio, insira `clrver`.</span><span class="sxs-lookup"><span data-stu-id="d9d64-224">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="d9d64-225">Esse comando gera uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d64-225">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="d9d64-226">Para saber mais sobre como usar essa ferramenta, veja [ Clrver.exe (Ferramenta de Versão do CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d9d64-226">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="d9d64-227">Localizar a versão do tempo de execução atual ao consultar a classe Environment no código</span><span class="sxs-lookup"><span data-stu-id="d9d64-227">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="d9d64-228">Consulte a propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para recuperar um objeto <xref:System.Version> que identifica a versão do tempo de execução que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="d9d64-228">Query the <xref:System.Environment.Version%2A?displayProperty=fullName> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="d9d64-229">Você pode usar a propriedade <xref:System.Version.Major%2A?displayProperty=fullName> para obter o identificador de versão principal (por exemplo, "4" para a versão 4,0), a propriedade <xref:System.Version.Minor%2A?displayProperty=fullName> para obter o identificador de versão secundária (por exemplo, "0" para a versão 4,0), ou o método <xref:System.Object.ToString%2A?displayProperty=fullName> para obter a cadeia de caracteres de versão inteira (por exemplo, "4.0.30319.18010", conforme mostrado no código a seguir).</span><span class="sxs-lookup"><span data-stu-id="d9d64-229">You can use the <xref:System.Version.Major%2A?displayProperty=fullName> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=fullName> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=fullName> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="d9d64-230">Essa propriedade retorna um valor único que reflete a versão do tempo de execução que está executando o código; ela não retorna versões do assembly ou outras versões de tempo de execução que podem ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="d9d64-230">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="d9d64-231">Para as versões do .NET Framework 4, 4.5, 4.5.1 e 4.5.2, a propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> retorna um objeto <xref:System.Version> cuja representação da cadeia de caracteres tem a forma `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="d9d64-231">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=fullName> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="d9d64-232">Para o .NET Framework 4.6 e posterior, ela tem a forma `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="d9d64-232">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d9d64-233">Para o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e posterior, não é recomendado o uso da propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para detectar a versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d9d64-233">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=fullName> property to detect the version of the runtime.</span></span> <span data-ttu-id="d9d64-234">Em vez disso, recomendamos a consulta do Registro, conforme descrito na seção [Para encontrar versões do .NET Framework consultando o Registro no código (.NET Framework 4.5 e posterior)](#net_d) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="d9d64-234">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="d9d64-235">Veja um exemplo de consulta da propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> para obtenção de informações de versão do tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="d9d64-235">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=fullName> property for runtime version information:</span></span>

     <span data-ttu-id="d9d64-236">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9d64-236">[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]    [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]</span></span>

     <span data-ttu-id="d9d64-237">O exemplo produz uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d64-237">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="d9d64-238">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9d64-238">See Also</span></span>
 <span data-ttu-id="d9d64-239">[Como determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="d9d64-239">[How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md) </span></span>  
 <span data-ttu-id="d9d64-240">[Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="d9d64-240">[Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md) </span></span>  
 [<span data-ttu-id="d9d64-241">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="d9d64-241">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)

