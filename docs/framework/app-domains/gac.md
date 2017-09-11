---
title: Cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bad9e339896b0d62dce75a4044b18f3ae6a69332
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="global-assembly-cache"></a><span data-ttu-id="fbc57-102">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="fbc57-102">Global Assembly Cache</span></span>
<span data-ttu-id="fbc57-103">Cada computador onde o Common Language Runtime está instalado tem um cache de código da máquina chamado cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-103">Each computer where the common language runtime is installed has a machine-wide code cache called the global assembly cache.</span></span> <span data-ttu-id="fbc57-104">O cache de assembly global armazena assemblies projetados especificamente para serem compartilhados por vários aplicativos no computador.</span><span class="sxs-lookup"><span data-stu-id="fbc57-104">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="fbc57-105">Você deve compartilhar assemblies instalando-os no cache de assembly global somente quando precisar.</span><span class="sxs-lookup"><span data-stu-id="fbc57-105">You should share assemblies by installing them into the global assembly cache only when you need to.</span></span> <span data-ttu-id="fbc57-106">Como diretriz geral, mantenha as dependências de um assembly privadas e localize os assemblies no diretório de aplicativo, a menos que o compartilhamento de um assembly seja explicitamente obrigatório.</span><span class="sxs-lookup"><span data-stu-id="fbc57-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="fbc57-107">Além disso, não é necessário instalar assemblies no cache de assembly global a fim de torná-los acessíveis para interoperabilidade COM ou código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fbc57-107">In addition, it is not necessary to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbc57-108">Há situações em que você explicitamente não deseja instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-108">There are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="fbc57-109">Se colocar um dos assemblies que compõem um aplicativo no cache de assembly global, você não poderá mais replicar nem instalar o aplicativo usando o comando **xcopy** para copiar o diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbc57-109">If you place one of the assemblies that make up an application in the global assembly cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="fbc57-110">Você também deve mover o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-110">You must move the assembly in the global assembly cache as well.</span></span>  
  
 <span data-ttu-id="fbc57-111">Há duas maneiras de implantar um assembly no cache de assembly global:</span><span class="sxs-lookup"><span data-stu-id="fbc57-111">There are two ways to deploy an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="fbc57-112">Use um instalador projetado para funcionar com o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-112">Use an installer designed to work with the global assembly cache.</span></span> <span data-ttu-id="fbc57-113">Essa é a opção preferencial para instalar assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-113">This is the preferred option for installing assemblies into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="fbc57-114">Use uma ferramenta de desenvolvedor chamada [Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), fornecida pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbc57-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fbc57-115">Em cenários de implantação, use o Windows Installer para instalar assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-115">In deployment scenarios, use Windows Installer to install assemblies into the global assembly cache.</span></span> <span data-ttu-id="fbc57-116">Só use a ferramenta Global Assembly Cache em cenários de desenvolvimento, porque ela não fornece contagem de referência de assembly e outros recursos fornecidos durante o uso do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="fbc57-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="fbc57-117">A partir do .NET Framework 4, o local padrão do cache de assembly global é **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="fbc57-117">Starting with the .NET Framework 4, the default location for the global assembly cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="fbc57-118">Em versões anteriores do .NET Framework, o local padrão era **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="fbc57-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="fbc57-119">Os administradores geralmente protegem o diretório systemroot usando uma ACL (lista de controle de acesso) para controlar acesso de escrita e execução.</span><span class="sxs-lookup"><span data-stu-id="fbc57-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="fbc57-120">Como o cache de assembly global é instalado em um subdiretório do diretório systemroot, ele herda a ACL desse diretório.</span><span class="sxs-lookup"><span data-stu-id="fbc57-120">Because the global assembly cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="fbc57-121">É recomendável que apenas usuários com privilégios Administrador tenham permissão para excluir arquivos do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fbc57-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
 <span data-ttu-id="fbc57-122">Assemblies implantados no cache de assembly global devem ter um nome forte.</span><span class="sxs-lookup"><span data-stu-id="fbc57-122">Assemblies deployed in the global assembly cache must have a strong name.</span></span> <span data-ttu-id="fbc57-123">Quando um assembly é adicionado ao cache de assembly global, são executadas verificações de integridade em todos os arquivos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="fbc57-123">When an assembly is added to the global assembly cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="fbc57-124">O cache executa essas verificações de integridade para garantir que um assembly não tenha sido adulterado, por exemplo, quando um arquivo é alterado, mas o manifesto não reflete a alteração.</span><span class="sxs-lookup"><span data-stu-id="fbc57-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc57-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbc57-125">See Also</span></span>  
 <span data-ttu-id="fbc57-126">[Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="fbc57-126">[Assemblies in the Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) </span></span>  
 <span data-ttu-id="fbc57-127">[Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="fbc57-127">[Working with Assemblies and the Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 [<span data-ttu-id="fbc57-128">Assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="fbc57-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)

