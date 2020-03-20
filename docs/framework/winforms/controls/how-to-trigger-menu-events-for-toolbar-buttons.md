---
title: Como acionar eventos de menu para botões da barra de ferramentas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182073"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Como acionar eventos de menu para botões da barra de ferramentas
> [!NOTE]
> O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 Se o formulário <xref:System.Windows.Forms.ToolBar> do Windows possui um controle com botões de barra de ferramentas, você vai querer saber em qual botão o usuário clica.  
  
 No <xref:System.Windows.Forms.ToolBar.ButtonClick> caso do <xref:System.Windows.Forms.ToolBar> controle, você <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> pode avaliar <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> a propriedade da classe. No exemplo a seguir, uma caixa de mensagem é exibida, indicando qual botão foi clicado. Para obter detalhes, consulte <xref:System.Windows.Forms.MessageBox>.  
  
 O exemplo abaixo <xref:System.Windows.Forms.ToolBar> assume que um controle foi adicionado a um formulário do Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Para manipular o evento de Clique na barra de ferramentas  
  
1. Em um procedimento, adicione botões <xref:System.Windows.Forms.ToolBar> de barra de ferramentas ao controle.  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. Adicione um manipulador <xref:System.Windows.Forms.ToolBar> de eventos <xref:System.Windows.Forms.ToolBar.ButtonClick> para o evento do controle. Use uma declaração de <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> comutação de caso e a classe para determinar o botão da barra de ferramentas que foi clicado. Com base nisso, exiba a caixa de mensagem apropriada.  
  
    > [!NOTE]
    > Uma caixa de mensagem está sendo usada apenas como um espaço reservado neste exemplo. Fique à vontade para adicionar outro código para ser executado quando os botões da barra de ferramentas forem clicados.  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ToolBar>
- [Como adicionar botões a um controle de barra de ferramentas](how-to-add-buttons-to-a-toolbar-control.md)
- [Como definir um ícone para um botão de barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button.md)
- [Controle ToolBar](toolbar-control-windows-forms.md)
