---
title: "Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64e51a8911e27a612500ba222df7e3637cd24a13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)
Você pode criar um nó derivado em um Windows Forms <xref:System.Windows.Forms.TreeView> controle ou um item derivado em uma <xref:System.Windows.Forms.ListView> controle. A derivação permite adicionar todos os campos necessários, assim como métodos e construtores personalizados para manipulá-los. Um uso desse recurso é anexar um objeto do cliente a cada nó de árvore ou item de lista. Os exemplos aqui são para uma <xref:System.Windows.Forms.TreeView> controle, mas a mesma abordagem pode ser usado para um <xref:System.Windows.Forms.ListView> controle.  
  
### <a name="to-derive-a-tree-node"></a>Para derivar um nó de árvore  
  
-   Criar uma nova classe do nó, derivada de <xref:System.Windows.Forms.TreeNode> classe, que tem um campo personalizado para gravar um caminho de arquivo.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Para usar um nó de árvore derivado  
  
1.  É possível usar o novo nó de árvore derivado como um parâmetro para chamadas de função.  
  
     No exemplo abaixo, o caminho definido para o local do arquivo de texto é a pasta Meus Documentos. Isso é feito porque podemos presumir que a maioria dos computadores rodando o sistema operacional Windows vão incluir este diretório. Isso também permite que usuários com níveis mínimos de acesso ao sistema executem com segurança o aplicativo.  
  
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
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
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
  
2.  Se são passados ao nó de árvore e seu tipo for um <xref:System.Windows.Forms.TreeNode> classe, em seguida, você precisará converter para sua classe derivada. Se trata de uma conversão explícita de um tipo de objeto para outro. Para mais informações sobre conversão, consulte [Conversões Implícitas e Explícitas](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() Operador](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) ou [Operador de Conversão: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
