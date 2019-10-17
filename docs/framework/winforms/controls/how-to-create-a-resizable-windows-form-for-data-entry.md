---
title: Como criar um Windows Form redimensionável para entrada de dados
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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396021"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="77cae-102">Como criar um Windows Form redimensionável para entrada de dados</span><span class="sxs-lookup"><span data-stu-id="77cae-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="77cae-103">Um bom layout responde bem a alterações nas dimensões de seu formulário pai.</span><span class="sxs-lookup"><span data-stu-id="77cae-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="77cae-104">Você pode usar o controle <xref:System.Windows.Forms.TableLayoutPanel> para organizar o layout do formulário para redimensionar e posicionar os controles de forma consistente à medida que as dimensões do formulário são alteradas.</span><span class="sxs-lookup"><span data-stu-id="77cae-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="77cae-105">O controle <xref:System.Windows.Forms.TableLayoutPanel> também é útil quando as alterações no conteúdo dos controles causam alterações no layout.</span><span class="sxs-lookup"><span data-stu-id="77cae-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="77cae-106">O processo abordado neste procedimento pode ser realizado no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77cae-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="77cae-107">Consulte também [Instruções passo a passo: criando um Windows Form redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="77cae-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77cae-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77cae-108">Example</span></span>  
 <span data-ttu-id="77cae-109">O exemplo a seguir demonstra como usar um controle <xref:System.Windows.Forms.TableLayoutPanel> para criar um layout que responde bem quando o usuário redimensiona o formulário.</span><span class="sxs-lookup"><span data-stu-id="77cae-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="77cae-110">Ele também demonstra um layout que responde bem à localização.</span><span class="sxs-lookup"><span data-stu-id="77cae-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77cae-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="77cae-111">Compiling the Code</span></span>  
 <span data-ttu-id="77cae-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="77cae-112">This example requires:</span></span>  
  
- <span data-ttu-id="77cae-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="77cae-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77cae-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="77cae-115">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="77cae-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="77cae-116">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="77cae-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
