---
title: 'Como: Iterar em todos os nós de um controle TreeView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: e8e5ef299ca7b5555a02e86e4422ca9f5b8a584f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199707"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Como: Iterar em todos os nós de um controle TreeView do Windows Forms
Às vezes é útil para examinar todos os nós em um Windows Forms <xref:System.Windows.Forms.TreeView> controle para realizar alguns cálculos nos valores de nó. Essa operação pode ser feita usando um procedimento recursivo (método recursivo em C# e C++) que itera em cada nó em cada coleção da árvore.  
  
 Cada <xref:System.Windows.Forms.TreeNode> objeto em uma exibição de árvore tem propriedades que você pode usar para navegar a exibição de árvore: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, e <xref:System.Windows.Forms.TreeNode.Parent%2A>. O valor da <xref:System.Windows.Forms.TreeNode.Parent%2A> propriedade é o nó pai do nó atual. Os nós filho do nó atual, caso haja algum, são listados no seu <xref:System.Windows.Forms.TreeNode.Nodes%2A> propriedade. O <xref:System.Windows.Forms.TreeView> próprio controle tem o <xref:System.Windows.Forms.TreeView.TopNode%2A> propriedade, que é o nó raiz do modo de exibição de árvore inteira.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Como iterar em todos os nós do controle TreeView  
  
1.  Crie um procedimento recursivo (método recursivo em C# e C++) que testa cada nó.  
  
2.  Chame o procedimento.  
  
     O exemplo a seguir mostra como imprimir cada <xref:System.Windows.Forms.TreeNode> do objeto <xref:System.Windows.Forms.TreeNode.Text%2A> propriedade:  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Procedimentos recursivos](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
