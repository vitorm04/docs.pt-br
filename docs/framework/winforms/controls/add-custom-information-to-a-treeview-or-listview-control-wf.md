---
title: 'Como: Adicionar informações personalizadas a um controle TreeView ou ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: faed586a5814526b0169ea46c8bb452e3777d8ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182431"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="3207f-102">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3207f-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="3207f-103">Você pode criar um nó derivado <xref:System.Windows.Forms.TreeView> em um controle do Windows <xref:System.Windows.Forms.ListView> Forms ou em um item derivado em um controle.</span><span class="sxs-lookup"><span data-stu-id="3207f-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="3207f-104">A derivação permite adicionar todos os campos necessários, assim como métodos e construtores personalizados para manipulá-los.</span><span class="sxs-lookup"><span data-stu-id="3207f-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="3207f-105">Um uso desse recurso é anexar um objeto do cliente a cada nó de árvore ou item de lista.</span><span class="sxs-lookup"><span data-stu-id="3207f-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="3207f-106">Os exemplos aqui são <xref:System.Windows.Forms.TreeView> para um controle, mas a <xref:System.Windows.Forms.ListView> mesma abordagem pode ser usada para um controle.</span><span class="sxs-lookup"><span data-stu-id="3207f-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="3207f-107">Para derivar um nó de árvore</span><span class="sxs-lookup"><span data-stu-id="3207f-107">To derive a tree node</span></span>  
  
- <span data-ttu-id="3207f-108">Crie uma nova classe de nó, derivada da <xref:System.Windows.Forms.TreeNode> classe, que tem um campo personalizado para gravar um caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="3207f-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="3207f-109">Para usar um nó de árvore derivado</span><span class="sxs-lookup"><span data-stu-id="3207f-109">To use a derived tree node</span></span>  
  
1. <span data-ttu-id="3207f-110">É possível usar o novo nó de árvore derivado como um parâmetro para chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="3207f-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="3207f-111">No exemplo abaixo, o caminho definido para o local do arquivo de texto é a pasta Meus Documentos.</span><span class="sxs-lookup"><span data-stu-id="3207f-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="3207f-112">Isso é feito porque podemos presumir que a maioria dos computadores rodando o sistema operacional Windows vão incluir este diretório.</span><span class="sxs-lookup"><span data-stu-id="3207f-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="3207f-113">Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3207f-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
    ```vb  
    ' You should replace the bold text file
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
    ```  
  
    ```csharp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\TextFile.txt") );  
    ```  
  
    ```cpp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2. <span data-ttu-id="3207f-114">Se você passar o nó da árvore e <xref:System.Windows.Forms.TreeNode> ele for digitado como uma classe, então você precisará lançar para a sua classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3207f-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="3207f-115">Se trata de uma conversão explícita de um tipo de objeto para outro.</span><span class="sxs-lookup"><span data-stu-id="3207f-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="3207f-116">Para obter mais informações sobre casting, consulte [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Fundição e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) ou [Operador de Elenco: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="3207f-116">For more information on casting, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Casting and type conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span></span>  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",
             myNode->FilePath));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3207f-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3207f-117">See also</span></span>

- [<span data-ttu-id="3207f-118">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="3207f-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="3207f-119">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="3207f-119">ListView Control</span></span>](listview-control-windows-forms.md)
