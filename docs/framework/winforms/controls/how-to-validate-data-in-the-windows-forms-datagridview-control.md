---
title: Como validar dados no controle DataGridView dos Windows Forms
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
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e608bae5c18fade8cf8432c2c5e1fbe305740c1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7dcb9-102">Como validar dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7dcb9-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7dcb9-103">O exemplo de código a seguir demonstra como validar dados inseridos por um usuário em um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7dcb9-104">Neste exemplo, o <xref:System.Windows.Forms.DataGridView> é preenchida com linhas do `Customers` tabela do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="7dcb9-105">Quando o usuário edita uma célula a `CompanyName` coluna, seu valor é testada quanto à validade, verificando se ela não está vazia.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="7dcb9-106">Se o manipulador de eventos para o <xref:System.Windows.Forms.DataGridView.CellValidating> evento localiza o valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impede que o usuário sair da célula até que uma cadeia de caracteres não vazia é inserida.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="7dcb9-107">Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: validando dados em controle de DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7dcb9-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dcb9-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7dcb9-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7dcb9-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7dcb9-109">Compiling the Code</span></span>  
 <span data-ttu-id="7dcb9-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7dcb9-110">This example requires:</span></span>  
  
-   <span data-ttu-id="7dcb9-111">Referências aos assemblies System, System. Data, System e System. XML.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="7dcb9-112">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7dcb9-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7dcb9-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="7dcb9-114">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7dcb9-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7dcb9-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7dcb9-115">.NET Framework Security</span></span>  
 <span data-ttu-id="7dcb9-116">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="7dcb9-117">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="7dcb9-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="7dcb9-118">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="7dcb9-118">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcb9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dcb9-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="7dcb9-120">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7dcb9-120">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7dcb9-121">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7dcb9-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7dcb9-122">Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7dcb9-122">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="7dcb9-123">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="7dcb9-123">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
