---
title: 'Como: Alinhar e alongar um controle em um controle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 6f36914387519b027fcf4cb6bf1e7654e551b3eb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328017"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="6cd95-102">Como: Alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6cd95-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="6cd95-103">Você pode alinhar e Alongar controles em uma <xref:System.Windows.Forms.TableLayoutPanel> com o <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="6cd95-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cd95-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="6cd95-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6cd95-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="6cd95-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6cd95-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="6cd95-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="6cd95-107">Para alinhar e alongar um controle</span><span class="sxs-lookup"><span data-stu-id="6cd95-107">To align and stretch a control</span></span>  
  
1. <span data-ttu-id="6cd95-108">Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="6cd95-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="6cd95-109">Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** a célula do canto superior esquerdo do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="6cd95-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="6cd95-110">O <xref:System.Windows.Forms.Button> controle é centralizado na célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3. <span data-ttu-id="6cd95-111">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="6cd95-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="6cd95-112">O <xref:System.Windows.Forms.Button> controlar alonga para corresponder à largura da célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4. <span data-ttu-id="6cd95-113">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="6cd95-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="6cd95-114">O <xref:System.Windows.Forms.Button> controlar alonga para corresponder à altura da célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5. <span data-ttu-id="6cd95-115">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="6cd95-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="6cd95-116">O <xref:System.Windows.Forms.Button> controle se expande para preencher a célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6. <span data-ttu-id="6cd95-117">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="6cd95-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="6cd95-118">O <xref:System.Windows.Forms.Button> controle retorna ao seu tamanho original e o move para o canto superior esquerdo da célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="6cd95-119">O **Designer de formulários do Windows** definiu o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="6cd95-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7. <span data-ttu-id="6cd95-120">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="6cd95-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="6cd95-121">O <xref:System.Windows.Forms.Button> controle se move para o canto inferior direito da célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8. <span data-ttu-id="6cd95-122">Defina o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="6cd95-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="6cd95-123">O <xref:System.Windows.Forms.Button> controle se move para o centro da célula.</span><span class="sxs-lookup"><span data-stu-id="6cd95-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd95-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cd95-124">See also</span></span>

- [<span data-ttu-id="6cd95-125">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6cd95-125">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
