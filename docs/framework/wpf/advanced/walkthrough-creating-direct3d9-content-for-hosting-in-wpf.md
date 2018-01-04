---
title: "Instruções passo a passo: criando conteúdo Direct3D9 para hospedar no WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1a5d70807541a0a3faf6bc99a3ced42827efd72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="a98af-102">Instruções passo a passo: criando conteúdo Direct3D9 para hospedar no WPF</span><span class="sxs-lookup"><span data-stu-id="a98af-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="a98af-103">Esta instrução passo a passo mostra como criar conteúdo Direct3D9 adequado para hospedagem em um aplicativo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a98af-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="a98af-104">Para obter mais informações sobre hospedagem de conteúdo Direct3D9 em aplicativos WPF, consulte [Interoperação Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="a98af-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>  
  
 <span data-ttu-id="a98af-105">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="a98af-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="a98af-106">Criar um projeto Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="a98af-106">Create a Direct3D9 project.</span></span>  
  
-   <span data-ttu-id="a98af-107">Configurar o projeto Direct3D9 para hospedagem em um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="a98af-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>  
  
 <span data-ttu-id="a98af-108">Ao terminar, você terá uma DLL com conteúdo Direct3D9 para uso em um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="a98af-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a98af-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a98af-109">Prerequisites</span></span>  
 <span data-ttu-id="a98af-110">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="a98af-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a98af-111">.</span><span class="sxs-lookup"><span data-stu-id="a98af-111">.</span></span>  
  
-   <span data-ttu-id="a98af-112">SDK do DirectX 9 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="a98af-112">DirectX SDK 9or later.</span></span>  
  
## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="a98af-113">Criar o projeto Direct3D9</span><span class="sxs-lookup"><span data-stu-id="a98af-113">Creating the Direct3D9 Project</span></span>  
 <span data-ttu-id="a98af-114">A primeira etapa é criar e configurar um projeto Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="a98af-114">The first step is to create and configure the Direct3D9 project.</span></span>  
  
#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="a98af-115">Criar o projeto Direct3D9</span><span class="sxs-lookup"><span data-stu-id="a98af-115">To create the Direct3D9 project</span></span>  
  
1.  <span data-ttu-id="a98af-116">Crie um novo Projeto Win32 no C++ chamado `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="a98af-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>  
  
     <span data-ttu-id="a98af-117">O Assistente de Aplicativo Win32 abrirá e exibirá a tela de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="a98af-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>  
  
2.  <span data-ttu-id="a98af-118">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a98af-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="a98af-119">A tela de Configurações do Aplicativo será exibida.</span><span class="sxs-lookup"><span data-stu-id="a98af-119">The Application Settings screen appears.</span></span>  
  
3.  <span data-ttu-id="a98af-120">Na seção **tipo de Aplicativo:**, selecione a opção **DLL**.</span><span class="sxs-lookup"><span data-stu-id="a98af-120">In the **Application type:** section, select the **DLL** option.</span></span>  
  
4.  <span data-ttu-id="a98af-121">Clique em **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="a98af-121">Click **Finish**.</span></span>  
  
     <span data-ttu-id="a98af-122">O projeto D3DContent será gerado.</span><span class="sxs-lookup"><span data-stu-id="a98af-122">The D3DContent project is generated.</span></span>  
  
5.  <span data-ttu-id="a98af-123">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto D3DContent e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a98af-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>  
  
     <span data-ttu-id="a98af-124">A caixa de diálogo **Páginas de Propriedades do D3DContent** se abrirá.</span><span class="sxs-lookup"><span data-stu-id="a98af-124">The **D3DContent Property Pages** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="a98af-125">Selecione o nó **C/C++**.</span><span class="sxs-lookup"><span data-stu-id="a98af-125">Select the **C/C++** node.</span></span>  
  
7.  <span data-ttu-id="a98af-126">No campo **Diretórios de Inclusão Adicionais**, especifique o local da pasta de inclusão DirectX.</span><span class="sxs-lookup"><span data-stu-id="a98af-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="a98af-127">O local padrão dessa pasta é %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span><span class="sxs-lookup"><span data-stu-id="a98af-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>  
  
8.  <span data-ttu-id="a98af-128">Clique duas vezes no nó **Vinculador** para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="a98af-128">Double-click the **Linker** node to expand it.</span></span>  
  
9. <span data-ttu-id="a98af-129">No campo **Diretórios de Inclusão Adicionais**, especifique o local da pasta de bibliotecas do DirectX.</span><span class="sxs-lookup"><span data-stu-id="a98af-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="a98af-130">O local padrão dessa pasta é %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="a98af-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>  
  
10. <span data-ttu-id="a98af-131">Selecione o nó **Entrada**.</span><span class="sxs-lookup"><span data-stu-id="a98af-131">Select the **Input** node.</span></span>  
  
11. <span data-ttu-id="a98af-132">No campo **Dependências Adicionais**, adicione os arquivos `d3d9.lib` e `d3dx9.lib`.</span><span class="sxs-lookup"><span data-stu-id="a98af-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>  
  
12. <span data-ttu-id="a98af-133">No Gerenciador de Soluções, adicione um novo arquivo de definição de módulo (.def) chamado `D3DContent.def` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a98af-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>  
  
## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="a98af-134">Criar o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="a98af-134">Creating the Direct3D9 Content</span></span>  
 <span data-ttu-id="a98af-135">Para obter o melhor desempenho, o conteúdo Direct3D9 deve usar configurações específicas.</span><span class="sxs-lookup"><span data-stu-id="a98af-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="a98af-136">O código a seguir mostra como criar uma superfície Direct3D9 com as melhores características de desempenho.</span><span class="sxs-lookup"><span data-stu-id="a98af-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="a98af-137">Para obter mais informações, consulte [Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="a98af-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>  
  
#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="a98af-138">Para criar o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="a98af-138">To create the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="a98af-139">Usando o Gerenciador de Soluções, adicione três classes do C++ ao projeto nomeado como a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>  
  
     <span data-ttu-id="a98af-140">`CRenderer` (com o destruidor virtual)</span><span class="sxs-lookup"><span data-stu-id="a98af-140">`CRenderer` (with virtual destructor)</span></span>  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  <span data-ttu-id="a98af-141">Abra o Renderer.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  <span data-ttu-id="a98af-142">Abra o Renderer.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  <span data-ttu-id="a98af-143">Abra o RendererManager.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  <span data-ttu-id="a98af-144">Abra o RendererManager.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  <span data-ttu-id="a98af-145">Abra o TriangleRenderer.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  <span data-ttu-id="a98af-146">Abra o TriangleRenderer.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  <span data-ttu-id="a98af-147">Abra o stdafx.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. <span data-ttu-id="a98af-148">Abra o dllmain.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. <span data-ttu-id="a98af-149">Abra o D3DContent.def no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="a98af-149">Open D3DContent.def in the code editor.</span></span>  
  
11. <span data-ttu-id="a98af-150">Substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98af-150">Replace the automatically generated code with the following code.</span></span>  
  
    ```  
    LIBRARY "D3DContent"  
  
    EXPORTS  
  
    SetSize  
    SetAlpha  
    SetNumDesiredSamples  
    SetAdapter  
  
    GetBackBufferNoRef  
    Render  
    Destroy  
    ```  
  
12. <span data-ttu-id="a98af-151">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="a98af-151">Build the project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a98af-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a98af-152">Next Steps</span></span>  
  
-   <span data-ttu-id="a98af-153">Hospede o conteúdo Direct3D9 em um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="a98af-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="a98af-154">Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando Conteúdo Direct3D9 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a98af-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98af-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a98af-155">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="a98af-156">Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF</span><span class="sxs-lookup"><span data-stu-id="a98af-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [<span data-ttu-id="a98af-157">Instruções Passo a Passo: Hospedando Conteúdo Direct3D9 no WPF</span><span class="sxs-lookup"><span data-stu-id="a98af-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
