---
title: Como reatribuir controles existentes a um pai diferente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998c002591850c0af3c265ae88b10657343787
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="08e5d-102">Como reatribuir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="08e5d-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="08e5d-103">Você pode atribuir controles que existem em seu formulário para um novo controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="08e5d-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08e5d-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="08e5d-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="08e5d-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="08e5d-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="08e5d-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="08e5d-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="08e5d-107">Para reatribuir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="08e5d-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="08e5d-108">Arraste três <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="08e5d-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="08e5d-109">Posicione-os próximo entre si, mas deixe-os desalinhados.</span><span class="sxs-lookup"><span data-stu-id="08e5d-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="08e5d-110">No **caixa de ferramentas**, clique no <xref:System.Windows.Forms.FlowLayoutPanel> ícone do controle.</span><span class="sxs-lookup"><span data-stu-id="08e5d-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="08e5d-111">Não arraste o ícone para o formulário.</span><span class="sxs-lookup"><span data-stu-id="08e5d-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="08e5d-112">Mova o ponteiro do mouse perto de três <xref:System.Windows.Forms.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="08e5d-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="08e5d-113">O ponteiro mudar para uma cruz com o <xref:System.Windows.Forms.FlowLayoutPanel> ícone de controle.</span><span class="sxs-lookup"><span data-stu-id="08e5d-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="08e5d-114">Clique e mantenha o botão do mouse pressionado.</span><span class="sxs-lookup"><span data-stu-id="08e5d-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="08e5d-115">Arraste o ponteiro do mouse para desenhar o contorno do <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="08e5d-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="08e5d-116">Desenhar o contorno em torno de três <xref:System.Windows.Forms.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="08e5d-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="08e5d-117">Solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="08e5d-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="08e5d-118">Os três <xref:System.Windows.Forms.Button> controles agora são inseridos a <xref:System.Windows.Forms.FlowLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="08e5d-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e5d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08e5d-119">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="08e5d-120">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08e5d-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="08e5d-121">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="08e5d-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="08e5d-122">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="08e5d-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
