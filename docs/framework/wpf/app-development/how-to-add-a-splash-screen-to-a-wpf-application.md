---
title: Como adicionar uma tela inicial
description: Descubra como adicionar uma janela de inicialização, ou tela inicial, a um aplicativo Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617954"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="fd16b-103">Como adicionar uma tela inicial a um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="fd16b-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="fd16b-104">Este tópico mostra como adicionar uma janela de inicialização ou *tela inicial*, para um aplicativo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="fd16b-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="fd16b-105">Para adicionar uma imagem existente como uma tela inicial</span><span class="sxs-lookup"><span data-stu-id="fd16b-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="fd16b-106">Crie ou localize uma imagem que deseja usar para a tela inicial.</span><span class="sxs-lookup"><span data-stu-id="fd16b-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="fd16b-107">Você pode usar qualquer formato de imagem com suporte do Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="fd16b-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="fd16b-108">Por exemplo, você pode usar o formato TIFF, GIF, JPEG, PNG ou BMP.</span><span class="sxs-lookup"><span data-stu-id="fd16b-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="fd16b-109">Adicione o arquivo de imagem ao projeto de aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="fd16b-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="fd16b-110">Em **Gerenciador de soluções**, selecione a imagem.</span><span class="sxs-lookup"><span data-stu-id="fd16b-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="fd16b-111">Na janela Propriedades, clique na seta suspensa para a propriedade **Build Action**.</span><span class="sxs-lookup"><span data-stu-id="fd16b-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="fd16b-112">Selecione **SplashScreen** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="fd16b-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="fd16b-113">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fd16b-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="fd16b-114">A imagem da tela inicial aparece no centro da tela e, em seguida, desaparece quando a janela principal do aplicativo aparecer.</span><span class="sxs-lookup"><span data-stu-id="fd16b-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="fd16b-115">Para excluir a tela inicial da compilação</span><span class="sxs-lookup"><span data-stu-id="fd16b-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="fd16b-116">Em **Gerenciador de soluções**, selecione a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="fd16b-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="fd16b-117">Na janela **Propriedades** , defina a **ação de compilação** como **nenhuma**.</span><span class="sxs-lookup"><span data-stu-id="fd16b-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="fd16b-118">Para remover a tela inicial de um aplicativo</span><span class="sxs-lookup"><span data-stu-id="fd16b-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="fd16b-119">Em **Gerenciador de soluções**, exclua a imagem da tela inicial.</span><span class="sxs-lookup"><span data-stu-id="fd16b-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd16b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd16b-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="fd16b-121">[Como adicionar itens existentes a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fd16b-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
