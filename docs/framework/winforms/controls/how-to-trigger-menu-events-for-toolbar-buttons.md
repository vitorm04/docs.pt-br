---
title: "Como acionar eventos de menu para botões da barra de ferramentas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7744b82e7a1e041b50b9ce1d55ac93f65b1489f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Como acionar eventos de menu para botões da barra de ferramentas
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 Se os recursos do Windows Form um <xref:System.Windows.Forms.ToolBar> controle com os botões da barra de ferramentas, você desejará saber qual botão o usuário clica.  
  
 No <xref:System.Windows.Forms.ToolBar.ButtonClick> eventos do <xref:System.Windows.Forms.ToolBar> controle, você pode avaliar o <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> propriedade o <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe. No exemplo a seguir, uma caixa de mensagem é exibida, indicando qual botão foi clicado. Para obter detalhes, consulte <xref:System.Windows.Forms.MessageBox>.  
  
 O exemplo a seguir supõe um <xref:System.Windows.Forms.ToolBar> controle foi adicionado a um formulário do Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Para manipular o evento de Clique na barra de ferramentas  
  
1.  Em um procedimento, adicione botões de barra de ferramentas para a <xref:System.Windows.Forms.ToolBar> controle.  
  
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
  
2.  Adicionar um manipulador de eventos para o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.ButtonClick> eventos. Use um caso de alternância de instrução e <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe para determinar o botão de barra de ferramentas que foi clicado. Com base nisso, exiba a caixa de mensagem apropriada.  
  
    > [!NOTE]
    >  Uma caixa de mensagem está sendo usada apenas como um espaço reservado neste exemplo. Fique à vontade para adicionar outro código para ser executado quando os botões da barra de ferramentas forem clicados.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolBar>  
 [Como adicionar botões a um controle de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [Como definir um ícone para um botão de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Controle de barra de ferramentas](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
