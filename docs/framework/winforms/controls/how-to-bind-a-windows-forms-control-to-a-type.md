---
title: 'Como: Associar um controle do Windows Forms a um tipo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: ab088e3f34f3f03be2073864a440006259fe5679
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591334"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="78202-102">Como: Associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="78202-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="78202-103">Quando estiver criando controles que interagem com os dados, às vezes, achará necessário associar um controle a um tipo, em vez de um objeto.</span><span class="sxs-lookup"><span data-stu-id="78202-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="78202-104">Essa situação ocorre especialmente em tempo de design, quando os dados podem não estar disponíveis, mas seus controles ligados a dados ainda precisam exibir informações da interface pública de um tipo.</span><span class="sxs-lookup"><span data-stu-id="78202-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="78202-105">Por exemplo, você pode associar uma <xref:System.Windows.Forms.DataGridView> controlar a um objeto exposto por um serviço Web e deseja que o <xref:System.Windows.Forms.DataGridView> controle para nomes de rótulo suas colunas em tempo de design com o membro de um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="78202-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="78202-106">Você pode associar facilmente um controle a um tipo com o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="78202-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78202-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78202-107">Example</span></span>  
 <span data-ttu-id="78202-108">O exemplo de código a seguir demonstra como associar um <xref:System.Windows.Forms.DataGridView> controle para um tipo personalizado usando um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="78202-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="78202-109">Quando você executar o exemplo, você perceberá a <xref:System.Windows.Forms.DataGridView> rotulou as colunas que refletem as propriedades de um `Customer` do objeto, antes do controle é preenchido com dados.</span><span class="sxs-lookup"><span data-stu-id="78202-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="78202-110">O exemplo tem um botão Add Customer para adicionar dados para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="78202-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="78202-111">Quando você clica no botão, uma nova `Customer` objeto é adicionado para o <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="78202-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="78202-112">Em um cenário do mundo real, os dados podem ser obtidos por uma chamada para um serviço Web ou outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="78202-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78202-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="78202-113">Compiling the Code</span></span>  
 <span data-ttu-id="78202-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="78202-114">This example requires:</span></span>  
  
- <span data-ttu-id="78202-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="78202-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78202-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78202-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="78202-117">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="78202-117">BindingSource Component</span></span>](bindingsource-component.md)
