---
title: Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de75d4d3d8de34bc85ee47b6761724da93fc0ecc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="94916-102">Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="94916-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="94916-103">O <xref:System.Windows.Forms.BindingSource> componente detectará automaticamente as alterações em uma fonte de dados quando o tipo contido de fonte de dados implementa a <xref:System.ComponentModel.INotifyPropertyChanged> interface e gera <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos quando um valor de propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="94916-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="94916-104">Isso é útil porque os controles associados para o <xref:System.Windows.Forms.BindingSource> , em seguida, será atualizado automaticamente como a alteração de valores de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="94916-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94916-105">Se sua fonte de dados implementa <xref:System.ComponentModel.INotifyPropertyChanged> e você estiver executando operações assíncronas, você não deve fazer alterações à fonte de dados em um thread em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="94916-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="94916-106">Em vez disso, você deve ler os dados em um thread em segundo plano e mesclar os dados em uma lista no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="94916-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94916-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94916-107">Example</span></span>  
 <span data-ttu-id="94916-108">O exemplo de código a seguir demonstra uma implementação simples do <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="94916-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="94916-109">Ele também mostra como o <xref:System.Windows.Forms.BindingSource> passa automaticamente uma alteração de fonte de dados para uma associação de controle quando o <xref:System.Windows.Forms.BindingSource> está associado a uma lista da <xref:System.ComponentModel.INotifyPropertyChanged> tipo.</span><span class="sxs-lookup"><span data-stu-id="94916-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="94916-110">Se você usar o atributo `CallerMemberName`, chamadas para o método `NotifyPropertyChanged` não precisarão especificar o nome da propriedade como um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="94916-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="94916-111">Para obter mais informações, consulte [Informações do chamador](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span><span class="sxs-lookup"><span data-stu-id="94916-111">For more information, see [Caller Information](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94916-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="94916-112">Compiling the Code</span></span>  
 <span data-ttu-id="94916-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="94916-113">This example requires:</span></span>  
  
-   <span data-ttu-id="94916-114">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="94916-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="94916-115">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94916-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="94916-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="94916-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="94916-117">Consulte também [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" como: compilar e executar uma completa Windows Forms código de exemplo com o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="94916-117">Also see [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94916-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94916-118">See Also</span></span>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [<span data-ttu-id="94916-119">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="94916-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="94916-120">Como acionar notificações de alteração usando o método BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="94916-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
