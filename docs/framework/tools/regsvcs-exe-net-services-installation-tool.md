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
ms.openlocfilehash: 3c531a08e4555a8a076d81835bcceffa53e3ad7d
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894819"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="dd494-102">Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)</span><span class="sxs-lookup"><span data-stu-id="dd494-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="dd494-103">A ferramenta Instalação de Serviços .NET realiza as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="dd494-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="dd494-104">Carrega e registra um assembly.</span><span class="sxs-lookup"><span data-stu-id="dd494-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="dd494-105">Gera, registra e instala uma biblioteca de tipos em um aplicativo COM+ especificado.</span><span class="sxs-lookup"><span data-stu-id="dd494-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="dd494-106">Configura serviços adicionados programaticamente à classe.</span><span class="sxs-lookup"><span data-stu-id="dd494-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="dd494-107">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="dd494-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="dd494-108">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="dd494-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="dd494-109">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dd494-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd494-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd494-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="dd494-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd494-111">Parameters</span></span>  
  
|<span data-ttu-id="dd494-112">Argumento</span><span class="sxs-lookup"><span data-stu-id="dd494-112">Argument</span></span>|<span data-ttu-id="dd494-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd494-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="dd494-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="dd494-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="dd494-115">O arquivo do assembly de origem.</span><span class="sxs-lookup"><span data-stu-id="dd494-115">The source assembly file.</span></span> <span data-ttu-id="dd494-116">O assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="dd494-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="dd494-117">Para obter mais informações, consulte [Assinando um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dd494-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="dd494-118">Opção</span><span class="sxs-lookup"><span data-stu-id="dd494-118">Option</span></span>|<span data-ttu-id="dd494-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd494-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dd494-120">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="dd494-120">**/appdir:** *path*</span></span>|<span data-ttu-id="dd494-121">Especifica o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd494-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="dd494-122">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="dd494-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="dd494-123">Especifica o nome do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="dd494-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="dd494-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="dd494-124">**/c**</span></span>|<span data-ttu-id="dd494-125">Cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="dd494-125">Creates the target application.</span></span>|  
|<span data-ttu-id="dd494-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="dd494-126">**/componly**</span></span>|<span data-ttu-id="dd494-127">Configura apenas componentes; ignora métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="dd494-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="dd494-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="dd494-128">**/exapp**</span></span>|<span data-ttu-id="dd494-129">Especifica a ferramenta para aguardar um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="dd494-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="dd494-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="dd494-130">**/extlb**</span></span>|<span data-ttu-id="dd494-131">Usa uma biblioteca de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="dd494-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="dd494-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="dd494-132">**/fc**</span></span>|<span data-ttu-id="dd494-133">Encontra ou cria o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="dd494-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="dd494-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="dd494-134">**/help**</span></span>|<span data-ttu-id="dd494-135">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="dd494-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="dd494-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="dd494-136">**/noreconfig**</span></span>|<span data-ttu-id="dd494-137">Não reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="dd494-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="dd494-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="dd494-138">**/nologo**</span></span>|<span data-ttu-id="dd494-139">Suprime a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dd494-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="dd494-140">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="dd494-140">**/parname:** *name*</span></span>|<span data-ttu-id="dd494-141">Especifica o nome ou a ID do aplicativo COM+ a ser encontrado ou criado.</span><span class="sxs-lookup"><span data-stu-id="dd494-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="dd494-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="dd494-142">**/reconfig**</span></span>|<span data-ttu-id="dd494-143">Reconfigura um aplicativo de destino existente.</span><span class="sxs-lookup"><span data-stu-id="dd494-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="dd494-144">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dd494-144">This is the default.</span></span>|  
|<span data-ttu-id="dd494-145">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="dd494-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="dd494-146">Especifica a biblioteca de tipos a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="dd494-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="dd494-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="dd494-147">**/u**</span></span>|<span data-ttu-id="dd494-148">Desinstala o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="dd494-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="dd494-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="dd494-149">**/quiet**</span></span>|<span data-ttu-id="dd494-150">Especifica o modo silencioso; suprime o logotipo e a exibição da mensagem de êxito.</span><span class="sxs-lookup"><span data-stu-id="dd494-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="dd494-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="dd494-151">**/?**</span></span>|<span data-ttu-id="dd494-152">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="dd494-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd494-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd494-153">Remarks</span></span>  
 <span data-ttu-id="dd494-154">O Regsvcs.exe exige um arquivo do assembly de origem especificado por *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="dd494-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="dd494-155">Esse assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="dd494-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="dd494-156">Para obter mais informações sobre a assinatura de nome forte, consulte [Assinando um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dd494-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="dd494-157">Os nomes do aplicativo de destino e do arquivo da biblioteca de tipos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="dd494-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="dd494-158">O argumento *applicationName* pode ser gerado com base no arquivo do assembly de origem e será criado por Regsvcs.exe, se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="dd494-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="dd494-159">O argumento *typelibraryfile* pode especificar um nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="dd494-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="dd494-160">Se você não especificar um nome da biblioteca de tipos, Regsvcs.exe usará o nome do assembly como o padrão.</span><span class="sxs-lookup"><span data-stu-id="dd494-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="dd494-161">Quando Regsvcs.exe registra os métodos de um componente, ele está sujeito a [demandas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) e [demandas de link](../../../docs/framework/misc/link-demands.md) nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="dd494-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="dd494-162">Como a ferramenta é executada em um ambiente totalmente confiável, a maioria das demandas de uma permissão é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="dd494-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="dd494-163">No entanto, Regsvcs.exe não pode registrar componentes com métodos protegidos por uma demanda ou uma exigência de vínculo para <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="dd494-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="dd494-164">Você deve ter privilégios administrativos no computador local para usar Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="dd494-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="dd494-165">Se falhar durante a realização de alguma dessas ações, Regsvcs.exe exibirá mensagens de erro correspondentes.</span><span class="sxs-lookup"><span data-stu-id="dd494-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dd494-166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dd494-166">Examples</span></span>  
 <span data-ttu-id="dd494-167">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="dd494-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="dd494-168">O comando a seguir adiciona todas as classes públicas contidas em `myTest.dll` a `myTargetApp` (um aplicativo COM+ existente) e produz a biblioteca de tipos `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="dd494-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd494-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd494-169">See also</span></span>

- [<span data-ttu-id="dd494-170">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="dd494-170">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="dd494-171">Como: assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="dd494-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="dd494-172">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="dd494-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
