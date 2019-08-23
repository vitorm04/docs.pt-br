---
title: 'Como: Como personalizar a adição de item com o BindingSource do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935358"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="b49e4-102">Como: Como personalizar a adição de item com o BindingSource do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b49e4-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="b49e4-103">Quando você usa um <xref:System.Windows.Forms.BindingSource> componente para associar um controle de Windows Forms a uma fonte de dados, pode ser necessário personalizar a criação de novos itens.</span><span class="sxs-lookup"><span data-stu-id="b49e4-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="b49e4-104">O <xref:System.Windows.Forms.BindingSource> componente torna isso simples fornecendo o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que normalmente é gerado quando o controle ligado precisa criar um novo item.</span><span class="sxs-lookup"><span data-stu-id="b49e4-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="b49e4-105">O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).</span><span class="sxs-lookup"><span data-stu-id="b49e4-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b49e4-106">Quando um item é adicionado manipulando o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, a adição não pode ser cancelada.</span><span class="sxs-lookup"><span data-stu-id="b49e4-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b49e4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b49e4-107">Example</span></span>  
 <span data-ttu-id="b49e4-108">O exemplo a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle a uma fábrica de classes usando um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="b49e4-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b49e4-109">Quando o usuário clica na <xref:System.Windows.Forms.DataGridView> nova linha do controle, o <xref:System.Windows.Forms.BindingSource.AddingNew> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="b49e4-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="b49e4-110">O manipulador de eventos cria um `DemoCustomer` novo objeto, que é atribuído <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> à propriedade.</span><span class="sxs-lookup"><span data-stu-id="b49e4-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b49e4-111">Isso faz com que `DemoCustomer` o novo objeto seja adicionado <xref:System.Windows.Forms.BindingSource> à lista do componente e seja exibido na nova linha do <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="b49e4-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b49e4-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b49e4-112">Compiling the Code</span></span>  
 <span data-ttu-id="b49e4-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b49e4-113">This example requires:</span></span>  
  
- <span data-ttu-id="b49e4-114">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b49e4-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49e4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b49e4-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b49e4-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="b49e4-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b49e4-117">Como: Associar um controle de Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="b49e4-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
