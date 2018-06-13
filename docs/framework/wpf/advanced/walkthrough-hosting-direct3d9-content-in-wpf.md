---
title: 'Instruções passo a passo: hospedando conteúdo de Direct3D9 no WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 3b215c0eead8c5fc28b477b81f75c39b5c946302
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546155"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="66c05-102">Instruções passo a passo: hospedando conteúdo de Direct3D9 no WPF</span><span class="sxs-lookup"><span data-stu-id="66c05-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="66c05-103">Esta instrução passo a passo mostra como hospedar o conteúdo Direct3D9 em um aplicativo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="66c05-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="66c05-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="66c05-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="66c05-105">Crie um projeto WPF para hospedar o conteúdo Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="66c05-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="66c05-106">Importe o conteúdo Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="66c05-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="66c05-107">Exibir o conteúdo de Direct3D9 usando o <xref:System.Windows.Interop.D3DImage> classe.</span><span class="sxs-lookup"><span data-stu-id="66c05-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="66c05-108">Quando tiver terminado, você saberá como hospedar conteúdo Direct3D9 em um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="66c05-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66c05-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="66c05-109">Prerequisites</span></span>  
 <span data-ttu-id="66c05-110">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="66c05-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="66c05-111">.</span><span class="sxs-lookup"><span data-stu-id="66c05-111">.</span></span>  
  
-   <span data-ttu-id="66c05-112">DirectX SDK 9 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="66c05-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="66c05-113">Uma DLL que contém o conteúdo Direct3D9 em um formato compatível com WPF.</span><span class="sxs-lookup"><span data-stu-id="66c05-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="66c05-114">Para obter mais informações, consulte [Interoperação de WPF e Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) e [Instrução passo a passo: criando conteúdo Direct3D9 para hospedar em WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="66c05-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="66c05-115">Criando o projeto WPF</span><span class="sxs-lookup"><span data-stu-id="66c05-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="66c05-116">A primeira etapa é criar o projeto do aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="66c05-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="66c05-117">Para criar o projeto WPF</span><span class="sxs-lookup"><span data-stu-id="66c05-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="66c05-118">Crie um novo projeto de aplicativo do WPF no Visual C#, chamado `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="66c05-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="66c05-119">Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="66c05-119">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="66c05-120">MainWindow.xaml é aberto no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66c05-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="66c05-121">Importando o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="66c05-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="66c05-122">Importar o conteúdo de Direct3D9 de uma DLL não gerenciada usando o `DllImport` atributo.</span><span class="sxs-lookup"><span data-stu-id="66c05-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="66c05-123">Para importar o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="66c05-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="66c05-124">Abra MainWindow.xaml.cs no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="66c05-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="66c05-125">Substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="66c05-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="66c05-126">Hospedando o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="66c05-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="66c05-127">Por fim, use o <xref:System.Windows.Interop.D3DImage> classe para hospedar o conteúdo de Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="66c05-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="66c05-128">Para hospedar o conteúdo Direct3D9</span><span class="sxs-lookup"><span data-stu-id="66c05-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="66c05-129">Em MainWindow.xaml, substitua o XAML gerado automaticamente pelo seguinte XAML.</span><span class="sxs-lookup"><span data-stu-id="66c05-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="66c05-130">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="66c05-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="66c05-131">Copie a DLL que contém o conteúdo Direct3D9 para a pasta lixeira/Debug.</span><span class="sxs-lookup"><span data-stu-id="66c05-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="66c05-132">Pressione F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="66c05-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="66c05-133">O conteúdo Direct3D9 aparece dentro do aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="66c05-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c05-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66c05-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="66c05-135">Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF</span><span class="sxs-lookup"><span data-stu-id="66c05-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
