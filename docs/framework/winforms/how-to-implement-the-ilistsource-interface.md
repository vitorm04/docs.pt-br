---
title: 'Como: implementar a interface IListSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: bd4e554b7e4be51847496307b50be3084d0115d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159777"
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="6d7e2-102">Como: implementar a interface IListSource</span><span class="sxs-lookup"><span data-stu-id="6d7e2-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="6d7e2-103">Implementar o <xref:System.ComponentModel.IListSource> interface para criar uma classe vinculável que não implementa <xref:System.Collections.IList> , mas em vez disso, fornece uma lista de outro local.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7e2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d7e2-104">Example</span></span>  
 <span data-ttu-id="6d7e2-105">O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.IListSource> interface.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="6d7e2-106">Um componente chamado `EmployeeListSource` expõe uma <xref:System.Collections.IList> para vinculação de dados Implementando o <xref:System.ComponentModel.IListSource.GetList%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d7e2-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6d7e2-107">Compiling the Code</span></span>  
 <span data-ttu-id="6d7e2-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6d7e2-108">This example requires:</span></span>  
  
-   <span data-ttu-id="6d7e2-109">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6d7e2-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7e2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d7e2-110">See also</span></span>

- <xref:System.ComponentModel.IListSource>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="6d7e2-111">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d7e2-111">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
