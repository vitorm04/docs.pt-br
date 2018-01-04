---
title: "Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 227ad36e87c3deceb7fefe3cd19013fc8e76c686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="12d49-102">Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados</span><span class="sxs-lookup"><span data-stu-id="12d49-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="12d49-103">Muitas vezes, ao trabalhar com vinculação de dados nos Windows Forms, vários controles são associados à mesma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="12d49-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="12d49-104">Em alguns casos, pode ser necessário executar etapas adicionais para garantir que as propriedades associadas dos controles permaneçam sincronizadas entre si e à fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="12d49-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="12d49-105">Essas etapas são necessárias em duas situações:</span><span class="sxs-lookup"><span data-stu-id="12d49-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="12d49-106">Se a fonte de dados não implementa <xref:System.ComponentModel.IBindingList>e, portanto, gerar <xref:System.ComponentModel.IBindingList.ListChanged> eventos do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span><span class="sxs-lookup"><span data-stu-id="12d49-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="12d49-107">Se a fonte de dados implementa <xref:System.ComponentModel.IEditableObject>.</span><span class="sxs-lookup"><span data-stu-id="12d49-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="12d49-108">No primeiro caso, você pode usar um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados para os controles.</span><span class="sxs-lookup"><span data-stu-id="12d49-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="12d49-109">No último caso, você deve usar um <xref:System.Windows.Forms.BindingSource> e tratar o <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos e chamadas <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> em associado <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="12d49-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12d49-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12d49-110">Example</span></span>  
 <span data-ttu-id="12d49-111">O exemplo de código a seguir demonstra como associar controles dos três — dois controles de caixa de texto e um <xref:System.Windows.Forms.DataGridView> controle — para a mesma coluna em uma <xref:System.Data.DataSet> usando um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="12d49-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="12d49-112">Este exemplo demonstra como tratar o <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos e certifique-se de que quando o valor de texto de uma caixa de texto é alterado, a caixa de texto adicionais e o <xref:System.Windows.Forms.DataGridView> controle são atualizados com o valor correto.</span><span class="sxs-lookup"><span data-stu-id="12d49-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="12d49-113">O exemplo usa um <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados e os controles.</span><span class="sxs-lookup"><span data-stu-id="12d49-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="12d49-114">Como alternativa, você pode vincular os controles diretamente à fonte de dados e recuperar o <xref:System.Windows.Forms.BindingManagerBase> para a associação do formulário de <xref:System.Windows.Forms.Control.BindingContext%2A> e, em seguida, manipular o <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> eventos para o <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="12d49-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="12d49-115">Para obter um exemplo de como fazer isso, consulte a página de ajuda o <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> evento <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="12d49-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12d49-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="12d49-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="12d49-117">Este exemplo de código requer</span><span class="sxs-lookup"><span data-stu-id="12d49-117">This code example requires</span></span>  
  
-   <span data-ttu-id="12d49-118">Referências a <xref:System>, <xref:System.Windows.Forms>, e <xref:System.Drawing> assemblies.</span><span class="sxs-lookup"><span data-stu-id="12d49-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="12d49-119">Um formulário com o <xref:System.Windows.Forms.Form.Load> eventos manipulados e uma chamada para o `InitializeControlsAndDataSource` método no exemplo do formulário de <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="12d49-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d49-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12d49-120">See Also</span></span>  
 [<span data-ttu-id="12d49-121">Como compartilhar dados associados entre formulários usando o componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="12d49-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="12d49-122">Notificação de alteração na vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12d49-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="12d49-123">Interfaces relacionadas à vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="12d49-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="12d49-124">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12d49-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
