---
title: "Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d57eee9181298ce3afa61a1e7a13d8f092ad68f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2c308-102">Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c308-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2c308-103">Você pode controlar a aparência de <xref:System.Windows.Forms.DataGridView> linhas ao manipular uma ou ambas as <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="2c308-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="2c308-104">Esses eventos são projetados para que pintar apenas o que você deseja enquanto permitindo que o <xref:System.Windows.Forms.DataGridView> controle pintar o restante.</span><span class="sxs-lookup"><span data-stu-id="2c308-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="2c308-105">Por exemplo, se você quiser pintar o plano de fundo personalizado, você pode manipular o <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> eventos e permitem que as células individuais de pintura com seus próprio conteúdo de primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="2c308-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="2c308-106">Como alternativa, você pode deixar as células pintar a mesmos e adicionar o conteúdo do primeiro plano personalizado em um manipulador para o <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="2c308-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="2c308-107">Você também pode desabilitar pintura da célula e pintar tudo por conta própria em um <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2c308-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="2c308-108">O exemplo de código a seguir implementa manipuladores para ambos os eventos a fim de fornecer uma tela de fundo de seleção do gradiente e algum conteúdo de primeiro plano personalizado que abrange várias colunas.</span><span class="sxs-lookup"><span data-stu-id="2c308-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c308-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c308-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2c308-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2c308-110">Compiling the Code</span></span>  
 <span data-ttu-id="2c308-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2c308-111">This example requires:</span></span>  
  
-   <span data-ttu-id="2c308-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2c308-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2c308-113">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="2c308-113">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2c308-114">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="2c308-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="2c308-115">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="2c308-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c308-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c308-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [<span data-ttu-id="2c308-117">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c308-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2c308-118">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="2c308-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
