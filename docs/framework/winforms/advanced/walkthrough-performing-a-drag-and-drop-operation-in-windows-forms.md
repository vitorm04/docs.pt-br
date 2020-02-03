---
title: 'Walkthrough: executar uma operação de arrastar e soltar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746798"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Instruções passo a passo: executando uma operação de arrastar e soltar no Windows Forms
Para executar operações de arrastar e soltar em aplicativos baseados no Windows, você deve lidar com uma série de eventos, principalmente os eventos <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>e <xref:System.Windows.Forms.Control.DragDrop>. Trabalhando com as informações disponíveis no evento argumentos desses eventos, você pode facilmente orientar as operações do tipo "arrastar e soltar".  
  
## <a name="dragging-data"></a>Arrastando dados  
 Todas as operações do tipo "arrastar e soltar" começam com arrastar. A funcionalidade para habilitar os dados a serem coletados ao arrastar iniciar é implementada no método <xref:System.Windows.Forms.Control.DoDragDrop%2A>.  
  
 No exemplo a seguir, o evento <xref:System.Windows.Forms.Control.MouseDown> é usado para iniciar a operação de arrastar porque ela é a mais intuitiva (a maioria das ações de arrastar e soltar começa com o botão do mouse que está sendo pressionado). No entanto, lembre-se de que qualquer evento pode ser usado para iniciar um procedimento do tipo "arrastar e soltar".  
  
> [!NOTE]
> Determinados controles têm eventos específicos de arrastar personalizados. Os controles <xref:System.Windows.Forms.ListView> e <xref:System.Windows.Forms.TreeView>, por exemplo, têm um evento <xref:System.Windows.Forms.TreeView.ItemDrag>.  
  
#### <a name="to-start-a-drag-operation"></a>Para iniciar uma operação de arrastar  
  
1. No evento <xref:System.Windows.Forms.Control.MouseDown> para o controle em que o arrastar será iniciado, use o método `DoDragDrop` para definir os dados a serem arrastados e o efeito permitido ao arrastar terá. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Data%2A> e <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     O exemplo a seguir mostra como iniciar uma operação de arrastar. O controle em que o arrastar começa é um controle <xref:System.Windows.Forms.Button>, os dados que estão sendo arrastados são a cadeia de caracteres que representa a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.Button>, e os efeitos permitidos estão sendo copiados ou movidos.  
  
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
    > Todos os dados podem ser usados como um parâmetro no método `DoDragDrop`; no exemplo acima, a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.Button> foi usada (em vez de embutir um valor em código ou recuperar dados de um conjunto) porque a propriedade estava relacionada ao local que está sendo arrastado (o controle de <xref:System.Windows.Forms.Button>). Lembre-se disso ao incorporar operações do tipo "arrastar e soltar" em seus aplicativos baseados em Windows.  
  
 Embora uma operação de arrastar esteja em vigor, você pode manipular o evento <xref:System.Windows.Forms.Control.QueryContinueDrag>, que "pede permissão" do sistema para continuar a operação de arrastar. Ao lidar com esse método, também é o ponto apropriado para você chamar métodos que terão efeito sobre a operação de arrastar, como expandir um <xref:System.Windows.Forms.TreeNode> em um controle de <xref:System.Windows.Forms.TreeView> quando o cursor passar sobre ele.  
  
## <a name="dropping-data"></a>Descartando dados  
 Depois de começar a arrastar dados de um local em um Formulário ou controle do Windows, você naturalmente desejará soltá-los em algum lugar. O cursor mudará ao cruzar uma área de um formulário ou controle que esteja configurado corretamente para receber os dados soltados. Qualquer área dentro de um formulário ou controle do Windows pode ser feita para aceitar dados eliminados definindo a propriedade <xref:System.Windows.Forms.Control.AllowDrop%2A> e manipulando os eventos <xref:System.Windows.Forms.Control.DragEnter> e <xref:System.Windows.Forms.Control.DragDrop>.  
  
#### <a name="to-perform-a-drop"></a>Para executar uma operação de soltar  
  
1. Defina a propriedade <xref:System.Windows.Forms.Control.AllowDrop%2A> como true.  
  
2. No evento `DragEnter` para o controle em que ocorrerá a remoção, verifique se os dados que estão sendo arrastados são de um tipo aceitável (nesse caso, <xref:System.Windows.Forms.Control.Text%2A>). Em seguida, o código define o efeito que ocorrerá quando a ação de soltar ocorrer em um valor na enumeração <xref:System.Windows.Forms.DragDropEffects>. Para obter mais informações, consulte <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Você pode definir seus próprios <xref:System.Windows.Forms.DataFormats> especificando seu próprio objeto como o parâmetro <xref:System.Object> do método <xref:System.Windows.Forms.DataObject.SetData%2A>. Ao fazer isso, verifique se o objeto especificado é serializável. Para obter mais informações, consulte <xref:System.Runtime.Serialization.ISerializable>.  
  
3. No evento <xref:System.Windows.Forms.Control.DragDrop> para o controle onde o drop ocorrerá, use o método <xref:System.Windows.Forms.DataObject.GetData%2A> para recuperar os dados que estão sendo arrastados. Para obter mais informações, consulte <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     No exemplo a seguir, um controle de <xref:System.Windows.Forms.TextBox> é o controle que está sendo arrastado para (onde o descarte ocorrerá). O código define a propriedade <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.TextBox> igual aos dados que estão sendo arrastados.  
  
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
    > Além disso, você pode trabalhar com a propriedade <xref:System.Windows.Forms.DragEventArgs.KeyState%2A>, de modo que, dependendo das chaves pressionadas durante a operação de arrastar e soltar, certos efeitos ocorram (por exemplo, é padrão copiar os dados arrastados quando a tecla CTRL é pressionada).  
  
## <a name="see-also"></a>Consulte também

- [Como Adicionar Dados à Área de Transferência](how-to-add-data-to-the-clipboard.md)
- [Como Recuperar Dados da Área de Transferência](how-to-retrieve-data-from-the-clipboard.md)
- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
