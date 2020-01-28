---
title: Criar um controle DataGridView não associado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 0b477eba6d8455554d72dc7ec8cfce68a91add38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730995"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="bb850-102">Como criar um controle DataGridView dos Windows Forms não associados</span><span class="sxs-lookup"><span data-stu-id="bb850-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bb850-103">O exemplo de código a seguir demonstra como popular um controle de <xref:System.Windows.Forms.DataGridView> programaticamente sem associá-lo a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="bb850-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="bb850-104">Isso é útil quando você tem uma pequena quantidade de dados que deseja exibir em um formato de tabela.</span><span class="sxs-lookup"><span data-stu-id="bb850-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="bb850-105">Para obter uma explicação completa deste exemplo de código, consulte [Walkthrough: Criando um controle Windows Forms DataGridView não associado](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bb850-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb850-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb850-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb850-107">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="bb850-107">Compiling the Code</span></span>  
 <span data-ttu-id="bb850-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bb850-108">This example requires:</span></span>  
  
- <span data-ttu-id="bb850-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="bb850-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb850-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="bb850-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="bb850-111">Instruções passo a passo: criando um controle DataGridView não associado do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb850-111">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bb850-112">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb850-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bb850-113">Modos de exibição de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb850-113">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
