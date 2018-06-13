---
title: Visão geral do controle TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 4514901870d9073b611746070a1f53d01db95766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541359"
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="b3faa-102">Visão geral do controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b3faa-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="b3faa-103">O <xref:System.Windows.Forms.TableLayoutPanel> controle organiza seu conteúdo em uma grade.</span><span class="sxs-lookup"><span data-stu-id="b3faa-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="b3faa-104">Como o layout é executado tanto em tempo de design quanto em tempo de execução, ele pode ser alterado dinamicamente à medida que o ambiente do aplicativo muda.</span><span class="sxs-lookup"><span data-stu-id="b3faa-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="b3faa-105">Assim, os controles no painel têm a capacidade de redimensionar proporcionalmente, portanto ele pode responder a alterações como o redimensionamento do controle pai ou à alteração de comprimento do texto devido à localização.</span><span class="sxs-lookup"><span data-stu-id="b3faa-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="b3faa-106">Qualquer controle de formulários do Windows pode ser um filho de <xref:System.Windows.Forms.TableLayoutPanel> controle, inclusive de outras instâncias de <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="b3faa-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="b3faa-107">Isso permite criar layouts sofisticados que se adaptam às alterações no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b3faa-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="b3faa-108">O <xref:System.Windows.Forms.TableLayoutPanel> controle pode ser expandido para acomodar novos controles quando eles são adicionados, dependendo do valor da <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, e <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="b3faa-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="b3faa-109">Configuração de <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ou <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> propriedade para um valor de 0 especifica que o <xref:System.Windows.Forms.TableLayoutPanel> será desacoplado na direção correspondente.</span><span class="sxs-lookup"><span data-stu-id="b3faa-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="b3faa-110">Você também pode controlar a direção de expansão (horizontal ou vertical) após o <xref:System.Windows.Forms.TableLayoutPanel> controle está completo de controles filho.</span><span class="sxs-lookup"><span data-stu-id="b3faa-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="b3faa-111">Por padrão, o <xref:System.Windows.Forms.TableLayoutPanel> controle se expande para baixo, adicionando linhas.</span><span class="sxs-lookup"><span data-stu-id="b3faa-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="b3faa-112">Se você desejar linhas e colunas que se comportam de maneira diferente do comportamento padrão, você pode controlar as propriedades de linhas e colunas usando o <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> e <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="b3faa-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="b3faa-113">É possível definir as propriedades de linhas ou colunas individualmente.</span><span class="sxs-lookup"><span data-stu-id="b3faa-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="b3faa-114">O <xref:System.Windows.Forms.TableLayoutPanel> controle adiciona as seguintes propriedades para seus controles filhos: `Cell`, `Column`, `Row`, `ColumnSpan`, e `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="b3faa-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="b3faa-115">Você pode mesclar células no <xref:System.Windows.Forms.TableLayoutPanel> controle definindo o `ColumnSpan` ou `RowSpan` propriedades em um controle filho.</span><span class="sxs-lookup"><span data-stu-id="b3faa-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  <span data-ttu-id="b3faa-116">[Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="b3faa-116">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="b3faa-117">[Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="b3faa-117">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="b3faa-118">[Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="b3faa-118">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="b3faa-119">[Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="b3faa-119">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3faa-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3faa-120">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [<span data-ttu-id="b3faa-121">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="b3faa-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="b3faa-122">Como criar um Windows Form redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="b3faa-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [<span data-ttu-id="b3faa-123">Práticas recomendadas para o controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b3faa-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
