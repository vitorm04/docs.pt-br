---
title: Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b529ccd8c5e0cf0563adf556a7d316372ac4d0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215034"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="3566c-102">Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)</span><span class="sxs-lookup"><span data-stu-id="3566c-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="3566c-103">A ferramenta Instalação de Serviços .NET realiza as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="3566c-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="3566c-104">Carrega e registra um assembly.</span><span class="sxs-lookup"><span data-stu-id="3566c-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="3566c-105">Gera, registra e instala uma biblioteca de tipos em um aplicativo COM+ especificado.</span><span class="sxs-lookup"><span data-stu-id="3566c-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="3566c-106">Configura serviços adicionados programaticamente à classe.</span><span class="sxs-lookup"><span data-stu-id="3566c-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="3566c-107">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="3566c-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="3566c-108">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3566c-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="3566c-109">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3566c-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3566c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3566c-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="3566c-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3566c-111">Parameters</span></span>  
  
|<span data-ttu-id="3566c-112">Argumento</span><span class="sxs-lookup"><span data-stu-id="3566c-112">Argument</span></span>|<span data-ttu-id="3566c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3566c-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3566c-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="3566c-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="3566c-115">O arquivo do assembly de origem.</span><span class="sxs-lookup"><span data-stu-id="3566c-115">The source assembly file.</span></span> <span data-ttu-id="3566c-116">O assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="3566c-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="3566c-117">Para obter mais informações, consulte [Assinando um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="3566c-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="3566c-118">Opção</span><span class="sxs-lookup"><span data-stu-id="3566c-118">Option</span></span>|<span data-ttu-id="3566c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3566c-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3566c-120">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="3566c-120">**/appdir:** *path*</span></span>|<span data-ttu-id="3566c-121">Especifica o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3566c-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="3566c-122">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="3566c-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="3566c-123">Especifica o nome do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="3566c-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="3566c-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="3566c-124">**/c**</span></span>|<span data-ttu-id="3566c-125">Cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="3566c-125">Creates the target application.</span></span>|  
|<span data-ttu-id="3566c-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="3566c-126">**/componly**</span></span>|<span data-ttu-id="3566c-127">Configura apenas componentes; ignora métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="3566c-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="3566c-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="3566c-128">**/exapp**</span></span>|<span data-ttu-id="3566c-129">Especifica a ferramenta para aguardar um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="3566c-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="3566c-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="3566c-130">**/extlb**</span></span>|<span data-ttu-id="3566c-131">Usa uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="3566c-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="3566c-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="3566c-132">**/fc**</span></span>|<span data-ttu-id="3566c-133">Encontra ou cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="3566c-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="3566c-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="3566c-134">**/help**</span></span>|<span data-ttu-id="3566c-135">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3566c-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="3566c-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="3566c-136">**/noreconfig**</span></span>|<span data-ttu-id="3566c-137">Não reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="3566c-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="3566c-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="3566c-138">**/nologo**</span></span>|<span data-ttu-id="3566c-139">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3566c-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="3566c-140">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="3566c-140">**/parname:** *name*</span></span>|<span data-ttu-id="3566c-141">Especifica o nome ou a ID do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="3566c-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="3566c-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="3566c-142">**/reconfig**</span></span>|<span data-ttu-id="3566c-143">Reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="3566c-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="3566c-144">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3566c-144">This is the default.</span></span>|  
|<span data-ttu-id="3566c-145">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="3566c-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="3566c-146">Especifica a biblioteca de tipos a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="3566c-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="3566c-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="3566c-147">**/u**</span></span>|<span data-ttu-id="3566c-148">Desinstala o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="3566c-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="3566c-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="3566c-149">**/quiet**</span></span>|<span data-ttu-id="3566c-150">Especifica o modo silencioso; suprime o logotipo e a exibição da mensagem de êxito.</span><span class="sxs-lookup"><span data-stu-id="3566c-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="3566c-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="3566c-151">**/?**</span></span>|<span data-ttu-id="3566c-152">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3566c-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3566c-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="3566c-153">Remarks</span></span>  
 <span data-ttu-id="3566c-154">O Regsvcs.exe exige um arquivo do assembly de origem especificado por *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="3566c-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="3566c-155">Esse assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="3566c-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="3566c-156">Para obter mais informações sobre a assinatura de nome forte, consulte [Assinando um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="3566c-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="3566c-157">Os nomes do aplicativo de destino e do arquivo da biblioteca de tipos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="3566c-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="3566c-158">O argumento *applicationName* pode ser gerado com base no arquivo do assembly de origem e será criado por Regsvcs.exe, se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="3566c-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="3566c-159">O argumento *typelibraryfile* pode especificar um nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="3566c-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="3566c-160">Se você não especificar um nome da biblioteca de tipos, Regsvcs.exe usará o nome do assembly como o padrão.</span><span class="sxs-lookup"><span data-stu-id="3566c-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="3566c-161">Quando Regsvcs.exe registra os métodos de um componente, ele está sujeito a [demandas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) e [demandas de link](../../../docs/framework/misc/link-demands.md) nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="3566c-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="3566c-162">Como a ferramenta é executada em um ambiente totalmente confiável, a maioria das demandas de uma permissão é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3566c-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="3566c-163">No entanto, Regsvcs.exe não pode registrar componentes com métodos protegidos por uma demanda ou uma exigência de vínculo para <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="3566c-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="3566c-164">Você deve ter privilégios administrativos no computador local para usar Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="3566c-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="3566c-165">Se falhar durante a realização de alguma dessas ações, Regsvcs.exe exibirá mensagens de erro correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3566c-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3566c-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3566c-166">Examples</span></span>  
 <span data-ttu-id="3566c-167">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="3566c-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="3566c-168">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="3566c-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="3566c-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3566c-169">See also</span></span>

- [<span data-ttu-id="3566c-170">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="3566c-170">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="3566c-171">Como: assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="3566c-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="3566c-172">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="3566c-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
