---
title: Como implementar a interface ITypedList
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
ms.openlocfilehash: 181879d3e41e0dd140c79a4c63d52e6999acf86d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="b39a6-102">Como implementar a interface ITypedList</span><span class="sxs-lookup"><span data-stu-id="b39a6-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="b39a6-103">Implementar o <xref:System.ComponentModel.ITypedList> interface para habilitar a descoberta do esquema para obter uma lista associável.</span><span class="sxs-lookup"><span data-stu-id="b39a6-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39a6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b39a6-104">Example</span></span>  
 <span data-ttu-id="b39a6-105">O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.ITypedList> interface.</span><span class="sxs-lookup"><span data-stu-id="b39a6-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="b39a6-106">Um tipo genérico chamado `SortableBindingList` deriva o <xref:System.ComponentModel.BindingList%601> classe e implemente o <xref:System.ComponentModel.ITypedList> interface.</span><span class="sxs-lookup"><span data-stu-id="b39a6-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="b39a6-107">Uma classe simples denominada `Customer` fornece dados, que são associados ao cabeçalho de uma <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="b39a6-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b39a6-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b39a6-108">Compiling the Code</span></span>  
 <span data-ttu-id="b39a6-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b39a6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="b39a6-110">Referências aos assemblies System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b39a6-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39a6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b39a6-111">See Also</span></span>  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [<span data-ttu-id="b39a6-112">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b39a6-112">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
