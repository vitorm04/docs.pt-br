---
title: Determinar quais versões do .NET Framework estão instaladas
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738194"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="3b57c-102">Como determinar quais versões do .NET Framework estão instaladas</span><span class="sxs-lookup"><span data-stu-id="3b57c-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="3b57c-103">Os usuários podem [instalar](../install/index.md) e executar várias versões do .NET Framework em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="3b57c-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="3b57c-104">Quando você desenvolve ou implanta um aplicativo, é necessário saber qual versão do .NET Framework está instalada no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="3b57c-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="3b57c-105">O .NET Framework consiste em dois componentes principais, que têm o controle de versão feito separadamente:</span><span class="sxs-lookup"><span data-stu-id="3b57c-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="3b57c-106">Um conjunto de assemblies que são coleções de tipos e recursos que fornecem a funcionalidade para os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3b57c-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="3b57c-107">O .NET Framework e assemblies que compartilham o mesmo número de versão.</span><span class="sxs-lookup"><span data-stu-id="3b57c-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="3b57c-108">O Common Language Runtime (CLR) que gerencia e executa o código dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3b57c-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="3b57c-109">O CLR é identificado por seu próprio número de versão (consulte [versões e dependências](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="3b57c-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="3b57c-110">Cada nova versão do .NET Framework retém recursos de versões anteriores e adiciona novos recursos.</span><span class="sxs-lookup"><span data-stu-id="3b57c-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="3b57c-111">Você pode carregar várias versões do .NET Framework em um único computador ao mesmo tempo, o que significa que você pode instalar o .NET Framework sem precisar desinstalar as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="3b57c-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="3b57c-112">Em geral, você não deve desinstalar as versões anteriores do .NET Framework, porque um aplicativo que você usa pode depender de uma versão específica e pode ser interrompido caso essa versão seja removida.</span><span class="sxs-lookup"><span data-stu-id="3b57c-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="3b57c-113">Há uma diferença entre a versão do .NET Framework e a versão do CLR:</span><span class="sxs-lookup"><span data-stu-id="3b57c-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="3b57c-114">A versão do .NET Framework baseia-se no conjunto de assemblies que forma a biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b57c-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="3b57c-115">Por exemplo, versões do .NET Framework incluem 4.5, 4.6.1 e 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="3b57c-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="3b57c-116">A versão do CLR baseia-se no runtime no qual os aplicativos .NET Framework são executados.</span><span class="sxs-lookup"><span data-stu-id="3b57c-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="3b57c-117">Uma única versão do CLR geralmente dá suporte a várias versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b57c-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="3b57c-118">Por exemplo, o CLR versão 4.0.30319.*xxxxx* dá suporte ao .NET Framework versões 4 a 4.5.2, em que *xxxxx* é menor que 42000; o CLR versão 4.0.30319.42000 dá suporte a versões do .NET Framework a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="3b57c-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="3b57c-119">Para obter mais informações sobre as versões, confira [Versões e dependências do .NET Framework](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="3b57c-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="3b57c-120">O registro contém uma lista das versões de .NET Framework instaladas em um computador.</span><span class="sxs-lookup"><span data-stu-id="3b57c-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="3b57c-121">Você pode usar o editor do registro para exibir o registro ou consultá-lo com código:</span><span class="sxs-lookup"><span data-stu-id="3b57c-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="3b57c-122">Encontre versões mais recentes do .NET Framework (4.5 e posterior):</span><span class="sxs-lookup"><span data-stu-id="3b57c-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="3b57c-123">Usar o Editor do Registro para encontrar versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b57c-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="3b57c-124">Usar o código para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="3b57c-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="3b57c-125">Usar o PowerShell para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="3b57c-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="3b57c-126">Localizar versões mais antigas do .NET Framework (de 1 a 4):</span><span class="sxs-lookup"><span data-stu-id="3b57c-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="3b57c-127">Usar o Editor do Registro para encontrar versões do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b57c-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="3b57c-128">Usar o código para consultar versões do .NET Framework no Registro</span><span class="sxs-lookup"><span data-stu-id="3b57c-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="3b57c-129">Para obter uma lista das versões do CLR instaladas em um computador, use uma ferramenta ou o código:</span><span class="sxs-lookup"><span data-stu-id="3b57c-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="3b57c-130">Usar a ferramenta Clrver</span><span class="sxs-lookup"><span data-stu-id="3b57c-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="3b57c-131">Usar o código para consultar a classe Environment</span><span class="sxs-lookup"><span data-stu-id="3b57c-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="3b57c-132">Para obter informações sobre como detectar as atualizações instaladas para cada versão do .NET Framework, consulte [como: determinar quais .NET Framework atualizações estão instaladas](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="3b57c-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="3b57c-133">Encontrar versões mais recentes do .NET Framework (4.5 e posterior)</span><span class="sxs-lookup"><span data-stu-id="3b57c-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="3b57c-134">Você pode usar o editor do registro para localizar informações de versão no registro ou pode consultar o registro programaticamente.</span><span class="sxs-lookup"><span data-stu-id="3b57c-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="3b57c-135">Usar o editor do registro</span><span class="sxs-lookup"><span data-stu-id="3b57c-135">Use Registry Editor</span></span>

1. <span data-ttu-id="3b57c-136">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="3b57c-137">Você precisará ter credenciais administrativas para executar o REGEDIT.</span><span class="sxs-lookup"><span data-stu-id="3b57c-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="3b57c-138">No editor do registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="3b57c-139">Se a subchave **Full** não estiver presente, você não terá o .NET Framework 4.5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="3b57c-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3b57c-140">A pasta **NET Framework Setup** no Registro *não* começa com um ponto.</span><span class="sxs-lookup"><span data-stu-id="3b57c-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="3b57c-141">Verifique se há uma entrada DWORD chamada **Release**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="3b57c-142">Se ele existir, você terá .NET Framework 4,5 ou posterior instalado.</span><span class="sxs-lookup"><span data-stu-id="3b57c-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="3b57c-143">Seu valor é uma chave de versão que corresponde a uma versão específica do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b57c-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="3b57c-144">Na figura a seguir, por exemplo, o valor da entrada de **versão** é 378389, que é a chave de versão para .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="3b57c-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="3b57c-145">![Entrada de registro para o .NET Framework 4,5](./media/clr-installdir.png "Entrada de registro para o .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="3b57c-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="3b57c-146">A tabela a seguir lista o valor de **Release** DWORD em cada sistema operacional individual para o .NET Framework 4.5 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="3b57c-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="3b57c-147">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b57c-147">.NET Framework version</span></span>|<span data-ttu-id="3b57c-148">Valor da liberação de DWORD</span><span class="sxs-lookup"><span data-stu-id="3b57c-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="3b57c-149">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="3b57c-149">.NET Framework 4.5</span></span>|<span data-ttu-id="3b57c-150">Todos os sistemas operacionais Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="3b57c-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="3b57c-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="3b57c-152">No Windows 8.1 e no Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="3b57c-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="3b57c-153">Em todos os outros sistemas operacionais Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="3b57c-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="3b57c-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="3b57c-155">Todos os sistemas operacionais Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="3b57c-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="3b57c-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="3b57c-156">.NET Framework 4.6</span></span>|<span data-ttu-id="3b57c-157">No Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="3b57c-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="3b57c-158">Em todos os outros sistemas operacionais Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="3b57c-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="3b57c-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="3b57c-160">Em sistemas com a Atualização de novembro do Windows 10: 394254</span><span class="sxs-lookup"><span data-stu-id="3b57c-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="3b57c-161">Em todos os outros sistemas operacionais Windows (incluindo o Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="3b57c-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="3b57c-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="3b57c-163">Na Atualização de Aniversário do Windows 10 e Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="3b57c-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="3b57c-164">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="3b57c-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="3b57c-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3b57c-165">.NET Framework 4.7</span></span>|<span data-ttu-id="3b57c-166">No Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="3b57c-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="3b57c-167">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="3b57c-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="3b57c-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="3b57c-169">Na atualização dos criadores de outono do Windows 10 e do Windows Server, versão 1709:461308</span><span class="sxs-lookup"><span data-stu-id="3b57c-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="3b57c-170">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="3b57c-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="3b57c-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="3b57c-172">Na atualização do Windows 10 de abril de 2018 e Windows Server, versão 1803:461808</span><span class="sxs-lookup"><span data-stu-id="3b57c-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="3b57c-173">Em todos os sistemas operacionais Windows, exceto Windows 10 de abril de 2018 atualização e Windows Server, versão 1803:461814</span><span class="sxs-lookup"><span data-stu-id="3b57c-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="3b57c-174">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="3b57c-174">.NET Framework 4.8</span></span>|<span data-ttu-id="3b57c-175">No Windows 10 maio 2019 atualização e Windows 10 de novembro de 2019 atualização: 528040</span><span class="sxs-lookup"><span data-stu-id="3b57c-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="3b57c-176">Em todos os outros sistemas operacionais Windows (incluindo outros sistemas operacionais Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="3b57c-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="3b57c-177">Versão específica</span><span class="sxs-lookup"><span data-stu-id="3b57c-177">Specific version</span></span>

<span data-ttu-id="3b57c-178">Para determinar se uma versão *específica* do .NET Framework está instalada em uma versão específica do sistema operacional Windows, teste se o valor DWORD da **versão** é *igual ao* valor listado na tabela.</span><span class="sxs-lookup"><span data-stu-id="3b57c-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="3b57c-179">Por exemplo, para determinar se o .NET Framework 4.6 está presente em um sistema Windows 10, teste o valor de **Release** que é *igual a* 393295.</span><span class="sxs-lookup"><span data-stu-id="3b57c-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="3b57c-180">Versão mínima</span><span class="sxs-lookup"><span data-stu-id="3b57c-180">Minimum version</span></span>

<span data-ttu-id="3b57c-181">Para determinar se uma versão *mínima* do .NET Framework está presente, use o menor valor DWORD da **versão** para essa versão da tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="3b57c-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="3b57c-182">(Para sua conveniência, os valores mínimos também são listados na tabela a seguir.)</span><span class="sxs-lookup"><span data-stu-id="3b57c-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="3b57c-183">Por exemplo, se seu aplicativo for executado em .NET Framework 4,8 ou em uma versão posterior, teste um valor DWORD de versão *maior ou igual a* 528040.</span><span class="sxs-lookup"><span data-stu-id="3b57c-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="3b57c-184">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b57c-184">.NET Framework version</span></span>|<span data-ttu-id="3b57c-185">Valor mínimo da versão DWORD</span><span class="sxs-lookup"><span data-stu-id="3b57c-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="3b57c-186">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="3b57c-186">.NET Framework 4.5</span></span>|<span data-ttu-id="3b57c-187">378389</span><span class="sxs-lookup"><span data-stu-id="3b57c-187">378389</span></span>|
|<span data-ttu-id="3b57c-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="3b57c-189">378675</span><span class="sxs-lookup"><span data-stu-id="3b57c-189">378675</span></span>|
|<span data-ttu-id="3b57c-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="3b57c-191">379893</span><span class="sxs-lookup"><span data-stu-id="3b57c-191">379893</span></span>|
|<span data-ttu-id="3b57c-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="3b57c-192">.NET Framework 4.6</span></span>|<span data-ttu-id="3b57c-193">393295</span><span class="sxs-lookup"><span data-stu-id="3b57c-193">393295</span></span>|
|<span data-ttu-id="3b57c-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="3b57c-195">394254</span><span class="sxs-lookup"><span data-stu-id="3b57c-195">394254</span></span>|
|<span data-ttu-id="3b57c-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="3b57c-197">394802</span><span class="sxs-lookup"><span data-stu-id="3b57c-197">394802</span></span>|
|<span data-ttu-id="3b57c-198">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3b57c-198">.NET Framework 4.7</span></span>|<span data-ttu-id="3b57c-199">460798</span><span class="sxs-lookup"><span data-stu-id="3b57c-199">460798</span></span>|
|<span data-ttu-id="3b57c-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="3b57c-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="3b57c-201">461308</span><span class="sxs-lookup"><span data-stu-id="3b57c-201">461308</span></span>|
|<span data-ttu-id="3b57c-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="3b57c-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="3b57c-203">461808</span><span class="sxs-lookup"><span data-stu-id="3b57c-203">461808</span></span>|
|<span data-ttu-id="3b57c-204">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="3b57c-204">.NET Framework 4.8</span></span>|<span data-ttu-id="3b57c-205">528040</span><span class="sxs-lookup"><span data-stu-id="3b57c-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="3b57c-206">Várias versões</span><span class="sxs-lookup"><span data-stu-id="3b57c-206">Multiple versions</span></span>

<span data-ttu-id="3b57c-207">Para testar várias versões, comece testando um valor que seja *maior ou igual ao* menor valor de DWORD da versão mais recente do .NET Framework e compare o valor com o menor valor de DWORD para cada versão anterior.</span><span class="sxs-lookup"><span data-stu-id="3b57c-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="3b57c-208">Por exemplo, se seu aplicativo exigir o .NET Framework 4.7 ou posterior e você quiser determinar a versão específica atual do .NET Framework, comece testando um valor de **RELEASE** DWORD que seja *maior ou igual a* 461808 (o menor valor de DWORD para o .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="3b57c-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="3b57c-209">Em seguida, compare o valor de **RELEASE** DWORD com o menor valor para cada versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b57c-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="3b57c-210">Consultar o registro usando código</span><span class="sxs-lookup"><span data-stu-id="3b57c-210">Query the registry using code</span></span>

1. <span data-ttu-id="3b57c-211">Use os métodos <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> e <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="3b57c-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="3b57c-212">A existência da entrada DWORD **Release** na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** indica que o .NET Framework 4.5 ou posterior está instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="3b57c-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="3b57c-213">Verifique o valor da entrada **Release** para determinar a versão instalada.</span><span class="sxs-lookup"><span data-stu-id="3b57c-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="3b57c-214">Para compatibilidade com a versão atual, verifique se há um valor superior ou igual ao valor listado na [tabela de versões do .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="3b57c-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="3b57c-215">O seguinte exemplo verifica o valor da entrada **Release** no Registro para encontrar o .NET Framework 4.5 e versões posteriores que estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="3b57c-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="3b57c-216">Este exemplo segue a prática recomendada para a verificação de versão:</span><span class="sxs-lookup"><span data-stu-id="3b57c-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="3b57c-217">Ele verifica se o valor da entrada **Release** é *superior ou igual* ao valor das chaves de versão conhecidas.</span><span class="sxs-lookup"><span data-stu-id="3b57c-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="3b57c-218">Ele verifica na ordem da versão mais recente para a versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="3b57c-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="3b57c-219">Usar o PowerShell para verificar se há uma versão mínima exigida</span><span class="sxs-lookup"><span data-stu-id="3b57c-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="3b57c-220">Use comandos do PowerShell para verificar o valor da entrada **Release** da subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="3b57c-221">Os exemplos a seguir verificam o valor da entrada **Release** para determinar se o .NET Framework 4.6.2 ou posterior está instalado.</span><span class="sxs-lookup"><span data-stu-id="3b57c-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="3b57c-222">Esse código retornará `True` se ele estiver instalado; caso contrário, retornará `False`.</span><span class="sxs-lookup"><span data-stu-id="3b57c-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="3b57c-223">Para verificar se há uma versão de .NET Framework mínima necessária diferente, substitua `394802` no exemplo por um valor da [tabela de versão .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="3b57c-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="3b57c-224">Use o menor valor mostrado para essa versão.</span><span class="sxs-lookup"><span data-stu-id="3b57c-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="3b57c-225">Localizar versões mais antigas do .NET Framework (1 a 4)</span><span class="sxs-lookup"><span data-stu-id="3b57c-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="3b57c-226">Usar o editor do registro (versões mais antigas do Framework)</span><span class="sxs-lookup"><span data-stu-id="3b57c-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="3b57c-227">No menu **Iniciar**, escolha **Executar**, insira *regedit* e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="3b57c-228">Você precisará ter credenciais administrativas para executar o REGEDIT.</span><span class="sxs-lookup"><span data-stu-id="3b57c-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="3b57c-229">No editor do registro, abra a seguinte subchave: **HKEY_LOCAL_MACHINE \Software\microsoft\net Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="3b57c-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="3b57c-230">Para as versões 1.1 a 3.5 do .NET Framework, cada versão instalada é listada como uma subchave na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="3b57c-231">Por exemplo, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="3b57c-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="3b57c-232">O número de versão é armazenado como um valor na entrada **Version** da subchave da versão.</span><span class="sxs-lookup"><span data-stu-id="3b57c-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="3b57c-233">Para o .NET Framework 4, a entrada **Version** está localizada na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client**, na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** ou em ambas as subchaves.</span><span class="sxs-lookup"><span data-stu-id="3b57c-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3b57c-234">A pasta **NET Framework Setup** no Registro não começa com um ponto.</span><span class="sxs-lookup"><span data-stu-id="3b57c-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="3b57c-235">A figura a seguir mostra a subchave e sua entrada **Version** para o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="3b57c-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="3b57c-236">![A entrada do registro para o .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 e versões anteriores")</span><span class="sxs-lookup"><span data-stu-id="3b57c-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="3b57c-237">Consultar o registro usando código (versões mais antigas do Framework)</span><span class="sxs-lookup"><span data-stu-id="3b57c-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="3b57c-238">Use a classe <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> para acessar a subchave **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="3b57c-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="3b57c-239">O exemplo a seguir localiza as .NET Framework de 1 a 4 versões instaladas:</span><span class="sxs-lookup"><span data-stu-id="3b57c-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="3b57c-240">Encontrar versões do CLR</span><span class="sxs-lookup"><span data-stu-id="3b57c-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="3b57c-241">Usar CLRVer. exe</span><span class="sxs-lookup"><span data-stu-id="3b57c-241">Use Clrver.exe</span></span>

<span data-ttu-id="3b57c-242">Use a [ferramenta de Versão do CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) para determinar quais versões do CLR estão instaladas em um computador:</span><span class="sxs-lookup"><span data-stu-id="3b57c-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="3b57c-243">Em um [Prompt de Comando do Desenvolvedor para o Visual Studio](../tools/developer-command-prompt-for-vs.md), insira `clrver`.</span><span class="sxs-lookup"><span data-stu-id="3b57c-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="3b57c-244">Saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="3b57c-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="3b57c-245">Usar a classe de ambiente</span><span class="sxs-lookup"><span data-stu-id="3b57c-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b57c-246">Para o .NET Framework 4.5 e versões posteriores, não use a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para detectar a versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="3b57c-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="3b57c-247">Em vez disso, consulte o Registro, conforme descrito em [Encontrar versões 4.5 e posteriores do .NET Framework com o código](#net_d).</span><span class="sxs-lookup"><span data-stu-id="3b57c-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="3b57c-248">Consulte a propriedade <xref:System.Environment.Version?displayProperty=nameWithType> para recuperar um objeto <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="3b57c-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="3b57c-249">O objeto `System.Version` retornado identifica a versão do runtime que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="3b57c-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="3b57c-250">Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="3b57c-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="3b57c-251">Nas versões 4, 4.5, 4.5.1 e 4.5.2 do .NET Framework, a representação de cadeia de caracteres do objeto <xref:System.Version> retornado tem o formato 4.0.30319.*xxxxx*, em que *xxxxx* é menor que 42000.</span><span class="sxs-lookup"><span data-stu-id="3b57c-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="3b57c-252">Para o .NET Framework 4.6 e versões posteriores, ele tem o formato 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="3b57c-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="3b57c-253">Depois de ter o objeto `Version`, consulte-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3b57c-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="3b57c-254">Para o identificador de versão principal (por exemplo, *4* para a versão 4.0), use a propriedade <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b57c-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="3b57c-255">Para o identificador de versão secundária (por exemplo, *0* para a versão 4.0), use a propriedade <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b57c-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="3b57c-256">Para a cadeia de caracteres de versão inteira (por exemplo, *4.0.30319.18010*), use o método <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b57c-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3b57c-257">Esse método retorna um único valor que reflete a versão do runtime que está executando o código.</span><span class="sxs-lookup"><span data-stu-id="3b57c-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="3b57c-258">Ele não retorna versões de assembly nem outras versões do runtime que possam ter sido instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="3b57c-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="3b57c-259">O seguinte exemplo usa a propriedade <xref:System.Environment.Version%2A?displayProperty=nameWithType> para recuperar informações de versão do CLR:</span><span class="sxs-lookup"><span data-stu-id="3b57c-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="3b57c-260">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b57c-260">See also</span></span>

- [<span data-ttu-id="3b57c-261">Como determinar quais .NET Framework atualizações estão instaladas</span><span class="sxs-lookup"><span data-stu-id="3b57c-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="3b57c-262">Instalar o .NET Framework para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="3b57c-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="3b57c-263">Versões e dependências do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b57c-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
