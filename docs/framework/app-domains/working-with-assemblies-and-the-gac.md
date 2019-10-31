---
title: Trabalhando com assemblies e o cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: 330555f907a5ee2ef9cfc11b0b5659a392c0dec7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119715"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="7bb91-102">Trabalhando com assemblies e o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="7bb91-102">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="7bb91-103">Se você pretender compartilhar um assembly com vários aplicativos, será necessário instalá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="7bb91-104">Cada computador em que o Common Language Runtime está instalado tem um cache de código em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="7bb91-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="7bb91-105">O cache de assembly global armazena assemblies projetados especificamente para serem compartilhados por vários aplicativos no computador.</span><span class="sxs-lookup"><span data-stu-id="7bb91-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="7bb91-106">Um assembly deve ter um nome forte para ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bb91-107">Assemblies colocados no cache de assembly global devem ter o mesmo nome de assembly e de arquivo (não incluindo a extensão de nome de arquivo).</span><span class="sxs-lookup"><span data-stu-id="7bb91-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="7bb91-108">Por exemplo, um assembly com o nome de myAssembly deve ter um nome de arquivo de myAssembly.exe ou myAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="7bb91-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="7bb91-109">Você deve compartilhar assemblies instalando-os no cache de assembly global somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="7bb91-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="7bb91-110">Como diretriz geral, mantenha as dependências de um assembly particulares e localize os assemblies no diretório de aplicativo, a menos que o compartilhamento de um assembly seja explicitamente obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7bb91-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="7bb91-111">Além disso, você não precisa instalar assemblies no cache de assembly global a fim de torná-los acessíveis para interoperabilidade COM ou código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7bb91-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="7bb91-112">Há diversas razões para instalar um assembly no cache de assembly global:</span><span class="sxs-lookup"><span data-stu-id="7bb91-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="7bb91-113">Local compartilhado.</span><span class="sxs-lookup"><span data-stu-id="7bb91-113">Shared location.</span></span>  
  
     <span data-ttu-id="7bb91-114">Assemblies que devem ser usados por aplicativos podem ser colocados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="7bb91-115">Por exemplo, se todos os aplicativos devem usar um assembly localizado no cache de assembly global, uma declaração de política de versão pode adicionada ao arquivo Machine.config que redireciona referências para o assembly.</span><span class="sxs-lookup"><span data-stu-id="7bb91-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="7bb91-116">Segurança do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7bb91-116">File security.</span></span>  
  
     <span data-ttu-id="7bb91-117">Os administradores geralmente protegem o diretório systemroot usando uma ACL (Lista de Controle de Acesso) para controlar os acesso de gravação e de execução.</span><span class="sxs-lookup"><span data-stu-id="7bb91-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="7bb91-118">Como o cache de assembly global é instalado em um diretório do systemroot, ele herda a ACL desse diretório.</span><span class="sxs-lookup"><span data-stu-id="7bb91-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="7bb91-119">É recomendável que apenas usuários com privilégios Administrador tenham permissão para excluir arquivos do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="7bb91-120">Controle de versão lado a lado.</span><span class="sxs-lookup"><span data-stu-id="7bb91-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="7bb91-121">Várias cópias de assemblies com o mesmo nome, mas com informações diferentes de versão, podem ser mantidas no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="7bb91-122">Local adicional de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="7bb91-122">Additional search location.</span></span>  
  
     <span data-ttu-id="7bb91-123">O Common Language Runtime verifica o cache de assembly global para um assembly que corresponde à solicitação de assembly antes de investigar ou usar as informações da base de código em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7bb91-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="7bb91-124">Observe que há situações em que explicitamente não é recomendado instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="7bb91-125">Se colocar um dos assemblies que compõem um aplicativo no cache de assembly global, você não poderá mais replicar nem instalar o aplicativo usando XCOPY para copiar o diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7bb91-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="7bb91-126">Nesse caso, você também deve mover o assembly para o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bb91-127">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7bb91-127">In This Section</span></span>  
[<span data-ttu-id="7bb91-128">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="7bb91-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="7bb91-129">Descreve as maneiras de instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="7bb91-130">Como exibir o conteúdo do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="7bb91-130">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="7bb91-131">Explica como usar a [Gacutil.exe (Ferramenta de Cache de Assembly Global)](../tools/gacutil-exe-gac-tool.md) para exibir o conteúdo do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="7bb91-132">Como remover um assembly do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="7bb91-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="7bb91-133">Explica como usar a [Gacutil.exe (Ferramenta de Cache de Assembly Global)](../tools/gacutil-exe-gac-tool.md) para remover um assembly do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="7bb91-134">Uso de componentes atendidos com o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="7bb91-134">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="7bb91-135">Explica por que componentes de atendidos (componentes COM+ gerenciados) devem ser colocados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7bb91-136">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7bb91-136">Related Sections</span></span>  

[<span data-ttu-id="7bb91-137">Criação de assemblies</span><span class="sxs-lookup"><span data-stu-id="7bb91-137">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="7bb91-138">Apresenta uma visão geral da criação de assemblies.</span><span class="sxs-lookup"><span data-stu-id="7bb91-138">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="7bb91-139">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="7bb91-139">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="7bb91-140">Descreve o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7bb91-140">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="7bb91-141">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="7bb91-141">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="7bb91-142">Explica como usar o [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um assembly.</span><span class="sxs-lookup"><span data-stu-id="7bb91-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="7bb91-143">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="7bb91-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="7bb91-144">Descreve como o Common Language Runtime localiza e carrega os assemblies que compõem seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7bb91-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="7bb91-145">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="7bb91-145">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="7bb91-146">Descreve assemblies, os blocos de construção de aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="7bb91-146">Describes assemblies, the building blocks of managed applications.</span></span>
