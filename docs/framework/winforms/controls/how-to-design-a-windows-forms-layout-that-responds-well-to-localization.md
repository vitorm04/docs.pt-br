---
title: Criar um layout amigável à localização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743286"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="2f45c-102">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="2f45c-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="2f45c-103">Criar formulários que estão prontos para serem localizados acelera bastante o desenvolvimento para mercados internacionais.</span><span class="sxs-lookup"><span data-stu-id="2f45c-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="2f45c-104">Você pode usar o controle de <xref:System.Windows.Forms.TableLayoutPanel> para implementar layouts que respondem normalmente à medida que os controles são redimensionados devido a alterações em seus valores de propriedade <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f45c-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f45c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f45c-105">Example</span></span>  
 <span data-ttu-id="2f45c-106">Este formulário demonstra como criar um layout que se ajusta proporcionalmente ao converter valores de cadeia de caracteres exibidos em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="2f45c-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="2f45c-107">Esse processo de conversão é chamado de *localização*.</span><span class="sxs-lookup"><span data-stu-id="2f45c-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="2f45c-108">Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="2f45c-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="2f45c-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f45c-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="2f45c-110">Consulte também [Walkthrough: Criando um layout que ajusta a proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2f45c-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="2f45c-111">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2f45c-111">Additional resources</span></span>

1. [<span data-ttu-id="2f45c-112">Como alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2f45c-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="2f45c-113">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2f45c-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="2f45c-114">Como abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2f45c-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="2f45c-115">Como editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2f45c-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="2f45c-116">Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f45c-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="2f45c-117">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2f45c-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="2f45c-118">Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="2f45c-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="2f45c-119">[Como: dar suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f45c-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="2f45c-120">[Walkthrough: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f45c-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f45c-121">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="2f45c-121">Compiling the Code</span></span>  
 <span data-ttu-id="2f45c-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2f45c-122">This example requires:</span></span>  
  
- <span data-ttu-id="2f45c-123">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2f45c-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f45c-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="2f45c-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="2f45c-125">Localização</span><span class="sxs-lookup"><span data-stu-id="2f45c-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
