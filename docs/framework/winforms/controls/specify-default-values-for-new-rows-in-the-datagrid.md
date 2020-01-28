---
title: Especificar valores padrão para novas linhas no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742935"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1880f-102">Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1880f-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1880f-103">Você pode tornar a entrada de dados mais conveniente quando o aplicativo preenche valores padrão para linhas adicionadas recentemente.</span><span class="sxs-lookup"><span data-stu-id="1880f-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="1880f-104">Com a classe <xref:System.Windows.Forms.DataGridView>, você pode preencher valores padrão com o evento <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="1880f-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="1880f-105">Esse evento é gerado quando o usuário insere a linha para novos registros.</span><span class="sxs-lookup"><span data-stu-id="1880f-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="1880f-106">Quando seu código manipula esse evento, você pode preencher as células desejadas com os valores de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1880f-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="1880f-107">O exemplo de código a seguir demonstra como especificar valores padrão para novas linhas usando o evento <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="1880f-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1880f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1880f-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1880f-109">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="1880f-109">Compiling the Code</span></span>  
 <span data-ttu-id="1880f-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1880f-110">This example requires:</span></span>  
  
- <span data-ttu-id="1880f-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="1880f-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="1880f-112">Uma função `NewCustomerId` para gerar valores de `CustomerID` exclusivos.</span><span class="sxs-lookup"><span data-stu-id="1880f-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="1880f-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1880f-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1880f-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="1880f-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="1880f-115">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1880f-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1880f-116">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1880f-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
