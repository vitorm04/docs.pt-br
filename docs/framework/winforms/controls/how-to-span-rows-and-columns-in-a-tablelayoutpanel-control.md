---
title: Como abranger linhas e colunas em um controle TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a78286be8ef64212d945b3cb11a2963d5a1b2e79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535341"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="4ef15-102">Como abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4ef15-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="4ef15-103">Controles em um <xref:System.Windows.Forms.TableLayoutPanel> controle pode abranger linhas e colunas adjacentes.</span><span class="sxs-lookup"><span data-stu-id="4ef15-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ef15-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="4ef15-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4ef15-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4ef15-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4ef15-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4ef15-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="4ef15-107">Para abranger linhas e colunas</span><span class="sxs-lookup"><span data-stu-id="4ef15-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="4ef15-108">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="4ef15-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="4ef15-109">Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** na célula superior esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="4ef15-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="4ef15-110">Definir o <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **2**.</span><span class="sxs-lookup"><span data-stu-id="4ef15-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="4ef15-111">Observe que o <xref:System.Windows.Forms.Button> controle abrange a primeira e segunda coluna.</span><span class="sxs-lookup"><span data-stu-id="4ef15-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="4ef15-112">Definir o <xref:System.Windows.Forms.Button> do controle **RowSpan** propriedade **2**.</span><span class="sxs-lookup"><span data-stu-id="4ef15-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="4ef15-113">Observe que o <xref:System.Windows.Forms.Button> controle abrange as primeira e segunda linhas.</span><span class="sxs-lookup"><span data-stu-id="4ef15-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="4ef15-114">Definir o <xref:System.Windows.Forms.Button> do controle **ColumnSpan** propriedade **1**.</span><span class="sxs-lookup"><span data-stu-id="4ef15-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="4ef15-115">Observe que o <xref:System.Windows.Forms.Button> controle move para a primeira coluna e abrange as primeira e segunda linhas.</span><span class="sxs-lookup"><span data-stu-id="4ef15-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef15-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ef15-116">See Also</span></span>  
 [<span data-ttu-id="4ef15-117">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4ef15-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
