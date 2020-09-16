---
title: Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)
description: Use Regsvcs.exe, a ferramenta de instalação de serviços .NET. Carregue e registre um assembly, configure os serviços que você adicionou programaticamente a uma classe e muito mais.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 474018b8bc39e4d5c36bd4bc6481072b218d6270
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558388"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="02413-104">Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)</span><span class="sxs-lookup"><span data-stu-id="02413-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="02413-105">A ferramenta Instalação de Serviços .NET realiza as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="02413-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="02413-106">Carrega e registra um assembly.</span><span class="sxs-lookup"><span data-stu-id="02413-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="02413-107">Gera, registra e instala uma biblioteca de tipos em um aplicativo COM+ especificado.</span><span class="sxs-lookup"><span data-stu-id="02413-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="02413-108">Configura serviços adicionados programaticamente à classe.</span><span class="sxs-lookup"><span data-stu-id="02413-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="02413-109">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="02413-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="02413-110">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="02413-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="02413-111">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="02413-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02413-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02413-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="02413-113">parâmetros</span><span class="sxs-lookup"><span data-stu-id="02413-113">Parameters</span></span>  
  
|<span data-ttu-id="02413-114">Argumento</span><span class="sxs-lookup"><span data-stu-id="02413-114">Argument</span></span>|<span data-ttu-id="02413-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="02413-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="02413-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="02413-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="02413-117">O arquivo do assembly de origem.</span><span class="sxs-lookup"><span data-stu-id="02413-117">The source assembly file.</span></span> <span data-ttu-id="02413-118">O assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="02413-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="02413-119">Para obter mais informações, consulte [Assinando um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="02413-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="02413-120">Opção</span><span class="sxs-lookup"><span data-stu-id="02413-120">Option</span></span>|<span data-ttu-id="02413-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="02413-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="02413-122">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="02413-122">**/appdir:** *path*</span></span>|<span data-ttu-id="02413-123">Especifica o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02413-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="02413-124">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="02413-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="02413-125">Especifica o nome do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="02413-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="02413-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="02413-126">**/c**</span></span>|<span data-ttu-id="02413-127">Cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="02413-127">Creates the target application.</span></span>|  
|<span data-ttu-id="02413-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="02413-128">**/componly**</span></span>|<span data-ttu-id="02413-129">Configura apenas componentes; ignora métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="02413-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="02413-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="02413-130">**/exapp**</span></span>|<span data-ttu-id="02413-131">Especifica a ferramenta para aguardar um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="02413-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="02413-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="02413-132">**/extlb**</span></span>|<span data-ttu-id="02413-133">Usa uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="02413-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="02413-134">**/FC**</span><span class="sxs-lookup"><span data-stu-id="02413-134">**/fc**</span></span>|<span data-ttu-id="02413-135">Encontra ou cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="02413-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="02413-136">**/Help**</span><span class="sxs-lookup"><span data-stu-id="02413-136">**/help**</span></span>|<span data-ttu-id="02413-137">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="02413-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="02413-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="02413-138">**/noreconfig**</span></span>|<span data-ttu-id="02413-139">Não reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="02413-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="02413-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="02413-140">**/nologo**</span></span>|<span data-ttu-id="02413-141">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02413-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="02413-142">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="02413-142">**/parname:** *name*</span></span>|<span data-ttu-id="02413-143">Especifica o nome ou a ID do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="02413-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="02413-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="02413-144">**/reconfig**</span></span>|<span data-ttu-id="02413-145">Reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="02413-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="02413-146">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="02413-146">This is the default.</span></span>|  
|<span data-ttu-id="02413-147">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="02413-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="02413-148">Especifica a biblioteca de tipos a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="02413-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="02413-149">**/u**</span><span class="sxs-lookup"><span data-stu-id="02413-149">**/u**</span></span>|<span data-ttu-id="02413-150">Desinstala o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="02413-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="02413-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="02413-151">**/quiet**</span></span>|<span data-ttu-id="02413-152">Especifica o modo silencioso; suprime o logotipo e a exibição da mensagem de êxito.</span><span class="sxs-lookup"><span data-stu-id="02413-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="02413-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="02413-153">**/?**</span></span>|<span data-ttu-id="02413-154">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="02413-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02413-155">Comentários</span><span class="sxs-lookup"><span data-stu-id="02413-155">Remarks</span></span>  
 <span data-ttu-id="02413-156">O Regsvcs.exe exige um arquivo do assembly de origem especificado por *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="02413-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="02413-157">Esse assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="02413-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="02413-158">Para obter mais informações sobre a assinatura de nome forte, consulte [Assinando um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="02413-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="02413-159">Os nomes do aplicativo de destino e do arquivo da biblioteca de tipos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="02413-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="02413-160">O argumento *applicationName* pode ser gerado com base no arquivo do assembly de origem e será criado por Regsvcs.exe, se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="02413-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="02413-161">O argumento *typelibraryfile* pode especificar um nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02413-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="02413-162">Se você não especificar um nome da biblioteca de tipos, Regsvcs.exe usará o nome do assembly como o padrão.</span><span class="sxs-lookup"><span data-stu-id="02413-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="02413-163">Quando Regsvcs.exe registra os métodos de um componente, ele está sujeito a [demandas](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) e [demandas de link](../misc/link-demands.md) nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="02413-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="02413-164">Como a ferramenta é executada em um ambiente totalmente confiável, a maioria das demandas de uma permissão é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="02413-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="02413-165">No entanto, Regsvcs.exe não pode registrar componentes com métodos protegidos por uma demanda ou uma exigência de vínculo para <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="02413-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="02413-166">Você deve ter privilégios administrativos no computador local para usar Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="02413-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="02413-167">Se falhar durante a realização de alguma dessas ações, Regsvcs.exe exibirá mensagens de erro correspondentes.</span><span class="sxs-lookup"><span data-stu-id="02413-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="02413-168">Exemplos</span><span class="sxs-lookup"><span data-stu-id="02413-168">Examples</span></span>  
 <span data-ttu-id="02413-169">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="02413-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="02413-170">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="02413-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="02413-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="02413-171">See also</span></span>

- [<span data-ttu-id="02413-172">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="02413-172">Tools</span></span>](index.md)
- [<span data-ttu-id="02413-173">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="02413-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="02413-174">Prompts de comando</span><span class="sxs-lookup"><span data-stu-id="02413-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
