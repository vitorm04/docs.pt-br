---
title: Iterar em todos os nós do controle TreeView
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
ms.openlocfilehash: 010932fa3fdfaa907325b9934682dcbf889265c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736373"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Como iterar em todos os nós de um controle TreeView dos Windows Forms
Às vezes, é útil examinar cada nó em um controle de <xref:System.Windows.Forms.TreeView> Windows Forms para executar algum cálculo nos valores de nó. Essa operação pode ser feita usando um procedimento recursivo (método recursivo em c# e C++) que itera em cada nó em cada coleção da árvore.  
  
 Cada objeto de <xref:System.Windows.Forms.TreeNode> em um modo de exibição de árvore tem propriedades que você pode usar para navegar no modo de exibição de árvore: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>e <xref:System.Windows.Forms.TreeNode.Parent%2A>. O valor da propriedade <xref:System.Windows.Forms.TreeNode.Parent%2A> é o nó pai do nó atual. Os nós filho do nó atual, se houver algum, são listados em sua propriedade <xref:System.Windows.Forms.TreeNode.Nodes%2A>. O próprio controle de <xref:System.Windows.Forms.TreeView> tem a propriedade <xref:System.Windows.Forms.TreeView.TopNode%2A>, que é o nó raiz do modo de exibição de árvore inteiro.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Como iterar em todos os nós do controle TreeView  
  
1. Crie um procedimento recursivo (método recursivo em c# e C++) que testa cada nó.  
  
2. Chame o procedimento.  
  
     O exemplo a seguir mostra como imprimir cada <xref:System.Windows.Forms.TreeNode> Propriedade <xref:System.Windows.Forms.TreeNode.Text%2A> do objeto:  
  
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
  
## <a name="see-also"></a>Veja também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Procedimentos Recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
