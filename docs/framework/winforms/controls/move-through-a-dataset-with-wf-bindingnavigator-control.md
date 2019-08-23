---
title: 'Como: Avançar em um DataSet com o controle BindingNavigator do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952688"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="13460-102">Como: Avançar em um DataSet com o controle BindingNavigator do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13460-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="13460-103">Ao criar aplicativos controlados por dados, muitas vezes você precisará exibir coleções de dados aos usuários.</span><span class="sxs-lookup"><span data-stu-id="13460-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="13460-104">O <xref:System.Windows.Forms.BindingNavigator> controle, em conjunto com o <xref:System.Windows.Forms.BindingSource> componente, fornece uma solução conveniente e extensível para a movimentação de uma coleção e a exibição de itens em sequência.</span><span class="sxs-lookup"><span data-stu-id="13460-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13460-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13460-105">Example</span></span>  
 <span data-ttu-id="13460-106">O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.BindingNavigator> um controle para percorrer dados.</span><span class="sxs-lookup"><span data-stu-id="13460-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="13460-107">O conjunto está contido em um <xref:System.Data.DataView>, que está associado a um <xref:System.Windows.Forms.TextBox> controle com um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="13460-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13460-108">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13460-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="13460-109">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="13460-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="13460-110">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="13460-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13460-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="13460-111">Compiling the Code</span></span>  
 <span data-ttu-id="13460-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="13460-112">This example requires:</span></span>  
  
- <span data-ttu-id="13460-113">Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="13460-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13460-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13460-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="13460-115">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="13460-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="13460-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="13460-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="13460-117">Como: Associar um controle de Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="13460-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
