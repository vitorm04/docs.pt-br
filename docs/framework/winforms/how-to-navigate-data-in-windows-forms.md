---
title: Como navegar por dados no Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99d794164307cb22c5dfc89d6c9c227aa457a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="b002e-102">Como navegar por dados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b002e-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="b002e-103">Em um aplicativo do Windows, a maneira mais fácil de navegar por meio de registros em uma fonte de dados é associar um <xref:System.Windows.Forms.BindingSource> componente para a fonte de dados e controles de associação para o <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="b002e-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="b002e-104">Você pode usar o método de navegação internos no <xref:System.Windows.Forms.BindingSource> tais um <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> e <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="b002e-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="b002e-105">Usar esses métodos ajustará o <xref:System.Windows.Forms.BindingSource.Position%2A> e <xref:System.Windows.Forms.BindingSource.Current%2A> propriedades do <xref:System.Windows.Forms.BindingSource> adequadamente.</span><span class="sxs-lookup"><span data-stu-id="b002e-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="b002e-106">Você também pode localizar um item e defina-o como o item atual, definindo o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b002e-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="b002e-107">Incrementar a posição em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="b002e-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="b002e-108">Definir o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade o <xref:System.Windows.Forms.BindingSource> para seus dados associados para a posição do registro para ir para.</span><span class="sxs-lookup"><span data-stu-id="b002e-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="b002e-109">O exemplo a seguir ilustra o uso de <xref:System.Windows.Forms.BindingSource.MoveNext%2A> método do <xref:System.Windows.Forms.BindingSource> para incrementar o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade quando o `nextButton` é clicado.</span><span class="sxs-lookup"><span data-stu-id="b002e-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="b002e-110">O <xref:System.Windows.Forms.BindingSource> está associado a `Customers` tabela de um conjunto de dados `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="b002e-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b002e-111">Definindo o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade para um valor para o primeiro ou último registro acima não resultar em um erro, como o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não permitirá que você defina a posição para um valor fora dos limites da lista.</span><span class="sxs-lookup"><span data-stu-id="b002e-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="b002e-112">Se, no aplicativo, for importante saber se você passou do primeiro ou do último registro, inclua a lógica para testar se a contagem de elementos de dados será excedida.</span><span class="sxs-lookup"><span data-stu-id="b002e-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="b002e-113">Verificar se você passou do final ou do início</span><span class="sxs-lookup"><span data-stu-id="b002e-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="b002e-114">Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.BindingSource.PositionChanged>.</span><span class="sxs-lookup"><span data-stu-id="b002e-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="b002e-115">No manipulador, é possível testar se o valor da posição proposta excedeu a contagem de elementos de dados real.</span><span class="sxs-lookup"><span data-stu-id="b002e-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="b002e-116">O exemplo a seguir ilustra como testar se o último elemento de dados foi alcançado.</span><span class="sxs-lookup"><span data-stu-id="b002e-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="b002e-117">No exemplo, se você estiver no último elemento, o botão **Próximo** do formulário estará desabilitado.</span><span class="sxs-lookup"><span data-stu-id="b002e-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b002e-118">Lembre-se de que é necessário alterar a lista em que você está navegando no código, reabilite o botão **Próximo**, para que os usuários possam pesquisar a totalidade da nova lista.</span><span class="sxs-lookup"><span data-stu-id="b002e-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="b002e-119">Além disso, lembre-se que as opções acima <xref:System.Windows.Forms.BindingSource.PositionChanged> evento específicas <xref:System.Windows.Forms.BindingSource> você estiver trabalhando com precisa ser associado com seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="b002e-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="b002e-120">A seguir está um exemplo de um método para tratar o <xref:System.Windows.Forms.BindingSource.PositionChanged> evento:</span><span class="sxs-lookup"><span data-stu-id="b002e-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="b002e-121">Localizar um item e defini-lo como o item atual</span><span class="sxs-lookup"><span data-stu-id="b002e-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="b002e-122">Localize o registro que deseja definir como o item atual.</span><span class="sxs-lookup"><span data-stu-id="b002e-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="b002e-123">Você pode fazer isso usando o <xref:System.Windows.Forms.BindingSource.Find%2A> método o <xref:System.Windows.Forms.BindingSource>, se sua fonte de dados implementa <xref:System.ComponentModel.IBindingList>.</span><span class="sxs-lookup"><span data-stu-id="b002e-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="b002e-124">Alguns exemplos de dados de fontes que implementam <xref:System.ComponentModel.IBindingList> são <xref:System.ComponentModel.BindingList%601> e <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="b002e-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b002e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b002e-125">See Also</span></span>  
 [<span data-ttu-id="b002e-126">Fontes de dados com suporte nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b002e-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="b002e-127">Notificação de alteração na vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b002e-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="b002e-128">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b002e-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="b002e-129">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b002e-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
