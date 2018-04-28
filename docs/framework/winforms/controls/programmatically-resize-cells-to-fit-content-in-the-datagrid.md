---
title: Como redimensionar de forma programática as células para que o conteúdo caiba no controle DataGridView dos Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e392e46b257fa7ef9b6bde3b5d6bb7274aaa01e6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1fcaf-102">Como redimensionar de forma programática as células para que o conteúdo caiba no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fcaf-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1fcaf-103">Você pode usar o <xref:System.Windows.Forms.DataGridView> controlar os métodos para redimensionar linhas, colunas e cabeçalhos para que eles exibam seus valores inteiros sem truncamento.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="1fcaf-104">Você pode usar estes métodos para redimensionar <xref:System.Windows.Forms.DataGridView> elementos às vezes de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="1fcaf-105">Como alternativa, você pode configurar o controle para redimensionar esses elementos automaticamente sempre que o conteúdo é alterado.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="1fcaf-106">No entanto, isso pode ser ineficiente quando você estiver trabalhando com grandes conjuntos de dados ou quando seus dados forem alterados com frequência.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="1fcaf-107">Para obter mais informações, consulte [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="1fcaf-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="1fcaf-108">Normalmente, você irá ajustar programaticamente <xref:System.Windows.Forms.DataGridView> elementos de acordo com seu conteúdo somente quando você carrega novos dados de uma fonte de dados ou quando o usuário tiver editado um valor.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="1fcaf-109">Isso é útil para otimizar o desempenho, mas também é útil quando desejar permitir que os usuários redimensionem manualmente linhas e colunas com o mouse.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="1fcaf-110">O exemplo de código a seguir demonstra as opções disponíveis para o redimensionamento programático.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fcaf-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fcaf-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1fcaf-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1fcaf-112">Compiling the Code</span></span>  
 <span data-ttu-id="1fcaf-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1fcaf-113">This example requires:</span></span>  
  
-   <span data-ttu-id="1fcaf-114">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1fcaf-115">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1fcaf-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1fcaf-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1fcaf-117">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1fcaf-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fcaf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fcaf-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [<span data-ttu-id="1fcaf-119">Redimensionando colunas e linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fcaf-119">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1fcaf-120">[Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1fcaf-120">[Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)</span></span>  
 [<span data-ttu-id="1fcaf-121">Como redimensionar automaticamente células quando o conteúdo é alterado no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fcaf-121">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)
