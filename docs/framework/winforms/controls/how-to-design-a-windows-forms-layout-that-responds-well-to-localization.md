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
ms.openlocfilehash: 9556c03699713b7d14f81a6eacc8e4ab337e869b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628625"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="569ac-102">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="569ac-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="569ac-103">Criar formulários que estão prontos para serem localizados acelera bastante o desenvolvimento para mercados internacionais.</span><span class="sxs-lookup"><span data-stu-id="569ac-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="569ac-104">Você pode usar o controle de <xref:System.Windows.Forms.TableLayoutPanel> para implementar layouts que respondem normalmente à medida que os controles são redimensionados devido a alterações em seus valores de propriedade <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="569ac-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>

## <a name="example"></a><span data-ttu-id="569ac-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="569ac-105">Example</span></span>
 <span data-ttu-id="569ac-106">Este formulário demonstra como criar um layout que se ajusta proporcionalmente ao converter valores de cadeia de caracteres exibidos em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="569ac-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="569ac-107">Esse processo de conversão é chamado de *localização*.</span><span class="sxs-lookup"><span data-stu-id="569ac-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="569ac-108">Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="569ac-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>

 <span data-ttu-id="569ac-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="569ac-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="569ac-110">Consulte também [Walkthrough: Criando um layout que ajusta a proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="569ac-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>

 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]

## <a name="additional-resources"></a><span data-ttu-id="569ac-111">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="569ac-111">Additional resources</span></span>

1. [<span data-ttu-id="569ac-112">Como alinhar e alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="569ac-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)

2. [<span data-ttu-id="569ac-113">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="569ac-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)

3. [<span data-ttu-id="569ac-114">Como abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="569ac-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)

4. [<span data-ttu-id="569ac-115">Como editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="569ac-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)

5. [<span data-ttu-id="569ac-116">Walkthrough: executar tarefas comuns usando ações de designer</span><span class="sxs-lookup"><span data-stu-id="569ac-116">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)

6. [<span data-ttu-id="569ac-117">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="569ac-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)

7. [<span data-ttu-id="569ac-118">Instruções passo a passo: projetando controles do Windows Forms com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="569ac-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)

8. <span data-ttu-id="569ac-119">[Como: dar suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="569ac-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>

9. <span data-ttu-id="569ac-120">[Walkthrough: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="569ac-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="569ac-121">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="569ac-121">Compiling the Code</span></span>
 <span data-ttu-id="569ac-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="569ac-122">This example requires:</span></span>

- <span data-ttu-id="569ac-123">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="569ac-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="569ac-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="569ac-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="569ac-125">Localização</span><span class="sxs-lookup"><span data-stu-id="569ac-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
