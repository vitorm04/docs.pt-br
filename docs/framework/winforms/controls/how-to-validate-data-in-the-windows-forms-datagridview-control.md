---
title: 'Como: Validar dados no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: 12fd668e22703271f8c629baf56487dd084cfd8b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591039"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9c6ab-102">Como: Validar dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c6ab-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9c6ab-103">O exemplo de código a seguir demonstra como validar dados inseridos por um usuário em um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9c6ab-104">Neste exemplo, o <xref:System.Windows.Forms.DataGridView> é preenchida com linhas do `Customers` tabela do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="9c6ab-105">Quando o usuário edita uma célula no `CompanyName` coluna, seu valor é testada quanto à validade, verificando se ele não está vazio.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="9c6ab-106">Se o manipulador de eventos para o <xref:System.Windows.Forms.DataGridView.CellValidating> evento localiza que o valor é uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impede que o usuário sair da célula até que uma cadeia de caracteres não vazia seja inserida.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="9c6ab-107">Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: Validando dados em que o Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9c6ab-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c6ab-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c6ab-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c6ab-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9c6ab-109">Compiling the Code</span></span>  
 <span data-ttu-id="9c6ab-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9c6ab-110">This example requires:</span></span>  
  
- <span data-ttu-id="9c6ab-111">Referências aos assemblies System, System. Data, System e System. XML.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9c6ab-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c6ab-112">.NET Framework Security</span></span>  
 <span data-ttu-id="9c6ab-113">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9c6ab-114">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9c6ab-115">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9c6ab-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6ab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c6ab-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="9c6ab-117">Passo a passo: Validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c6ab-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9c6ab-118">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c6ab-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9c6ab-119">Passo a passo: Tratamento de erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c6ab-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="9c6ab-120">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="9c6ab-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
