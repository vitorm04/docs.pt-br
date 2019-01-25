---
title: 'Como: Personalizar a aparência das linhas no controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 6ec3765eb667f8a249afa815400eb7f1edbec3dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632940"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d0780-102">Como: Personalizar a aparência das linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0780-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d0780-103">Você pode controlar a aparência dos <xref:System.Windows.Forms.DataGridView> linhas manipulando uma ou ambas as <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="d0780-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="d0780-104">Esses eventos são projetados para que você pode pintar apenas o que você deseja enquanto permitindo que o <xref:System.Windows.Forms.DataGridView> controle pintará o restante.</span><span class="sxs-lookup"><span data-stu-id="d0780-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="d0780-105">Por exemplo, se você desejar pintar um plano de fundo personalizado, você pode manipular o <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> eventos e permitem que as células individuais pintar seus próprio conteúdo em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="d0780-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="d0780-106">Como alternativa, você pode permitir que as células se pintarem e adicione o conteúdo do primeiro plano personalizado em um manipulador para o <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="d0780-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="d0780-107">Você também pode desabilitar a pintura da célula e pintar tudo por conta própria em uma <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="d0780-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="d0780-108">O exemplo de código a seguir implementa manipuladores para ambos os eventos a fim de fornecer uma tela de fundo de seleção do gradiente e algum conteúdo de primeiro plano personalizado que abrange várias colunas.</span><span class="sxs-lookup"><span data-stu-id="d0780-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0780-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0780-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0780-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d0780-110">Compiling the Code</span></span>  
 <span data-ttu-id="d0780-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d0780-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d0780-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d0780-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d0780-113">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d0780-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d0780-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="d0780-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="d0780-115">Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d0780-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0780-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0780-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="d0780-117">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0780-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d0780-118">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0780-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
