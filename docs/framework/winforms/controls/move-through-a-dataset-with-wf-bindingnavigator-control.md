---
title: 'Como: Percorrer um conjunto de dados com o controle BindingNavigator dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: df11a525ab6491cf12b4ffb63c276f39cae0e44e
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260695"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="b1c4c-102">Como: Percorrer um conjunto de dados com o controle BindingNavigator dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1c4c-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="b1c4c-103">Como criar aplicativos controlados por dados, geralmente você precisará exibir coleções de dados para os usuários.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="b1c4c-104">O <xref:System.Windows.Forms.BindingNavigator> controle, em conjunto com o <xref:System.Windows.Forms.BindingSource> componente, fornece uma solução conveniente e extensível para mover uma coleção e exibir itens em sequência.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1c4c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c4c-105">Example</span></span>  
 <span data-ttu-id="b1c4c-106">O exemplo de código a seguir demonstra como usar um <xref:System.Windows.Forms.BindingNavigator> controle a ser movido por meio de dados.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="b1c4c-107">O conjunto é contido em um <xref:System.Data.DataView>, que está associada a uma <xref:System.Windows.Forms.TextBox> controlar com um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c4c-108">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="b1c4c-109">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="b1c4c-110">Para obter mais informações, consulte [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="b1c4c-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1c4c-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b1c4c-111">Compiling the Code</span></span>  
 <span data-ttu-id="b1c4c-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b1c4c-112">This example requires:</span></span>  
  
-   <span data-ttu-id="b1c4c-113">Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="b1c4c-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b1c4c-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b1c4c-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="b1c4c-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1c4c-116">See also</span></span>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b1c4c-117">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="b1c4c-117">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="b1c4c-118">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="b1c4c-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="b1c4c-119">Como: Associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="b1c4c-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
