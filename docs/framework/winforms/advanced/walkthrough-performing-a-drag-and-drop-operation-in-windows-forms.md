---
title: 'Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529448"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms
Para executar operações de arrastar e soltar em aplicativos baseados no Windows você precisa lidar uma série de eventos, particularmente o <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos. Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".  
  
## <a name="dragging-data"></a>Arrastando dados  
 Todas as operações do tipo "arrastar e soltar" começam com arrastar. A funcionalidade de permitir que dados sejam coletados quando o arrastamento começa é implementada no <xref:System.Windows.Forms.Control.DoDragDrop%2A> método.  
  
 No exemplo a seguir, o <xref:System.Windows.Forms.Control.MouseDown> eventos é usado para iniciar a operação de arrastar porque ele é o mais intuitivo (a maioria das ações de arrastar e soltar começa com o botão do mouse sendo pressionado). No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".  
  
> [!NOTE]
>  Determinados controles têm eventos específicos de arrastar personalizados. O <xref:System.Windows.Forms.ListView> e <xref:System.Windows.Forms.TreeView> controles, por exemplo, tem um <xref:System.Windows.Forms.TreeView.ItemDrag> eventos.  
  
#### <a name="to-start-a-drag-operation"></a>Para iniciar uma operação de arrastar  
  
1.  No <xref:System.Windows.Forms.Control.MouseDown> eventos para o controle onde o arrastamento começará, use o `DoDragDrop` terão método para definir os dados a serem arrastados e o efeito permitido. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     O exemplo a seguir mostra como iniciar uma operação de arrastar. O controle onde começa a arrastar um <xref:System.Windows.Forms.Button> controle, os dados que está sendo arrastados é a cadeia de caracteres que representa o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.Button> controle e os efeitos permitidos são copiar ou mover.  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  Nenhum dado pode ser usado como um parâmetro no `DoDragDrop` método; no exemplo acima, o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.Button> controle foi usado (em vez de embutir um valor ou recuperar dados de um conjunto de dados) porque a propriedade estava relacionada com o local que está sendo arrastada (o <xref:System.Windows.Forms.Button> controle). Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.  
  
 Enquanto uma operação de arrastar estiver em vigor, você pode manipular o <xref:System.Windows.Forms.Control.QueryContinueDrag> evento, que "pede a permissão" do sistema para continuar a operação de arrastar. Ao lidar com esse método, também é o ponto apropriado para você chamar métodos que terão um efeito sobre a operação de arrastar, como expandir um <xref:System.Windows.Forms.TreeNode> em um <xref:System.Windows.Forms.TreeView> controlar quando o cursor passa sobre ele.  
  
## <a name="dropping-data"></a>Descartando dados  
 Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar. O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados. Qualquer área em um formulário do Windows ou controle pode ser feita para aceitar dados soltos, definindo a <xref:System.Windows.Forms.Control.AllowDrop%2A> propriedade e tratamento de <xref:System.Windows.Forms.Control.DragEnter> e <xref:System.Windows.Forms.Control.DragDrop> eventos.  
  
#### <a name="to-perform-a-drop"></a>Para executar uma operação de soltar  
  
1.  Definir o <xref:System.Windows.Forms.Control.AllowDrop%2A> propriedade como true.  
  
2.  No `DragEnter` eventos para o controle onde o descarte ocorrerá, certifique-se de que os dados que está sendo arrastados são de um tipo aceitável (neste caso, <xref:System.Windows.Forms.Control.Text%2A>). O código define o efeito que acontecerá quando o descarte ocorre para um valor na <xref:System.Windows.Forms.DragDropEffects> enumeração. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  Você pode definir suas próprias <xref:System.Windows.Forms.DataFormats> especificando seu próprio objeto como o <xref:System.Object> parâmetro o <xref:System.Windows.Forms.DataObject.SetData%2A> método. Ao fazer isso, verifique se o objeto especificado é serializável. Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  No <xref:System.Windows.Forms.Control.DragDrop> eventos para o controle onde a operação de soltar irá ocorrer, use o <xref:System.Windows.Forms.DataObject.GetData%2A> método para recuperar os dados que está sendo arrastados. Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     No exemplo a seguir, um <xref:System.Windows.Forms.TextBox> controle é o controle sendo arrastado para (onde a operação de soltar irá ocorrer). O código define o <xref:System.Windows.Forms.Control.Text%2A> propriedade o <xref:System.Windows.Forms.TextBox> controlar igual aos dados que está sendo arrastados.  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  Além disso, você pode trabalhar com o <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> propriedade, para que, dependendo das teclas pressionadas durante a operação de arrastar e soltar, determinados efeitos ocorram (por exemplo, ele é padrão para copiar os dados arrastados quando a tecla CTRL pressionada).  
  
## <a name="see-also"></a>Consulte também  
 [Como Adicionar Dados à Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Como Recuperar Dados da Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
