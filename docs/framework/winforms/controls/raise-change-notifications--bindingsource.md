---
title: Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739688"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="efae1-102">Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="efae1-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="efae1-103">O <xref:System.Windows.Forms.BindingSource> componente detecta automaticamente alterações em uma fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> quando <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> o tipo contido na fonte de dados implementa e levanta eventos quando um valor de propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="efae1-103">The <xref:System.Windows.Forms.BindingSource> component automatically detects changes in a data source when the type contained in the data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="efae1-104">Essa detecção de alteração é <xref:System.Windows.Forms.BindingSource> útil porque os controles vinculados à atualização automática à medida que os valores de origem de dados mudam.</span><span class="sxs-lookup"><span data-stu-id="efae1-104">This change detection is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efae1-105">Se a sua <xref:System.ComponentModel.INotifyPropertyChanged> fonte de dados for implementada e você estiver realizando operações assíncronas, você não deve fazer alterações na fonte de dados em um segmento de fundo.</span><span class="sxs-lookup"><span data-stu-id="efae1-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="efae1-106">Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="efae1-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efae1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="efae1-107">Example</span></span>  
 <span data-ttu-id="efae1-108">O exemplo de código a <xref:System.ComponentModel.INotifyPropertyChanged> seguir demonstra uma implementação simples da interface.</span><span class="sxs-lookup"><span data-stu-id="efae1-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="efae1-109">Ele também mostra <xref:System.Windows.Forms.BindingSource> como a mudança de origem de <xref:System.Windows.Forms.BindingSource> dados passa automaticamente para <xref:System.ComponentModel.INotifyPropertyChanged> um controle vinculado quando está vinculado a uma lista do tipo.</span><span class="sxs-lookup"><span data-stu-id="efae1-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="efae1-110">Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="efae1-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="efae1-111">Para obter mais informações, consulte [Informações do chamador (C#)](../../../csharp/language-reference/attributes/caller-information.md) ou [Informações do Chamador (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="efae1-111">For more information, see [Caller Information (C#)](../../../csharp/language-reference/attributes/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="efae1-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="efae1-112">Compiling the Code</span></span>  
 <span data-ttu-id="efae1-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="efae1-113">This example requires:</span></span>  
  
- <span data-ttu-id="efae1-114">Referências aos conjuntos System,Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="efae1-114">References to the System, System.Data, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efae1-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="efae1-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="efae1-116">Componente de origem de vinculação</span><span class="sxs-lookup"><span data-stu-id="efae1-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="efae1-117">Como gerar notificações de alteração usando o método BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="efae1-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
