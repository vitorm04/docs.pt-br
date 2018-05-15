---
title: Como definir os modos de dimensionamento do controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 3d2ebb2b42a3e6558d5aedb207bdc4e2607d5270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="1104c-102">Como definir os modos de dimensionamento do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1104c-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1104c-103">Os procedimentos a seguir demonstram alguns cenários comuns que personalizam ou combinam as opções de dimensionamento disponíveis para o <xref:System.Windows.Forms.DataGridView> controle e para colunas específicas em um controle.</span><span class="sxs-lookup"><span data-stu-id="1104c-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="1104c-104">Para criar uma coluna de largura fixa</span><span class="sxs-lookup"><span data-stu-id="1104c-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="1104c-105">Definir o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriedade para <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, o <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> propriedade para <xref:System.Windows.Forms.DataGridViewTriState.False>, o <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> propriedade `true`e o <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> propriedade para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="1104c-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="1104c-106">Para criar uma coluna que ajusta seu tamanho para o conteúdo</span><span class="sxs-lookup"><span data-stu-id="1104c-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="1104c-107">Definir o <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> propriedade para um modo de dimensionamento com base em conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1104c-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="1104c-108">Para criar colunas de modo de preenchimento para valores de tamanho e importância variáveis</span><span class="sxs-lookup"><span data-stu-id="1104c-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="1104c-109">Definir o <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> para definir o modo de dimensionamento para todas as colunas que não substituir esse valor.</span><span class="sxs-lookup"><span data-stu-id="1104c-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="1104c-110">Definir o <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> larguras de conteúdo de propriedades das colunas para valores que serão proporcionais à sua média.</span><span class="sxs-lookup"><span data-stu-id="1104c-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="1104c-111">Definir o <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> propriedades das colunas importantes para garantir a exibição de conteúdo parcial.</span><span class="sxs-lookup"><span data-stu-id="1104c-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="1104c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1104c-112">Example</span></span>  
 <span data-ttu-id="1104c-113">O exemplo de código completo a seguir fornece um aplicativo de demonstração que pode ajudá-lo a entender as opções de dimensionamento descritas neste tópico.</span><span class="sxs-lookup"><span data-stu-id="1104c-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="1104c-114">Para usar esse aplicativo de demonstração:</span><span class="sxs-lookup"><span data-stu-id="1104c-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="1104c-115">Altere o tamanho do formulário.</span><span class="sxs-lookup"><span data-stu-id="1104c-115">Change the size of the form.</span></span> <span data-ttu-id="1104c-116">Observe como as colunas de modo de preenchimento alteram as larguras enquanto mantém as proporções indicado pelo <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1104c-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="1104c-117">Observe como uma coluna <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> impede a alteração quando o formulário é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="1104c-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="1104c-118">Altere os tamanhos das colunas arrastando os divisores de coluna com o mouse.</span><span class="sxs-lookup"><span data-stu-id="1104c-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="1104c-119">Observe como algumas colunas não podem ser redimensionadas e como as colunas redimensionáveis não podem ficar mais estreitas do que suas larguras mínimas.</span><span class="sxs-lookup"><span data-stu-id="1104c-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1104c-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1104c-120">Compiling the Code</span></span>  
 <span data-ttu-id="1104c-121">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1104c-121">This example requires:</span></span>  
  
-   <span data-ttu-id="1104c-122">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1104c-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1104c-123">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1104c-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1104c-124">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1104c-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1104c-125">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1104c-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1104c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1104c-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
