---
title: 'Como: Adicionar uma tela inicial a um aplicativo WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307459"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="d79a1-102">Como: Adicionar uma tela inicial a um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="d79a1-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="d79a1-103">Este tópico mostra como adicionar uma janela de inicialização ou *tela inicial*, para um aplicativo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d79a1-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="d79a1-104">Para adicionar uma imagem existente como uma tela inicial</span><span class="sxs-lookup"><span data-stu-id="d79a1-104">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="d79a1-105">Crie ou localize uma imagem que deseja usar para a tela inicial.</span><span class="sxs-lookup"><span data-stu-id="d79a1-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="d79a1-106">Você pode usar qualquer formato de imagem com suporte do Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="d79a1-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="d79a1-107">Por exemplo, você pode usar o formato TIFF, GIF, JPEG, PNG ou BMP.</span><span class="sxs-lookup"><span data-stu-id="d79a1-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="d79a1-108">Adicione o arquivo de imagem ao projeto de aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="d79a1-108">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="d79a1-109">Na **Gerenciador de soluções**, selecione a imagem.</span><span class="sxs-lookup"><span data-stu-id="d79a1-109">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="d79a1-110">Na janela Propriedades, clique na seta suspensa para a propriedade **Build Action**.</span><span class="sxs-lookup"><span data-stu-id="d79a1-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="d79a1-111">Selecione **SplashScreen** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="d79a1-111">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="d79a1-112">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d79a1-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="d79a1-113">A imagem da tela inicial aparece no centro da tela e, em seguida, desaparece quando a janela principal do aplicativo aparecer.</span><span class="sxs-lookup"><span data-stu-id="d79a1-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="d79a1-114">Para excluir a tela inicial de build</span><span class="sxs-lookup"><span data-stu-id="d79a1-114">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="d79a1-115">Na **Gerenciador de soluções**, selecione a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="d79a1-115">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="d79a1-116">No **propriedades** janela, defina as **Build Action** para **None**.</span><span class="sxs-lookup"><span data-stu-id="d79a1-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="d79a1-117">Para remover a tela inicial de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="d79a1-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="d79a1-118">Na **Gerenciador de soluções**, exclua a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="d79a1-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="d79a1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d79a1-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="d79a1-120">[Como: Adicionar itens existentes a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d79a1-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
