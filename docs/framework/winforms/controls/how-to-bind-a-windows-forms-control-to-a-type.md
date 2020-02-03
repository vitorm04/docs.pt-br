---
title: Associar controle a um tipo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744991"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="871f9-102">Como associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="871f9-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="871f9-103">Quando estiver criando controles que interagem com os dados, às vezes, achará necessário associar um controle a um tipo, em vez de um objeto.</span><span class="sxs-lookup"><span data-stu-id="871f9-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="871f9-104">Essa situação ocorre especialmente em tempo de design, quando os dados podem não estar disponíveis, mas seus controles ligados a dados ainda precisam exibir informações da interface pública de um tipo.</span><span class="sxs-lookup"><span data-stu-id="871f9-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="871f9-105">Por exemplo, você pode associar um controle de <xref:System.Windows.Forms.DataGridView> a um objeto exposto por um serviço Web e deseja que o controle de <xref:System.Windows.Forms.DataGridView> etiquete suas colunas em tempo de design com os nomes de membro de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="871f9-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="871f9-106">Você pode associar facilmente um controle a um tipo com o componente <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="871f9-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="871f9-107">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="871f9-107">Example</span></span>  
 <span data-ttu-id="871f9-108">O exemplo de código a seguir demonstra como associar um controle de <xref:System.Windows.Forms.DataGridView> a um tipo personalizado usando um componente <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="871f9-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="871f9-109">Ao executar o exemplo, você observará que o <xref:System.Windows.Forms.DataGridView> tem colunas rotuladas que refletem as propriedades de um objeto `Customer`, antes que o controle seja preenchido com dados.</span><span class="sxs-lookup"><span data-stu-id="871f9-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="871f9-110">O exemplo tem um botão Adicionar cliente para adicionar dados ao controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="871f9-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="871f9-111">Quando você clica no botão, um novo objeto `Customer` é adicionado à <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="871f9-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="871f9-112">Em um cenário do mundo real, os dados podem ser obtidos por uma chamada para um serviço Web ou outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="871f9-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="871f9-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="871f9-113">Compiling the Code</span></span>  
 <span data-ttu-id="871f9-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="871f9-114">This example requires:</span></span>  
  
- <span data-ttu-id="871f9-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="871f9-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871f9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="871f9-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="871f9-117">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="871f9-117">BindingSource Component</span></span>](bindingsource-component.md)
