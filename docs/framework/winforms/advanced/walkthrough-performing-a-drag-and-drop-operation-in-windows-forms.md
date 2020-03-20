---
title: 'Passo a passo: Realize uma operação de arrastar e soltar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182439"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms
Para executar operações de arrastar e soltar dentro de aplicativos baseados no <xref:System.Windows.Forms.Control.DragEnter>Windows, você deve lidar com uma série de eventos, principalmente os <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> eventos. Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".  
  
## <a name="dragging-data"></a>Arrastando dados  
 Todas as operações do tipo "arrastar e soltar" começam com arrastar. A funcionalidade para permitir que os dados sejam <xref:System.Windows.Forms.Control.DoDragDrop%2A> coletados quando o arrasto começa é implementada no método.  
  
 No exemplo a <xref:System.Windows.Forms.Control.MouseDown> seguir, o evento é usado para iniciar a operação de arrastar porque é a mais intuitiva (a maioria das ações de arrastar e soltar começa com o botão do mouse sendo pressionado). No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".  
  
> [!NOTE]
> Determinados controles têm eventos específicos de arrastar personalizados. Os <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> controles, por exemplo, <xref:System.Windows.Forms.TreeView.ItemDrag> têm um evento.  
  
#### <a name="to-start-a-drag-operation"></a>Para iniciar uma operação de arrastar  
  
1. No <xref:System.Windows.Forms.Control.MouseDown> caso de o controle onde o `DoDragDrop` arrasto começará, use o método para definir os dados a serem arrastados e o arrasto de efeito permitido terá. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     O exemplo a seguir mostra como iniciar uma operação de arrastar. O controle onde o <xref:System.Windows.Forms.Button> arrasto começa é um controle, os <xref:System.Windows.Forms.Control.Text%2A> dados <xref:System.Windows.Forms.Button> que estão sendo arrastados é a string representando a propriedade do controle, e os efeitos permitidos estão copiando ou se movendo.  
  
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
    > Qualquer dado pode ser usado `DoDragDrop` como parâmetro no método; no exemplo acima, <xref:System.Windows.Forms.Control.Text%2A> a <xref:System.Windows.Forms.Button> propriedade do controle foi usada (em vez de codificar um valor ou recuperar dados de um <xref:System.Windows.Forms.Button> conjunto de dados) porque a propriedade estava relacionada com o local que estava sendo arrastado (o controle). Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.  
  
 Enquanto uma operação de arrasto <xref:System.Windows.Forms.Control.QueryContinueDrag> estiver em vigor, você pode lidar com o evento, que "pede permissão" do sistema para continuar a operação de arrasto. Ao manusear este método, também é o ponto apropriado para você chamar métodos que terão um efeito na operação de arrasto, como expandir um <xref:System.Windows.Forms.TreeNode> em um <xref:System.Windows.Forms.TreeView> controle quando o cursor paira sobre ele.  
  
## <a name="dropping-data"></a>Descartando dados  
 Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar. O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados. Qualquer área dentro de um Formulário ou controle do Windows <xref:System.Windows.Forms.Control.AllowDrop%2A> pode ser <xref:System.Windows.Forms.Control.DragEnter> feita <xref:System.Windows.Forms.Control.DragDrop> para aceitar dados descartados definindo a propriedade e lidando com os eventos e eventos.  
  
#### <a name="to-perform-a-drop"></a>Para executar uma operação de soltar  
  
1. Coloque <xref:System.Windows.Forms.Control.AllowDrop%2A> a propriedade como verdadeira.  
  
2. No `DragEnter` caso de controle onde a queda ocorrerá, certifique-se de que os dados <xref:System.Windows.Forms.Control.Text%2A>que estão sendo arrastados sejam de um tipo aceitável (neste caso, ). O código então define o efeito que acontecerá quando <xref:System.Windows.Forms.DragDropEffects> a queda ocorrer a um valor na enumeração. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Você pode definir <xref:System.Windows.Forms.DataFormats> o seu próprio especificando seu próprio objeto como o <xref:System.Object> parâmetro do <xref:System.Windows.Forms.DataObject.SetData%2A> método. Ao fazer isso, verifique se o objeto especificado é serializável. Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.  
  
3. No <xref:System.Windows.Forms.Control.DragDrop> caso de controlar onde a queda <xref:System.Windows.Forms.DataObject.GetData%2A> ocorrerá, use o método para recuperar os dados que estão sendo arrastados. Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     No exemplo abaixo, <xref:System.Windows.Forms.TextBox> um controle é o controle sendo arrastado para (onde a queda ocorrerá). O código <xref:System.Windows.Forms.Control.Text%2A> define a <xref:System.Windows.Forms.TextBox> propriedade do controle igual aos dados que estão sendo arrastados.  
  
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
    > Além disso, você pode <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> trabalhar com a propriedade, de modo que, dependendo das teclas deprimidas durante a operação de arrastar e soltar, certos efeitos ocorram (por exemplo, é padrão copiar os dados arrastados quando a tecla CTRL é pressionada).  
  
## <a name="see-also"></a>Confira também

- [Como Adicionar Dados à Área de Transferência](how-to-add-data-to-the-clipboard.md)
- [Como Recuperar Dados da Área de Transferência](how-to-retrieve-data-from-the-clipboard.md)
- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
