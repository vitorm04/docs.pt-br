---
title: 'Como: Criar um layout do Windows Forms que responda bem à localização'
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
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928562"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="e88c5-102">Como: Criar um layout do Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="e88c5-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="e88c5-103">Criar formulários que estão prontos para serem localizados acelera bastante o desenvolvimento para mercados internacionais.</span><span class="sxs-lookup"><span data-stu-id="e88c5-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="e88c5-104">Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar layouts que respondem normalmente conforme os controles são redimensionados <xref:System.Windows.Forms.Control.Text%2A> devido a alterações em seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e88c5-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e88c5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88c5-105">Example</span></span>  
 <span data-ttu-id="e88c5-106">Este formulário demonstra como criar um layout que se ajusta proporcionalmente ao converter valores de cadeia de caracteres exibidos em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="e88c5-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="e88c5-107">Esse processo de conversão é chamado de *localização*.</span><span class="sxs-lookup"><span data-stu-id="e88c5-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="e88c5-108">Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="e88c5-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="e88c5-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e88c5-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="e88c5-110">Consulte também [passo a passos: Criando um layout que ajusta a proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e88c5-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="e88c5-111">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e88c5-111">Additional resources</span></span>

1. [<span data-ttu-id="e88c5-112">Como: Alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e88c5-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="e88c5-113">Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e88c5-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="e88c5-114">Como: Abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e88c5-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="e88c5-115">Como: Editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e88c5-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="e88c5-116">Passo a passo: Executando tarefas comuns usando marcas inteligentes em controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e88c5-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="e88c5-117">Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e88c5-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="e88c5-118">Passo a passo: Dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="e88c5-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="e88c5-119">[Como: Suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e88c5-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="e88c5-120">[Passo a passo: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e88c5-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e88c5-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e88c5-121">Compiling the Code</span></span>  
 <span data-ttu-id="e88c5-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e88c5-122">This example requires:</span></span>  
  
- <span data-ttu-id="e88c5-123">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e88c5-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88c5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e88c5-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="e88c5-125">Localização</span><span class="sxs-lookup"><span data-stu-id="e88c5-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
