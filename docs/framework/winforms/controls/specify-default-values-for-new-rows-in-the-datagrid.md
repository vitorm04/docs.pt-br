---
title: 'Como: Especificar valores padrão para novas linhas no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193688"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a7f5c-102">Como: Especificar valores padrão para novas linhas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7f5c-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a7f5c-103">Você pode fazer mais conveniente a entrada de dados quando o aplicativo em default preenche os valores para linhas recém-adicionadas.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="a7f5c-104">Com o <xref:System.Windows.Forms.DataGridView> classe, você pode preencher em default valores com o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> eventos.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="a7f5c-105">Esse evento é gerado quando o usuário insere a linha para novos registros.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="a7f5c-106">Quando seu código manipula esse evento, você pode preencher desejadas células com valores de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="a7f5c-107">O exemplo de código a seguir demonstra como especificar valores padrão para novas linhas usando o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> eventos.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f5c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7f5c-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7f5c-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a7f5c-109">Compiling the Code</span></span>  
 <span data-ttu-id="a7f5c-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a7f5c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="a7f5c-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="a7f5c-112">Um `NewCustomerId` função para gerar exclusivo `CustomerID` valores.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="a7f5c-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a7f5c-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f5c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7f5c-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="a7f5c-115">Entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7f5c-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a7f5c-116">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7f5c-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
