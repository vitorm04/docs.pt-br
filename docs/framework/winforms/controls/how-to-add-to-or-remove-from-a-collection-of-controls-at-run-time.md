---
title: 'Como: Adicionar ou remover de uma coleção de controles em tempo de execução'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 88a743cc6d0a1e90d2912c9ec610fae326ff5770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744902"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Como: Adicionar ou remover de uma coleção de controles em tempo de execução
Tarefas comuns no desenvolvimento de aplicativos são adicionar controles para e remover controles de qualquer controle de contêiner em formulários (como o <xref:System.Windows.Forms.Panel> ou <xref:System.Windows.Forms.GroupBox> controle ou até mesmo o próprio formulário). Em tempo de design, controles podem ser arrastados diretamente para um painel ou caixa de grupo. Em tempo de execução, esses controles mantêm uma coleção `Controls`, que mantém o controle de quais controles são colocados neles.  
  
> [!NOTE]
>  O exemplo de código a seguir aplica-se a qualquer controle que mantém uma coleção de controles dentro dele.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Para adicionar um controle a uma coleção de forma programática  
  
1.  Crie uma instância do controle a ser adicionado.  
  
2.  Defina as propriedades do novo controle.  
  
3.  Adicione o controle à coleção `Controls` do controle pai.  
  
     O exemplo de código a seguir mostra como criar uma instância da <xref:System.Windows.Forms.Button> controle. Ele exige um formulário com um <xref:System.Windows.Forms.Panel> controle e que o método de manipulação de eventos para o botão que está sendo criado, `NewPanelButton_Click`, já existe.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Para remover os controles de uma coleção de forma programática  
  
1.  Remova o manipulador de eventos do evento. No Visual Basic, use o [Instrução RemoveHandler](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) palavra-chave; no Visual C#, use o [-= operador (C# referência)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Use o método `Remove` para excluir o controle desejado da coleção `Controls` do painel.  
  
3.  Chamar o <xref:System.Windows.Forms.Control.Dispose%2A> método para liberar todos os recursos usados pelo controle.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Panel>
- [Controle de painel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
