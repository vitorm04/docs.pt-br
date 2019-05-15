---
title: 'Como: Gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged'
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
ms.openlocfilehash: 6a622e64076d2ed2a073dc0f0e55204d1767cfd7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591827"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="41783-102">Como: Gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="41783-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="41783-103">O <xref:System.Windows.Forms.BindingSource> componente detectará automaticamente as alterações em uma fonte de dados quando o tipo contido de fonte de dados implementa a <xref:System.ComponentModel.INotifyPropertyChanged> interface e gera <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos quando um valor da propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="41783-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="41783-104">Isso é útil porque os controles associados ao <xref:System.Windows.Forms.BindingSource> , em seguida, atualizará automaticamente como sendo a alteração de valores de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="41783-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41783-105">Se a fonte de dados implementa <xref:System.ComponentModel.INotifyPropertyChanged> e você estiver executando operações assíncronas, você não deve fazer alterações à fonte de dados em um thread em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="41783-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="41783-106">Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="41783-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41783-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41783-107">Example</span></span>  
 <span data-ttu-id="41783-108">O exemplo de código a seguir demonstra uma implementação simples dos <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="41783-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="41783-109">Ele também mostra como o <xref:System.Windows.Forms.BindingSource> passa automaticamente uma alteração de fonte de dados para um limite controlar quando o <xref:System.Windows.Forms.BindingSource> está associado a uma lista da <xref:System.ComponentModel.INotifyPropertyChanged> tipo.</span><span class="sxs-lookup"><span data-stu-id="41783-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="41783-110">Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="41783-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="41783-111">Para obter mais informações, consulte [informações do chamador (C#)](../../../csharp/programming-guide/concepts/caller-information.md) ou [informações do chamador (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="41783-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41783-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="41783-112">Compiling the Code</span></span>  
 <span data-ttu-id="41783-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="41783-113">This example requires:</span></span>  
  
- <span data-ttu-id="41783-114">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="41783-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41783-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41783-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="41783-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="41783-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="41783-117">Como: Gerar notificações de alteração usando o método BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="41783-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
