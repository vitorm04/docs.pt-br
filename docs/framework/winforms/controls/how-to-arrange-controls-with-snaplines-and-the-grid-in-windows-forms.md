---
title: Como organizar controles com guias de alinhamento e a grade nos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 166ccba959bd9facb8e24d580d47577a0c8746a8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="00a3b-102">Como organizar controles com guias de alinhamento e a grade nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00a3b-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="00a3b-103">Ao usar os recursos de layout do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], você pode direcionar precisamente onde os controles serão colocados em um formulário.</span><span class="sxs-lookup"><span data-stu-id="00a3b-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="00a3b-104">Controles adicionados a um formulário ou movidos em um formulário podem ser alinhados automaticamente para as linhas e colunas da grade Designer de Formulários do Windows ou você pode alinhar controles usando o recurso de guias de ajuste.</span><span class="sxs-lookup"><span data-stu-id="00a3b-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00a3b-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="00a3b-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="00a3b-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="00a3b-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="00a3b-107">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="00a3b-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="00a3b-108">Para ajustar todos os controles à grade</span><span class="sxs-lookup"><span data-stu-id="00a3b-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="00a3b-109">Selecione o modo de layout **SnapToGrid** na caixa de diálogo **Opções** do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="00a3b-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="00a3b-110">Para obter mais informações, consulte [Geral, Designer de Formulários do Windows, Caixa de diálogo Opções](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="00a3b-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="00a3b-111">Todos os controles agora se alinham junto aos pontos na grade.</span><span class="sxs-lookup"><span data-stu-id="00a3b-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="00a3b-112">Você pode encaixar controles individuais na grade bloqueando-os no lugar.</span><span class="sxs-lookup"><span data-stu-id="00a3b-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="00a3b-113">No entanto, enquanto eles estiverem bloqueados, não poderão ser movidos ou redimensionados.</span><span class="sxs-lookup"><span data-stu-id="00a3b-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="00a3b-114">Para obter mais informações sobre bloqueio de controles, consulte [Como bloquear controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="00a3b-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="00a3b-115">Para alinhar controles usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="00a3b-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="00a3b-116">Selecione o modo de layout **SnapLines** na caixa de diálogo **Opções** do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="00a3b-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="00a3b-117">Para obter mais informações, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="00a3b-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="00a3b-118">Agora você pode usar guias de alinhamento para alinhar e organizar controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="00a3b-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a3b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00a3b-119">See Also</span></span>  
 [<span data-ttu-id="00a3b-120">Geral, Designer de formulários do Windows, a caixa de diálogo Opções</span><span class="sxs-lookup"><span data-stu-id="00a3b-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="00a3b-121">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="00a3b-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="00a3b-122">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00a3b-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="00a3b-123">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00a3b-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="00a3b-124">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00a3b-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="00a3b-125">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="00a3b-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="00a3b-126">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00a3b-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="00a3b-127">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="00a3b-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
