---
title: Como adicionar uma tela inicial a um aplicativo WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 06d6cb7c5a5081d3b6c4979ab50e1caaa726acbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546995"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="cdaac-102">Como adicionar uma tela inicial a um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="cdaac-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="cdaac-103">Este tópico mostra como adicionar uma janela de inicialização ou *tela inicial*, para um aplicativo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="cdaac-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="cdaac-104">Para adicionar uma imagem existente como uma tela inicial</span><span class="sxs-lookup"><span data-stu-id="cdaac-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="cdaac-105">Crie ou localize uma imagem que deseja usar para a tela inicial.</span><span class="sxs-lookup"><span data-stu-id="cdaac-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="cdaac-106">Você pode usar qualquer formato de imagem com suporte do Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="cdaac-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="cdaac-107">Por exemplo, você pode usar o formato TIFF, GIF, JPEG, PNG ou BMP.</span><span class="sxs-lookup"><span data-stu-id="cdaac-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="cdaac-108">Adicione o arquivo de imagem ao projeto de aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="cdaac-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="cdaac-109">Para obter mais informações, consulte [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="cdaac-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="cdaac-110">No Gerenciador de Soluções, selecione a imagem.</span><span class="sxs-lookup"><span data-stu-id="cdaac-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="cdaac-111">Na janela Propriedades, clique na seta suspensa para a propriedade **Build Action**.</span><span class="sxs-lookup"><span data-stu-id="cdaac-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="cdaac-112">Selecione **SplashScreen** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="cdaac-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cdaac-113">Se você não vir a opção **SplashScreen**, certifique-se de verificar se está usando [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="cdaac-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="cdaac-114">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdaac-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="cdaac-115">A imagem da tela inicial aparece no centro da tela e, em seguida, desaparece quando a janela principal do aplicativo aparecer.</span><span class="sxs-lookup"><span data-stu-id="cdaac-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="cdaac-116">Para remover a tela inicial de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="cdaac-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="cdaac-117">No Gerenciador de Soluções, selecione a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="cdaac-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="cdaac-118">Na janela Propriedades, defina **Build Action** como **None**.</span><span class="sxs-lookup"><span data-stu-id="cdaac-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="cdaac-119">Para remover a tela inicial de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="cdaac-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="cdaac-120">No Gerenciador de Soluções, exclua a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="cdaac-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="cdaac-121">Exclua a imagem da tela inicial do projeto.</span><span class="sxs-lookup"><span data-stu-id="cdaac-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdaac-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdaac-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="cdaac-123">NIB: como adicionar itens existentes a um projeto</span><span class="sxs-lookup"><span data-stu-id="cdaac-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
