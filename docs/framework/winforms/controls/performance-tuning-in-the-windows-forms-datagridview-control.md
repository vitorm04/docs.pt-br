---
title: Ajuste de desempenho no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 79f74db4ebd095156207a6218f59c0e9ae423085
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012640"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a49d2-102">Ajuste de desempenho no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a49d2-103">Ao trabalhar com grandes quantidades de dados, o controle `DataGridView` pode consumir uma grande quantidade de memória em sobrecarga, a menos que você o utilize com cuidado.</span><span class="sxs-lookup"><span data-stu-id="a49d2-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="a49d2-104">Em clientes com memória limitada, é possível evitar um pouco dessa sobrecarga, evitando recursos que têm um custo de memória alto.</span><span class="sxs-lookup"><span data-stu-id="a49d2-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="a49d2-105">Você também pode gerenciar alguns ou todas as tarefas de manutenção e recuperação de dados usando o modo virtual para personalizar o uso de memória para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="a49d2-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a49d2-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a49d2-106">In This Section</span></span>  
 [<span data-ttu-id="a49d2-107">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a49d2-108">Descreve como usar o controle `DataGridView` de uma maneira que evite penalidades no desempenho e no uso de memória desnecessário ao trabalhar com grandes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="a49d2-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="a49d2-109">Modo virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a49d2-110">Descreve como usar o modo virtual para suplementar ou substituir o mecanismo de associação de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="a49d2-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="a49d2-111">Passo a passo: Implementando o modo Virtual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="a49d2-112">Descreve como implementar manipuladores para vários eventos no modo virtual.</span><span class="sxs-lookup"><span data-stu-id="a49d2-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="a49d2-113">Também demonstra como implementar a reversão de nível de linha e confirmar as edições do usuário.</span><span class="sxs-lookup"><span data-stu-id="a49d2-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="a49d2-114">Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="a49d2-115">Descreve como carregar dados sob demanda, que é útil quando você tem mais dados para exibir do que a memória de cliente disponível pode armazenar.</span><span class="sxs-lookup"><span data-stu-id="a49d2-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a49d2-116">Referência</span><span class="sxs-lookup"><span data-stu-id="a49d2-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a49d2-117">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="a49d2-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="a49d2-118">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a49d2-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49d2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a49d2-119">See also</span></span>

- [<span data-ttu-id="a49d2-120">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="a49d2-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="a49d2-121">Modos de exibição dos dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a49d2-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
