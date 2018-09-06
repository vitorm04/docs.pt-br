---
title: Como criar um controle DataGridView dos Windows Forms não associados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 0441f0ce1005c82ae7ea9a0daecb3ec7ff41f59b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745707"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="f6f44-102">Como criar um controle DataGridView dos Windows Forms não associados</span><span class="sxs-lookup"><span data-stu-id="f6f44-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f6f44-103">O exemplo de código a seguir demonstra como preencher um <xref:System.Windows.Forms.DataGridView> controle programaticamente sem associação a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="f6f44-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="f6f44-104">Isso é útil quando você tem uma pequena quantidade de dados que você deseja exibir em um formato de tabela.</span><span class="sxs-lookup"><span data-stu-id="f6f44-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="f6f44-105">Para obter uma explicação completa sobre este exemplo de código, consulte [instruções passo a passo: Criando um controle DataGridView não associado do Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f6f44-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f44-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6f44-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6f44-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f6f44-107">Compiling the Code</span></span>  
 <span data-ttu-id="f6f44-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f6f44-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f6f44-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f6f44-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f6f44-110">Para obter informações sobre como compilar este exemplo de linha de comando do visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f6f44-110">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f6f44-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="f6f44-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f6f44-112">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f6f44-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f44-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6f44-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="f6f44-114">Instruções passo a passo: criando um controle DataGridView não associado do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6f44-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f6f44-115">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6f44-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f6f44-116">Modos de exibição dos dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6f44-116">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
