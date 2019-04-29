---
title: 'Como: Criar um Windows Form redimensionável para entrada de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: ebccad248927d8a201bd5758e5ddf2d5414455f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746635"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="d0afc-102">Como: Criar um Windows Form redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="d0afc-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="d0afc-103">Um bom layout responde bem a alterações nas dimensões de seu formulário pai.</span><span class="sxs-lookup"><span data-stu-id="d0afc-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="d0afc-104">Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para organizar o layout do formulário para redimensionar e posicionar os controles de forma consistente, como alterar de dimensões do formulário.</span><span class="sxs-lookup"><span data-stu-id="d0afc-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="d0afc-105">O <xref:System.Windows.Forms.TableLayoutPanel> controle também é útil quando altera o conteúdo de seus controles causa alterações no layout.</span><span class="sxs-lookup"><span data-stu-id="d0afc-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="d0afc-106">O processo abordado neste procedimento pode ser realizado no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0afc-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="d0afc-107">Consulte também [passo a passo: Criando um formulário do Windows redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d0afc-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0afc-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0afc-108">Example</span></span>  
 <span data-ttu-id="d0afc-109">O exemplo a seguir demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um layout que responda bem quando o usuário redimensiona o formulário.</span><span class="sxs-lookup"><span data-stu-id="d0afc-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="d0afc-110">Ele também demonstra um layout que responde bem à localização.</span><span class="sxs-lookup"><span data-stu-id="d0afc-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0afc-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d0afc-111">Compiling the Code</span></span>  
 <span data-ttu-id="d0afc-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d0afc-112">This example requires:</span></span>  
  
- <span data-ttu-id="d0afc-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d0afc-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d0afc-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d0afc-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d0afc-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="d0afc-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0afc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0afc-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="d0afc-117">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d0afc-117">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="d0afc-118">Como: Projetar um Layout de formulários do Windows que responde bem à localização</span><span class="sxs-lookup"><span data-stu-id="d0afc-118">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="d0afc-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário). Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="d0afc-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
