---
title: Como instalar um assembly no cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23a1d8c638b198c31d7c83aaf3f216b465f01453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="122ec-102">Como instalar um assembly no cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="122ec-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="122ec-103">Há duas maneiras de instalar um assembly com nome forte no GAC (Cache de Assembly Global):</span><span class="sxs-lookup"><span data-stu-id="122ec-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="122ec-104">Apenas os assemblies com nome forte podem ser instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="122ec-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="122ec-105">Para obter informações sobre como criar um assembly de nome forte, consulte [Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="122ec-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="122ec-106">Usando o [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="122ec-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="122ec-107">Você faz isso no Visual Studio 2012 e no Visual Studio 2013 ao criar um projeto do InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="122ec-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="122ec-108">Essa é a maneira recomendada e mais comum de adicionar assemblies no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="122ec-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="122ec-109">O instalador fornece uma contagem de referência de assemblies no Cache de Assembly Global, além de outros benefícios.</span><span class="sxs-lookup"><span data-stu-id="122ec-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="122ec-110">Usando a [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="122ec-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="122ec-111">Você pode usar o Gacutil.exe para adicionar assemblies com nome forte ao Cache de Assembly Global e para exibir o conteúdo desse cache.</span><span class="sxs-lookup"><span data-stu-id="122ec-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="122ec-112">Gacutil.exe destina-se a fins de desenvolvimento e não deve ser usado para instalar assemblies de produção no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="122ec-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="122ec-113">Nas versões anteriores do .NET Framework, a extensão do shell do Windows Shfusion.dll permitia instalar assemblies arrastando-os no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="122ec-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="122ec-114">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.</span><span class="sxs-lookup"><span data-stu-id="122ec-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="122ec-115">Para usar a ferramenta Cache de Assembly Global (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="122ec-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="122ec-116">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="122ec-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="122ec-117">**gacutil -i** \<*nome do assembly*></span><span class="sxs-lookup"><span data-stu-id="122ec-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="122ec-118">Neste comando, *nome do assembly* é o nome do assembly a ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="122ec-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="122ec-119">O exemplo a seguir instala um assembly com nome de arquivo `hello.dll` no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="122ec-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="122ec-120">Para obter mais informações, consulte [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="122ec-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="122ec-121">Para usar um projeto do InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="122ec-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="122ec-122">Adicione um pacote de instalação e implantação à sua solução ao abrir o menu de atalho para a solução e, em seguida, escolha **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="122ec-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="122ec-123">Na caixa de diálogo **Adicionar Novo Projeto**, na pasta **Instalado**, escolha **Outros Tipos de Projeto**, **Instalação e Implantação**, **InstallShield Limited Edition** e atribua um nome ao projeto.</span><span class="sxs-lookup"><span data-stu-id="122ec-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="122ec-124">(Se solicitado, baixe, instale e ative o InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="122ec-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="122ec-125">Faça a configuração geral do seu projeto de instalação e implantação usando o Assistente de Projeto no **Gerenciador de Soluções** ou escolhendo as subetapas das etapas numeradas no **Gerenciador de Soluções**. Configure sua instalação como faria se não estivesse adicionando assemblies ao GAC.</span><span class="sxs-lookup"><span data-stu-id="122ec-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="122ec-126">Para iniciar o processo de adicionar um assembly ao GAC, escolha **Arquivos**, sob a etapa **Especificar Dados do Aplicativo** no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="122ec-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="122ec-127">No painel **Pastas do computador de destino**, abra o menu de atalho para **Computador de Destino** e escolha **Mostrar Pasta Predefinida**, **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="122ec-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="122ec-128">Para cada projeto na solução que contém um assembly que você deseja instalar no Cache de assembly Global:</span><span class="sxs-lookup"><span data-stu-id="122ec-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="122ec-129">No painel **Pastas do computador de origem**, escolha o projeto.</span><span class="sxs-lookup"><span data-stu-id="122ec-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="122ec-130">No painel **Pastas do computador de destino**, escolha **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="122ec-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="122ec-131">No painel **Arquivos do computador de origem**, escolha **Saída primária de** *<project_name>*.</span><span class="sxs-lookup"><span data-stu-id="122ec-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="122ec-132">Arraste o arquivo na etapa c para o painel **Arquivos do computador de destino** (ou use os comandos **Copiar** e **Colar** no menu de atalho de arquivo).</span><span class="sxs-lookup"><span data-stu-id="122ec-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122ec-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="122ec-133">See Also</span></span>  
 [<span data-ttu-id="122ec-134">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="122ec-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="122ec-135">Como remover um assembly do cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="122ec-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="122ec-136">Gacutil.exe (Ferramenta Cache de Assembly Global)</span><span class="sxs-lookup"><span data-stu-id="122ec-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="122ec-137">Como assinar um assembly com um nome forte</span><span class="sxs-lookup"><span data-stu-id="122ec-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="122ec-138">implantação do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="122ec-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
