---
title: Refletir atualizações de fonte de dados no controle com BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: f98296b477dbb674cdbdbd8d03e291dd6ca0c8a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742442"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="74b6d-102">Como refletir atualizações feitas na fonte de dados em um controle dos Windows Forms com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="74b6d-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="74b6d-103">Ao usar controles vinculados a dados, às vezes você precisa responder às alterações na fonte de dados quando a fonte de dados não gerar eventos de alteração de lista.</span><span class="sxs-lookup"><span data-stu-id="74b6d-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="74b6d-104">Ao usar o componente <xref:System.Windows.Forms.BindingSource> para associar a fonte de dados a um controle de Windows Forms, você pode notificar o controle de que sua fonte de dados foi alterada chamando o método <xref:System.Windows.Forms.BindingSource.ResetBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="74b6d-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74b6d-105">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="74b6d-105">Example</span></span>  
 <span data-ttu-id="74b6d-106">O exemplo de código a seguir demonstra o uso do método <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> para notificar um controle ligado sobre uma atualização na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="74b6d-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74b6d-107">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="74b6d-107">Compiling the Code</span></span>  
 <span data-ttu-id="74b6d-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="74b6d-108">This example requires:</span></span>  
  
- <span data-ttu-id="74b6d-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="74b6d-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b6d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74b6d-110">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="74b6d-111">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="74b6d-111">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="74b6d-112">Como associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="74b6d-112">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
