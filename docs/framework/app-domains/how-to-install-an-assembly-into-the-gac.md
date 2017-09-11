---
title: Como instalar um assembly no cache de assemblies global
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
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: 24
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c1a0eb5034c10b84b02f493cd21bccd121c8315c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="ecf38-102">Como instalar um assembly no cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="ecf38-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="ecf38-103">Há duas maneiras de instalar um assembly com nome forte no GAC (Cache de Assembly Global):</span><span class="sxs-lookup"><span data-stu-id="ecf38-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecf38-104">Apenas os assemblies com nome forte podem ser instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="ecf38-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="ecf38-105">Para obter informações sobre como criar um assembly de nome forte, consulte [Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="ecf38-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="ecf38-106">Usando o [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="ecf38-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="ecf38-107">Você faz isso no Visual Studio 2012 e no Visual Studio 2013 ao criar um projeto do InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="ecf38-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="ecf38-108">Essa é a maneira recomendada e mais comum de adicionar assemblies no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="ecf38-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="ecf38-109">O instalador fornece uma contagem de referência de assemblies no Cache de Assembly Global, além de outros benefícios.</span><span class="sxs-lookup"><span data-stu-id="ecf38-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="ecf38-110">Usando a [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ecf38-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="ecf38-111">Você pode usar o Gacutil.exe para adicionar assemblies com nome forte ao Cache de Assembly Global e para exibir o conteúdo desse cache.</span><span class="sxs-lookup"><span data-stu-id="ecf38-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecf38-112">Gacutil.exe destina-se a fins de desenvolvimento e não deve ser usado para instalar assemblies de produção no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="ecf38-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecf38-113">Nas versões anteriores do .NET Framework, a extensão do shell do Windows Shfusion.dll permitia instalar assemblies arrastando-os no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="ecf38-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="ecf38-114">A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ecf38-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="ecf38-115">Para usar a ferramenta Cache de Assembly Global (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ecf38-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="ecf38-116">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ecf38-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="ecf38-117">**gacutil -i** \<*nome do assembly*></span><span class="sxs-lookup"><span data-stu-id="ecf38-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="ecf38-118">Neste comando, *nome do assembly* é o nome do assembly a ser instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="ecf38-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="ecf38-119">O exemplo a seguir instala um assembly com nome de arquivo `hello.dll` no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="ecf38-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="ecf38-120">Para obter mais informações, consulte [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ecf38-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="ecf38-121">Para usar um projeto do InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="ecf38-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="ecf38-122">Adicione um pacote de instalação e implantação à sua solução ao abrir o menu de atalho para a solução e, em seguida, escolha **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ecf38-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="ecf38-123">Na caixa de diálogo **Adicionar Novo Projeto**, na pasta **Instalado**, escolha **Outros Tipos de Projeto**, **Instalação e Implantação**, **InstallShield Limited Edition** e atribua um nome ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ecf38-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="ecf38-124">(Se solicitado, baixe, instale e ative o InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="ecf38-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="ecf38-125">Faça a configuração geral do seu projeto de instalação e implantação usando o Assistente de Projeto no **Gerenciador de Soluções** ou escolhendo as subetapas das etapas numeradas no **Gerenciador de Soluções**. Configure sua instalação como faria se não estivesse adicionando assemblies ao GAC.</span><span class="sxs-lookup"><span data-stu-id="ecf38-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="ecf38-126">Para iniciar o processo de adicionar um assembly ao GAC, escolha **Arquivos**, sob a etapa **Especificar Dados do Aplicativo** no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="ecf38-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="ecf38-127">No painel **Pastas do computador de destino**, abra o menu de atalho para **Computador de Destino** e escolha **Mostrar Pasta Predefinida**, **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="ecf38-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="ecf38-128">Para cada projeto na solução que contém um assembly que você deseja instalar no Cache de assembly Global:</span><span class="sxs-lookup"><span data-stu-id="ecf38-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="ecf38-129">No painel **Pastas do computador de origem**, escolha o projeto.</span><span class="sxs-lookup"><span data-stu-id="ecf38-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="ecf38-130">No painel **Pastas do computador de destino**, escolha **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="ecf38-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="ecf38-131">No painel **Arquivos do computador de origem**, escolha **Saída primária de** *<project_name>*.</span><span class="sxs-lookup"><span data-stu-id="ecf38-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="ecf38-132">Arraste o arquivo na etapa c para o painel **Arquivos do computador de destino** (ou use os comandos **Copiar** e **Colar** no menu de atalho de arquivo).</span><span class="sxs-lookup"><span data-stu-id="ecf38-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf38-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecf38-133">See Also</span></span>  
 <span data-ttu-id="ecf38-134">[Trabalhando com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="ecf38-134">[Working with Assemblies and the Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 <span data-ttu-id="ecf38-135">[Como remover um assembly do cache de assembly global](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="ecf38-135">[How to: Remove an Assembly from the Global Assembly Cache](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md) </span></span>  
 <span data-ttu-id="ecf38-136">[Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) </span><span class="sxs-lookup"><span data-stu-id="ecf38-136">[Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) </span></span>  
 <span data-ttu-id="ecf38-137">[Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) </span><span class="sxs-lookup"><span data-stu-id="ecf38-137">[How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) </span></span>  
 [<span data-ttu-id="ecf38-138">implantação do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="ecf38-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)

