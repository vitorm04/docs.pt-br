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
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310753"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="8f453-102">Como: Criar um layout do Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="8f453-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="8f453-103">Criação de formulários que estão prontos para serem localizados aumenta a velocidade de desenvolvimento para mercados internacionais.</span><span class="sxs-lookup"><span data-stu-id="8f453-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="8f453-104">Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar os layouts que respondem normalmente como controles redimensionam devido a alterações nas suas <xref:System.Windows.Forms.Control.Text%2A> valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="8f453-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f453-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f453-105">Example</span></span>  
 <span data-ttu-id="8f453-106">Este formulário demonstra como criar um layout que ajusta proporcionalmente quando você converter valores de cadeia de caracteres exibidos em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="8f453-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="8f453-107">Esse processo de conversão é chamado *localização*.</span><span class="sxs-lookup"><span data-stu-id="8f453-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="8f453-108">Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="8f453-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="8f453-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f453-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="8f453-110">Consulte também [passo a passo: Criando um Layout que ajusta proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8f453-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="8f453-111">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="8f453-111">Additional resources</span></span>
1. [<span data-ttu-id="8f453-112">Como: Alinhar e Alongar um controle em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f453-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="8f453-113">Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f453-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="8f453-114">Como: Abranger linhas e colunas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f453-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="8f453-115">Como: Editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f453-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="8f453-116">Passo a passo: Realizando tarefas comuns usando Smart Tags no Windows, controles de formulários</span><span class="sxs-lookup"><span data-stu-id="8f453-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="8f453-117">Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f453-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="8f453-118">Passo a passo: Definindo o layout dos Windows Forms controles com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="8f453-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="8f453-119">[Como: Suporte à localização em formulários do Windows usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8f453-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="8f453-120">[Passo a passo: Criando um formulário do Windows redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8f453-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f453-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8f453-121">Compiling the Code</span></span>  
 <span data-ttu-id="8f453-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8f453-122">This example requires:</span></span>  
  
-   <span data-ttu-id="8f453-123">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8f453-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8f453-124">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8f453-124">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8f453-125">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="8f453-125">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f453-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f453-126">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="8f453-127">Localização</span><span class="sxs-lookup"><span data-stu-id="8f453-127">Localization</span></span>](../../../standard/globalization-localization/localization.md)
