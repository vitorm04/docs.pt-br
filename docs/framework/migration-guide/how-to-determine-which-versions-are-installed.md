---
title: 'Como: Determinar quais versões do .NET Framework estão instaladas'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584168"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="b050c-102">Como: Determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="b050c-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="b050c-103">Você pode instalar e executar várias versões do .NET Framework em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="b050c-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="b050c-104">Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="b050c-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="b050c-105">Observe que o .NET Framework consiste em dois componentes, que são versões separadas:</span><span class="sxs-lookup"><span data-stu-id="b050c-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="b050c-106">Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b050c-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="b050c-107">O .NET Framework e assemblies que compartilham o mesmo número de versão.</span><span class="sxs-lookup"><span data-stu-id="b050c-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="b050c-108">O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b050c-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="b050c-109">O CLR é identificado pelo seu próprio número de versão (confira [Versões e dependências](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="b050c-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
<span data-ttu-id="b050c-110">Para obter uma lista precisa nas versões do .NET Framework instaladas no computador, você pode ver o Registro ou consultar o Registro em código:</span><span class="sxs-lookup"><span data-stu-id="b050c-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="b050c-111">Encontrar as versões 1 a 4 do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="b050c-111">Find .NET Framework versions 1-4 in the registry</span></span>](#net_a)  
 [<span data-ttu-id="b050c-112">Encontrar versões 4.5 e posteriores do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="b050c-112">Find .NET Framework versions 4.5 and later in the registry)</span></span>](#net_b)  
 [<span data-ttu-id="b050c-113">Usar o código para consultar o Registro (versões 1 a 4)</span><span class="sxs-lookup"><span data-stu-id="b050c-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="b050c-114">Usar o código para consultar o Registro (versões 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="b050c-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="b050c-115">Uso do PowerShell para consultar o Registro (versões 4.5 e posteriores)</span><span class="sxs-lookup"><span data-stu-id="b050c-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  

 <span data-ttu-id="b050c-116">Para encontrar a versão CLR, é possível usar uma ferramenta ou código:</span><span class="sxs-lookup"><span data-stu-id="b050c-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="b050c-117">Usar a ferramenta Clrver</span><span class="sxs-lookup"><span data-stu-id="b050c-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="b050c-118">Usar o código para consultar a classe System.Environment</span><span class="sxs-lookup"><span data-stu-id="b050c-118">Using code to query the System.Environment class</span></span>](#clr_b)  

> [!NOTE]
> <span data-ttu-id="b050c-119">Há uma diferença entre a versão do .NET Framework e a versão de CLR (common language runtime).</span><span class="sxs-lookup"><span data-stu-id="b050c-119">There is a difference between the .NET Framework version and the common language runtime (CLR) version.</span></span> <span data-ttu-id="b050c-120">O .NET Framework tem controle de versão com base no conjunto de assemblies que forma a Biblioteca de Classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b050c-120">The .NET Framework is versioned based on the set of assemblies that form the .NET Framework Class Library.</span></span> <span data-ttu-id="b050c-121">Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="b050c-121">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> <span data-ttu-id="b050c-122">O CLR tem controle de versão com base no tempo de execução no qual os aplicativos .NET Framework são executados, e uma única versão do CLR geralmente oferece suporte a várias versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b050c-122">The CLR is versioned based on the runtime on which .NET Framework applications execute, and a single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="b050c-123">O CLR versão 4.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2; o CLR versão 4.30319.42000 dá suporte a versões do .NET Framework a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="b050c-123">CLR version 4.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2; CLR version 4.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> <span data-ttu-id="b050c-124">Para obter mais informações, consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b050c-124">For more information, see the <xref:System.Environment.Version?displayProperty=nameWithType> property.</span></span>

 <span data-ttu-id="b050c-125">Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, confira [Como: Determinar quais atualizações do .NET Framework estão instaladas](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="b050c-125">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="b050c-126">Para obter mais informações sobre como instalar o .NET Framework, consulte [Instalar o .NET Framework para desenvolvedores](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="b050c-126">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a><span data-ttu-id="b050c-127">Encontrar versões 1-4 do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="b050c-127">Find .NET Framework versions 1-4 in the registry</span></span> 
  
1.  <span data-ttu-id="b050c-128">No menu **Iniciar**, escolha **Executar**.</span><span class="sxs-lookup"><span data-stu-id="b050c-128">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="b050c-129">Na caixa **Abrir**, insira **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b050c-129">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="b050c-130">Você deve ter credenciais administrativas para executar o regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="b050c-130">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="b050c-131">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="b050c-131">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="b050c-132">Para o .NET Framework versões 1.1 a 3.5, as versões instaladas são listadas como as subchaves da subchave `NDP`.</span><span class="sxs-lookup"><span data-stu-id="b050c-132">For .NET Framework versions 1.1 through 3.5, the installed versions are listed as subkeys under the `NDP` subkey.</span></span> <span data-ttu-id="b050c-133">O número de versão é armazenado na entrada **Version** da subchave da versão.</span><span class="sxs-lookup"><span data-stu-id="b050c-133">The version number is stored in the version subkey's **Version** entry.</span></span> 
     
     <span data-ttu-id="b050c-134">Para o .NET Framework 4, a entrada **Version** está sob a subchave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client`, a subchave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` ou sob as duas subchaves.</span><span class="sxs-lookup"><span data-stu-id="b050c-134">For .NET Framework 4, the **Version** entry is under the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` subkey, the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b050c-135">A pasta "NET Framework Setup” no Registro não começa por um ponto.</span><span class="sxs-lookup"><span data-stu-id="b050c-135">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="b050c-136">A figura a seguir mostra a subchave para o .NET Framework 3.5, juntamente com sua entrada **Version**.</span><span class="sxs-lookup"><span data-stu-id="b050c-136">The following figure shows that the subkey for the .NET Framework 3.5 along with its **Version** entry.</span></span>

     <span data-ttu-id="b050c-137">![A entrada do Registro para o .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 e versões anteriores")</span><span class="sxs-lookup"><span data-stu-id="b050c-137">![The registry entry for the .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 and earlier versions")</span></span>

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="b050c-138">Encontrar versões 4.5 do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="b050c-138">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="b050c-139">No menu **Iniciar**, escolha **Executar**.</span><span class="sxs-lookup"><span data-stu-id="b050c-139">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="b050c-140">Na caixa **Abrir**, insira **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b050c-140">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="b050c-141">Você deve ter credenciais administrativas para executar o regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="b050c-141">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="b050c-142">No Editor do Registro, abrir a seguinte subchave:</span><span class="sxs-lookup"><span data-stu-id="b050c-142">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="b050c-143">Observe que o caminho até a subchave `Full` inclui a subchave `Net Framework` em vez de `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="b050c-143">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b050c-144">Se a subchave `Full` não estiver presente, então você não terá o .NET Framework 4.5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="b050c-144">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="b050c-145">Procure um valor DWORD chamado `Release`.</span><span class="sxs-lookup"><span data-stu-id="b050c-145">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="b050c-146">A existência do DWORD `Release` indica que o .NET Framework 4.5 ou posterior foi instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="b050c-146">The existence of the `Release` DWORD indicates that .NET Framework 4.5 or later has been installed on that computer.</span></span> <span data-ttu-id="b050c-147">Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b050c-147">Its value is a release key that corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="b050c-148">Na figura a seguir, por exemplo, o valor do DWORD `Release` é 378389, que é a chave de versão do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b050c-148">In the following figure, for example, the value of the `Release` DWORD is 378389, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="b050c-149">![A entrada do Registro para o .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="b050c-149">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

<span data-ttu-id="b050c-150">A tabela a seguir lista o valor mínimo do DWORD `Release` para cada versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b050c-150">The following table lists the minimum value of the `Release` DWORD for each .NET Framework version.</span></span> <span data-ttu-id="b050c-151">Use esses valores da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b050c-151">You can use these values as follows:</span></span>

- <span data-ttu-id="b050c-152">Para determinar se uma versão mínima do .NET Framework está presente, teste se o valor de DWORD `Release` encontrado no Registro é *maior ou igual ao* valor listado na tabela.</span><span class="sxs-lookup"><span data-stu-id="b050c-152">To determine whether a minimum .NET Framework version is present, test whether the `Release` DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="b050c-153">Por exemplo, se o seu aplicativo exigir o .NET Framework 4.7 ou posterior, você verificaria a existência de um valor de versão mínima de 460798.</span><span class="sxs-lookup"><span data-stu-id="b050c-153">For example, if your application requires .NET Framework 4.7 or later, you would test for a minimum release key value of 460798.</span></span>

- <span data-ttu-id="b050c-154">Para testar várias versões, comece com a versão mais recente do .NET Framework e, em seguida, teste cada versão anterior sucessiva.</span><span class="sxs-lookup"><span data-stu-id="b050c-154">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|<span data-ttu-id="b050c-155">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b050c-155">.NET Framework Version</span></span>|<span data-ttu-id="b050c-156">Valor da liberação de DWORD</span><span class="sxs-lookup"><span data-stu-id="b050c-156">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="b050c-157">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b050c-157">.NET Framework 4.5</span></span>|<span data-ttu-id="b050c-158">378389</span><span class="sxs-lookup"><span data-stu-id="b050c-158">378389</span></span>|
|<span data-ttu-id="b050c-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="b050c-159">.NET Framework 4.5.1</span></span>|<span data-ttu-id="b050c-160">378675</span><span class="sxs-lookup"><span data-stu-id="b050c-160">378675</span></span>|
|<span data-ttu-id="b050c-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="b050c-161">.NET Framework 4.5.2</span></span>|<span data-ttu-id="b050c-162">379893</span><span class="sxs-lookup"><span data-stu-id="b050c-162">379893</span></span>|
|<span data-ttu-id="b050c-163">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="b050c-163">.NET Framework 4.6</span></span>|<span data-ttu-id="b050c-164">393295</span><span class="sxs-lookup"><span data-stu-id="b050c-164">393295</span></span>|
|<span data-ttu-id="b050c-165">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="b050c-165">.NET Framework 4.6.1</span></span>|<span data-ttu-id="b050c-166">394254</span><span class="sxs-lookup"><span data-stu-id="b050c-166">394254</span></span>|
|<span data-ttu-id="b050c-167">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b050c-167">.NET Framework 4.6.2</span></span>|<span data-ttu-id="b050c-168">394802</span><span class="sxs-lookup"><span data-stu-id="b050c-168">394802</span></span>|
|<span data-ttu-id="b050c-169">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b050c-169">.NET Framework 4.7</span></span>|<span data-ttu-id="b050c-170">460798</span><span class="sxs-lookup"><span data-stu-id="b050c-170">460798</span></span>|
|<span data-ttu-id="b050c-171">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b050c-171">.NET Framework 4.7.1</span></span>|<span data-ttu-id="b050c-172">461308</span><span class="sxs-lookup"><span data-stu-id="b050c-172">461308</span></span>|
|<span data-ttu-id="b050c-173">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b050c-173">.NET Framework 4.7.2</span></span>|<span data-ttu-id="b050c-174">461808</span><span class="sxs-lookup"><span data-stu-id="b050c-174">461808</span></span>|

<span data-ttu-id="b050c-175">Para ver uma tabela completa de chaves de versão para o .NET Framework para versões específicas do sistema operacional Windows, consulte [Chaves de versão do .NET Framework e versões do sistema operacional Windows](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b050c-175">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a><span data-ttu-id="b050c-176">Encontrar versões 1-4 do .NET Framework com código</span><span class="sxs-lookup"><span data-stu-id="b050c-176">Find .NET Framework versions 1-4 with code</span></span>

- <span data-ttu-id="b050c-177">Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave `Software\Microsoft\NET Framework Setup\NDP\` sob o branch `HKEY_LOCAL_MACHINE` no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="b050c-177">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the `Software\Microsoft\NET Framework Setup\NDP\` subkey under `HKEY_LOCAL_MACHINE` branch in the Windows registry.</span></span>

     <span data-ttu-id="b050c-178">O código a seguir mostra um exemplo dessa consulta.</span><span class="sxs-lookup"><span data-stu-id="b050c-178">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b050c-179">Esse código não mostra como detectar o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b050c-179">This code does not show how to detect .NET Framework 4.5 or later.</span></span> <span data-ttu-id="b050c-180">Verifique a DWORD `Release` para detectar as versões, conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b050c-180">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="b050c-181">Para conhecer o código que detecta o .NET Framework 4.5 ou versões posteriores, confira a próxima seção neste artigo.</span><span class="sxs-lookup"><span data-stu-id="b050c-181">For code that detects .NET Framework 4.5 or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="b050c-182">Encontrar versões 4.5 e posteriores do .NET Framework com código</span><span class="sxs-lookup"><span data-stu-id="b050c-182">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="b050c-183">A existência do DWORD `Release` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` indica que o .NET Framework 4.5 ou posterior foi instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="b050c-183">The existence of the `Release` DWORD in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key indicates that the .NET Framework 4.5 or later is installed on a computer.</span></span> <span data-ttu-id="b050c-184">O valor da palavra-chave indica a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="b050c-184">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="b050c-185">Para verificar essa palavra-chave, use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> para acessar a subchave no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="b050c-185">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the subkey in the Windows registry.</span></span>

2. <span data-ttu-id="b050c-186">Verifique o valor da palavra-chave `Release` para determinar a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="b050c-186">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="b050c-187">Para ser compatível com versões posteriores, você pode verificar um valor maior ou igual ao valor listado na tabela, na seção [Encontrar versões 4.5 e posteriores do .NET Framework no Registro](#net_b).</span><span class="sxs-lookup"><span data-stu-id="b050c-187">To be forward-compatible, you can check for a value greater than or equal to the value listed in the table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section.</span></span>

<span data-ttu-id="b050c-188">O exemplo a seguir verifica o valor `Release` no Registro para determinar se o .NET Framework 4.5 ou uma versão posterior está instalada.</span><span class="sxs-lookup"><span data-stu-id="b050c-188">The following example checks the `Release` value in the registry to determine whether .NET Framework 4.5 or a later version is installed.</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="b050c-189">Este exemplo segue a prática recomendada para a verificação de versão:</span><span class="sxs-lookup"><span data-stu-id="b050c-189">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="b050c-190">Ele verifica se o valor da entrada `Release` é *maior ou igual* ao valor das chaves de versão conhecidas.</span><span class="sxs-lookup"><span data-stu-id="b050c-190">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="b050c-191">Ele verifica na ordem da versão mais recente para a versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="b050c-191">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="b050c-192">Verificar se há uma versão mínima necessária do .NET Framework (4.5 e posterior) com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="b050c-192">Check for a minimum required .NET Framework version (4.5 and later) with PowerShell</span></span>

<span data-ttu-id="b050c-193">O exemplo a seguir verificará o valor da palavra-chave `Release` para determinar se o .NET Framework 4.6.2 ou superior está instalado (retornando `True` se estiver, e `False`, caso contrário).</span><span class="sxs-lookup"><span data-stu-id="b050c-193">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="b050c-194">Localizar a versão atual do CLR com Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="b050c-194">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="b050c-195">Use a Ferramenta de Versão do CLR (Clrver.exe) para determinar quais versões do Common Language Runtime estão instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="b050c-195">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

<span data-ttu-id="b050c-196">Usando um Prompt de Comando do Desenvolvedor para o Visual Studio, insira `clrver`.</span><span class="sxs-lookup"><span data-stu-id="b050c-196">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="b050c-197">Esse comando gera uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="b050c-197">This command produces output similar to the following:</span></span>

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

<span data-ttu-id="b050c-198">Para saber mais sobre como usar essa ferramenta, veja [ Clrver.exe (Ferramenta de Versão do CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b050c-198">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="b050c-199">Localizar a versão atual do CLR com a classe Environment</span><span class="sxs-lookup"><span data-stu-id="b050c-199">Find the current CLR version with the Environment class</span></span>

<span data-ttu-id="b050c-200">Recupere o valor da propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version> que identifica a versão do tempo de execução que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="b050c-200">You can retrieve the value of the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="b050c-201">Essa propriedade retorna um valor único que reflete a versão do tempo de execução que está executando o código; ela não retorna versões de assembly ou outras versões do tempo de execução que podem ter sido instaladas no computador. Você pode usar a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType> para obter o identificador de versão principal (por exemplo, "4" para a versão 4.0), a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType> para obter o identificador de versão secundária (por exemplo, "0" para a versão 4.0), ou o método <xref:System.Version.ToString%2A?displayProperty=nameWithType> para obter a cadeia de caracteres completa da versão (por exemplo, "4.0.30319.18010", conforme mostra o código a seguir).</span><span class="sxs-lookup"><span data-stu-id="b050c-201">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> 

<span data-ttu-id="b050c-202">Para as versões do .NET Framework 4, 4.5, 4.5.1 e 4.5.2, a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> retorna um objeto <xref:System.Version> cuja representação da cadeia de caracteres tem a forma `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="b050c-202">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="b050c-203">Para o .NET Framework 4.6 e posterior, ela tem a forma `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="b050c-203">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b050c-204">Para o .NET Framework 4.5 e posterior, não é recomendado o uso da propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b050c-204">For the .NET Framework 4.5 and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="b050c-205">Em vez disso, recomendamos a consulta do Registro, conforme descrito na seção [Para encontrar versões do .NET Framework consultando o Registro no código (.NET Framework 4.5 e posterior)](#net_d) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="b050c-205">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

<span data-ttu-id="b050c-206">O exemplo a seguir usou a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="b050c-206">The following example used the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve runtime version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="b050c-207">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b050c-207">See also</span></span>

- [<span data-ttu-id="b050c-208">Como: Determinar quais atualizações do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="b050c-208">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="b050c-209">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="b050c-209">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="b050c-210">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="b050c-210">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)
