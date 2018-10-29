---
title: Como remover um assembly do cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18148d21c6329167437cd1ca3ea1f4635c7a28a0
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452528"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="8a02a-102">Como remover um assembly do cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="8a02a-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="8a02a-103">Há duas maneiras de remover um assembly do GAC (cache de assemblies global):</span><span class="sxs-lookup"><span data-stu-id="8a02a-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="8a02a-104">Usando a [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8a02a-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="8a02a-105">Use essa opção para desinstalar assemblies que você colocou no GAC durante o desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="8a02a-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="8a02a-106">Usando o [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="8a02a-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="8a02a-107">Use essa opção para desinstalar assemblies ao testar pacotes de instalação e para sistemas de produção.</span><span class="sxs-lookup"><span data-stu-id="8a02a-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="8a02a-108">Remover um assembly com o Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="8a02a-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="8a02a-109">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="8a02a-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="8a02a-110">**gacutil –u** \<*nome do assembly*></span><span class="sxs-lookup"><span data-stu-id="8a02a-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="8a02a-111">Neste comando, *nome do assembly* é o nome do assembly a ser removido do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8a02a-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="8a02a-112">Não use Gacutil.exe para remover assemblies em sistemas de produção devido à possibilidade de que o assembly ainda possa ser necessário para algum aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a02a-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="8a02a-113">Em vez disso, use o Windows Installer, que mantém uma contagem de referência para cada assembly que ele instala no GAC.</span><span class="sxs-lookup"><span data-stu-id="8a02a-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="8a02a-114">O exemplo a seguir remove um assembly chamado `hello.dll` do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8a02a-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="8a02a-115">Remover um assembly com o Windows Installer</span><span class="sxs-lookup"><span data-stu-id="8a02a-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="8a02a-116">No aplicativo **Programas e Recursos**, em **Painel de Controle**, selecione o aplicativo que você deseja desinstalar.</span><span class="sxs-lookup"><span data-stu-id="8a02a-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="8a02a-117">Se o pacote de instalação tiver colocado assemblies no GAC, o Windows Installer os removerá se não forem usados por outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a02a-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a02a-118">O Windows Installer mantém uma contagem de referência para os assemblies instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="8a02a-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="8a02a-119">Um assembly será removido do GAC apenas quando sua contagem de referência atingir zero, o que indica que ele não é usado por qualquer aplicativo instalado por um pacote do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="8a02a-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a02a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a02a-120">See Also</span></span>  
- [<span data-ttu-id="8a02a-121">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8a02a-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [<span data-ttu-id="8a02a-122">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="8a02a-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
- [<span data-ttu-id="8a02a-123">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="8a02a-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
