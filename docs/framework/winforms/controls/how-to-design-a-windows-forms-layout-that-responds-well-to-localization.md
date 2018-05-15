---
title: Como criar um layout dos Windows Forms que responda bem à localização
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
ms.openlocfilehash: aa141319e902ff96ecfb9e9a70ca66528705418d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="81b65-102">Como criar um layout dos Windows Forms que responda bem à localização</span><span class="sxs-lookup"><span data-stu-id="81b65-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="81b65-103">Criação de formulários que estão prontos para ser localizados aumenta a velocidade de desenvolvimento para mercados internacionais.</span><span class="sxs-lookup"><span data-stu-id="81b65-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="81b65-104">Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar layouts respondem normalmente como redimensionam controles devido a alterações em seus <xref:System.Windows.Forms.Control.Text%2A> valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="81b65-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81b65-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81b65-105">Example</span></span>  
 <span data-ttu-id="81b65-106">Este formulário demonstra como criar um layout que proporcionalmente se ajusta ao converter valores de cadeia de caracteres exibidos em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="81b65-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="81b65-107">Esse processo de conversão é chamado *localização*.</span><span class="sxs-lookup"><span data-stu-id="81b65-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="81b65-108">Para obter mais informações, consulte [localização](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="81b65-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="81b65-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81b65-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="81b65-110">Consulte também [passo a passo: Criando um Layout que ajusta proporção para localização](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="81b65-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  <span data-ttu-id="81b65-111">[Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-111">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="81b65-112">[Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="81b65-113">[Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-113">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="81b65-114">[Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-114">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
5.  <span data-ttu-id="81b65-115">[Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="81b65-116">[Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="81b65-117">[Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="81b65-118">[Como: oferecer suporte à localização no Windows Forms usando AutoSize e o controle TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="81b65-119">[Passo a passo: Criando um Windows Form redimensionável para entrada de dados](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="81b65-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81b65-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="81b65-120">Compiling the Code</span></span>  
 <span data-ttu-id="81b65-121">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="81b65-121">This example requires:</span></span>  
  
-   <span data-ttu-id="81b65-122">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="81b65-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="81b65-123">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="81b65-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="81b65-124">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="81b65-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="81b65-125">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="81b65-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b65-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81b65-126">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="81b65-127">Localização</span><span class="sxs-lookup"><span data-stu-id="81b65-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
