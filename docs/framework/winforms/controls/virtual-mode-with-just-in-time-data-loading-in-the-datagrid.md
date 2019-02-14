---
title: 'Como: Implementar o modo Virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: 473b2ebab95c26d8df03efc9edf332c56fb7e0e0
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261668"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="90669-102">Como: Implementar o modo Virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90669-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="90669-103">O exemplo de código a seguir mostra como usar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle com um cache de dados que carrega dados de um servidor somente quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="90669-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="90669-104">Este exemplo é descrito detalhadamente no [Implementando o modo Virtual com carregamento de dados just-in-no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="90669-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90669-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90669-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90669-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="90669-106">Compiling the Code</span></span>  
 <span data-ttu-id="90669-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="90669-107">This example requires:</span></span>  
  
-   <span data-ttu-id="90669-108">Referências aos assemblies System, System. Data, System. XML e System.</span><span class="sxs-lookup"><span data-stu-id="90669-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="90669-109">Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server instalado.</span><span class="sxs-lookup"><span data-stu-id="90669-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
 <span data-ttu-id="90669-110">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="90669-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="90669-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="90669-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="90669-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90669-112">.NET Framework Security</span></span>  
 <span data-ttu-id="90669-113">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="90669-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="90669-114">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="90669-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="90669-115">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="90669-115">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90669-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90669-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="90669-117">Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90669-117">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="90669-118">Ajuste de desempenho no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90669-118">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="90669-119">Modo virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90669-119">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
