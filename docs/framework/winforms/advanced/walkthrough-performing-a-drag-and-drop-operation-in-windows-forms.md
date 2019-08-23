---
title: 'Passo a passo: executar uma operação do tipo "arrastar e soltar" no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957129"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Passo a passo: executar uma operação do tipo "arrastar e soltar" no Windows Forms
Para executar operações de arrastar e soltar em aplicativos baseados no Windows, você deve lidar com uma série de eventos, principalmente os <xref:System.Windows.Forms.Control.DragEnter>eventos <xref:System.Windows.Forms.Control.DragLeave>, e <xref:System.Windows.Forms.Control.DragDrop> . Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".  
  
## <a name="dragging-data"></a>Arrastando dados  
 Todas as operações do tipo "arrastar e soltar" começam com arrastar. A funcionalidade para habilitar os dados a serem coletados ao arrastar iniciar é implementada no <xref:System.Windows.Forms.Control.DoDragDrop%2A> método.  
  
 No exemplo a seguir, o <xref:System.Windows.Forms.Control.MouseDown> evento é usado para iniciar a operação de arrastar porque ela é a mais intuitiva (a maioria das ações de arrastar e soltar começa com o botão do mouse que está sendo pressionado). No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".  
  
> [!NOTE]
> Determinados controles têm eventos específicos de arrastar personalizados. Os <xref:System.Windows.Forms.ListView> controles <xref:System.Windows.Forms.TreeView> e, por exemplo, têm um <xref:System.Windows.Forms.TreeView.ItemDrag> evento.  
  
#### <a name="to-start-a-drag-operation"></a>Para iniciar uma operação de arrastar  
  
1. No evento para o controle em que o arrastar será iniciado, use o `DoDragDrop` método para definir os dados a serem arrastados e o efeito permitido ao arrastar terá. <xref:System.Windows.Forms.Control.MouseDown> Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     O exemplo a seguir mostra como iniciar uma operação de arrastar. O controle em que o arrastar começa é <xref:System.Windows.Forms.Button> um controle, os dados que estão sendo arrastados são <xref:System.Windows.Forms.Control.Text%2A> a cadeia de <xref:System.Windows.Forms.Button> caracteres que representa a propriedade do controle e os efeitos permitidos estão sendo copiados ou movidos.  
  
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
    > Todos os dados podem ser usados como um parâmetro no `DoDragDrop` método; no exemplo acima, a <xref:System.Windows.Forms.Control.Text%2A> Propriedade do <xref:System.Windows.Forms.Button> controle foi usada (em vez de embutir em código um valor ou recuperar dados de um DataSet) porque a propriedade estava relacionada ao local que está sendo arrastado <xref:System.Windows.Forms.Button> (o controle). Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.  
  
 Embora uma operação de arrastar esteja em vigor, você pode manipular <xref:System.Windows.Forms.Control.QueryContinueDrag> o evento, que "pede permissão" do sistema para continuar a operação de arrastar. Ao lidar com esse método, também é o ponto apropriado para você chamar métodos que terão um efeito na operação de arrastar, como expandir um <xref:System.Windows.Forms.TreeNode> em um <xref:System.Windows.Forms.TreeView> controle quando o cursor passar sobre ele.  
  
## <a name="dropping-data"></a>Descartando dados  
 Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar. O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados. Qualquer área dentro de um formulário ou controle do Windows pode ser feita para aceitar dados eliminados <xref:System.Windows.Forms.Control.AllowDrop%2A> definindo a propriedade e <xref:System.Windows.Forms.Control.DragEnter> manipulando os eventos e <xref:System.Windows.Forms.Control.DragDrop> .  
  
#### <a name="to-perform-a-drop"></a>Para executar uma operação de soltar  
  
1. Defina a <xref:System.Windows.Forms.Control.AllowDrop%2A> Propriedade como true.  
  
2. No caso do controle onde o descarte ocorrerá, verifique se os dados que estão sendo arrastados são de um tipo aceitável (nesse caso, <xref:System.Windows.Forms.Control.Text%2A>). `DragEnter` Em seguida, o código define o efeito que ocorrerá quando a ação de soltar ocorrer em <xref:System.Windows.Forms.DragDropEffects> um valor na enumeração. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Você pode definir seu próprio <xref:System.Windows.Forms.DataFormats> especificando seu próprio objeto como o <xref:System.Object> parâmetro do <xref:System.Windows.Forms.DataObject.SetData%2A> método. Ao fazer isso, verifique se o objeto especificado é serializável. Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.  
  
3. No caso do controle em que o drop ocorrerá, use o <xref:System.Windows.Forms.DataObject.GetData%2A> método para recuperar os dados que estão sendo arrastados. <xref:System.Windows.Forms.Control.DragDrop> Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     No exemplo a seguir, um <xref:System.Windows.Forms.TextBox> controle é o controle que está sendo arrastado para (onde o descarte ocorrerá). O código define a <xref:System.Windows.Forms.Control.Text%2A> propriedade <xref:System.Windows.Forms.TextBox> do controle igual aos dados que estão sendo arrastados.  
  
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
    > Além disso, você pode trabalhar com <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> a propriedade, de modo que, dependendo das chaves pressionadas durante a operação de arrastar e soltar, certos efeitos ocorram (por exemplo, é padrão para copiar os dados arrastados quando a tecla CTRL é pressionada).  
  
## <a name="see-also"></a>Consulte também

- [Como: Adicionar dados à área de transferência](how-to-add-data-to-the-clipboard.md)
- [Como: Recuperar dados da área de transferência](how-to-retrieve-data-from-the-clipboard.md)
- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
