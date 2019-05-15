---
title: 'Como: Associar um controle do Windows Forms a um objeto de alocador'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: b64545528746e50d00f88d626a07ac98839e926c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589729"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="1ab2a-102">Como: Associar um controle do Windows Forms a um objeto de alocador</span><span class="sxs-lookup"><span data-stu-id="1ab2a-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="1ab2a-103">Quando você estiver criando controles que interagem com os dados, às vezes, será necessário associar um controle a um objeto ou método que gere outros objetos.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="1ab2a-104">Esse objeto ou método é chamado de alocador.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="1ab2a-105">A fonte de dados pode ser, por exemplo, o valor retornado de uma chamada de método, em vez de um objeto na memória ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="1ab2a-106">Você pode associar um controle a esse tipo de fonte de dados desde que a fonte retorne uma coleção.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="1ab2a-107">Você pode associar facilmente um controle para um objeto de fábrica usando o <xref:System.Windows.Forms.BindingSource> controle.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ab2a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ab2a-108">Example</span></span>  
 <span data-ttu-id="1ab2a-109">O exemplo a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle para um método de fábrica usando um <xref:System.Windows.Forms.BindingSource> controle.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="1ab2a-110">O método de fábrica chama-se `GetOrdersByCustomerId` e retorna todos os pedidos para determinado cliente no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ab2a-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1ab2a-111">Compiling the Code</span></span>  
 <span data-ttu-id="1ab2a-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1ab2a-112">This example requires:</span></span>  
  
- <span data-ttu-id="1ab2a-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1ab2a-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab2a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ab2a-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1ab2a-115">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="1ab2a-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1ab2a-116">Como: Associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="1ab2a-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
