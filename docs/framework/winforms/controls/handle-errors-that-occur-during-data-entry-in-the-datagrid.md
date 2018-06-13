---
title: Como identificar erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 871a1df104310b8fbe718cc4d61e382663961b9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527255"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e4c69-102">Como identificar erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4c69-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e4c69-103">O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.DataGridView> controle para relatar erros de entrada de dados para o usuário.</span><span class="sxs-lookup"><span data-stu-id="e4c69-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="e4c69-104">Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: Manipulando erros que ocorrem durante a entrada de dados no controle de DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="e4c69-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c69-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c69-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4c69-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e4c69-106">Compiling the Code</span></span>  
 <span data-ttu-id="e4c69-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e4c69-107">This example requires:</span></span>  
  
-   <span data-ttu-id="e4c69-108">Referências aos assemblies System, System.Data, System.Windows.Forms e System.XML.</span><span class="sxs-lookup"><span data-stu-id="e4c69-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="e4c69-109">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e4c69-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e4c69-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e4c69-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e4c69-111">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e4c69-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e4c69-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e4c69-112">.NET Framework Security</span></span>  
 <span data-ttu-id="e4c69-113">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4c69-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e4c69-114">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e4c69-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e4c69-115">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e4c69-115">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c69-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c69-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="e4c69-117">Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4c69-117">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="e4c69-118">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4c69-118">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e4c69-119">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4c69-119">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e4c69-120">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="e4c69-120">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
