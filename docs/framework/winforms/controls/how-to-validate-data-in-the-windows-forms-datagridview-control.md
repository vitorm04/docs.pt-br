---
title: Validar dados no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728311"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b5f0c-102">Como validar dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5f0c-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b5f0c-103">O exemplo de código a seguir demonstra como validar dados inseridos por um usuário em um controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b5f0c-104">Neste exemplo, a <xref:System.Windows.Forms.DataGridView> é preenchida com linhas da tabela `Customers` do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="b5f0c-105">Quando o usuário edita uma célula na coluna `CompanyName`, seu valor é testado quanto à validade, verificando se ela não está vazia.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="b5f0c-106">Se o manipulador de eventos para o evento <xref:System.Windows.Forms.DataGridView.CellValidating> descobrir que o valor é uma cadeia de caracteres vazia, a <xref:System.Windows.Forms.DataGridView> impede que o usuário saia da célula até que uma cadeia de caracteres não vazia seja inserida.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="b5f0c-107">Para obter uma explicação completa deste exemplo de código, consulte [Walkthrough: Validando dados no controle Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5f0c-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f0c-108">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b5f0c-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5f0c-109">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="b5f0c-109">Compiling the Code</span></span>  
 <span data-ttu-id="b5f0c-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b5f0c-110">This example requires:</span></span>  
  
- <span data-ttu-id="b5f0c-111">Referências ao sistema, System. Data, System. Windows. Forms e assemblies System. XML.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b5f0c-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5f0c-112">.NET Framework Security</span></span>  
 <span data-ttu-id="b5f0c-113">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="b5f0c-114">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b5f0c-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="b5f0c-115">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="b5f0c-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f0c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f0c-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b5f0c-117">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5f0c-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b5f0c-118">Entrada de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5f0c-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b5f0c-119">Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5f0c-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="b5f0c-120">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="b5f0c-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
