---
title: 'Como: Gerar automaticamente colunas em um controle DataGridView associado a dados do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: eb74c1ef1661fc8bd7a57f079f10d24a7eef8187
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639759"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="78fb5-102">Como: Gerar automaticamente colunas em um controle DataGridView associado a dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78fb5-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="78fb5-103">O exemplo de código a seguir demonstra como exibir as colunas da fonte de dados associados em um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="78fb5-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="78fb5-104">Quando o <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> é o valor da propriedade `true` (o padrão), um <xref:System.Windows.Forms.DataGridViewColumn> é criado para cada coluna na tabela de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="78fb5-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="78fb5-105">Se o <xref:System.Windows.Forms.DataGridView> controle já tem colunas quando você definir o <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> propriedade, o limite existente colunas são comparadas com as colunas na fonte de dados e preservadas sempre que houver uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="78fb5-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="78fb5-106">Colunas não associadas sempre são preservadas.</span><span class="sxs-lookup"><span data-stu-id="78fb5-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="78fb5-107">As colunas associadas para as quais não há nenhuma correspondência na fonte de dados são removidas.</span><span class="sxs-lookup"><span data-stu-id="78fb5-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="78fb5-108">Colunas da fonte de dados para o qual não há nenhuma correspondência no controle geram novos <xref:System.Windows.Forms.DataGridViewColumn> objetos, que são adicionados ao final do <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="78fb5-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78fb5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78fb5-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78fb5-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="78fb5-110">Compiling the Code</span></span>  
 <span data-ttu-id="78fb5-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="78fb5-111">This example requires:</span></span>  
  
- <span data-ttu-id="78fb5-112">Um controle <xref:System.Windows.Forms.DataGridView> chamado `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="78fb5-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="78fb5-113">Um <xref:System.Data.DataSet> objeto nomeado `customersDataSet` que tem uma tabela chamada `Customers`.</span><span class="sxs-lookup"><span data-stu-id="78fb5-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="78fb5-114">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, e <xref:System.Xml?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="78fb5-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fb5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78fb5-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="78fb5-116">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78fb5-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="78fb5-117">Como: Remover colunas geradas automaticamente de um controle de DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78fb5-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
