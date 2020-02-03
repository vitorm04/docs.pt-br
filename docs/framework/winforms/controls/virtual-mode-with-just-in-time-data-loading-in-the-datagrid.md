---
title: Implementar o modo virtual com o carregamento de dados Just-in-time no controle DataGridView
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
ms.openlocfilehash: bbe98d3c317a7625b36b729f0be23ea20f65dec0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745428"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a74d5-102">Como implementar o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a74d5-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a74d5-103">O exemplo de código a seguir mostra como usar o modo virtual no controle de <xref:System.Windows.Forms.DataGridView> com um cache de dados que carrega dados de um servidor somente quando ele é necessário.</span><span class="sxs-lookup"><span data-stu-id="a74d5-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="a74d5-104">Este exemplo é descrito em detalhes na [implementação do modo virtual com carregamento de dados Just-in-time no controle Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a74d5-105">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a74d5-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a74d5-106">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="a74d5-106">Compiling the Code</span></span>  
 <span data-ttu-id="a74d5-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a74d5-107">This example requires:</span></span>  
  
- <span data-ttu-id="a74d5-108">Referências aos assemblies sistema, System. Data, System. xml e System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="a74d5-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="a74d5-109">Acesso a um servidor com o banco de dados Northwind SQL Server exemplo instalado.</span><span class="sxs-lookup"><span data-stu-id="a74d5-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a74d5-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a74d5-110">.NET Framework Security</span></span>  
 <span data-ttu-id="a74d5-111">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a74d5-111">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="a74d5-112">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a74d5-112">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="a74d5-113">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="a74d5-113">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74d5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a74d5-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="a74d5-115">Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a74d5-115">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="a74d5-116">Ajuste de desempenho no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a74d5-116">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a74d5-117">Modo virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a74d5-117">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
