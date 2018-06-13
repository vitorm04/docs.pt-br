---
title: Como adicionar controles aos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 2dd048fb074d1ec5bb7bc0a67f196d5d51281545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528471"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Como adicionar controles aos Windows Forms
A maioria dos formulários é projetada adicionando controles à superfície do formulário para definir uma interface do usuário (IU). Um *controle* é um componente em um formulário usado para exibir informações ou aceitar a entrada do usuário. Para obter mais informações sobre controles, consulte [Controles do Windows Forms](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-draw-a-control-on-a-form"></a>Desenhar um controle em um formulário  
  
1.  Abra o formulário. Para obter mais informações, consulte [Como exibir Windows Forms no Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Na **Caixa de ferramentas**, clique no controle que você deseja adicionar ao formulário.  
  
3.  No formulário, clique onde você deseja que o canto superior esquerdo do controle se localize e arraste até onde você deseja posicionar o canto inferior direito do controle.  
  
     O controle é adicionado ao formulário com a localização e o tamanho especificados.  
  
    > [!NOTE]
    >  Cada controle tem um tamanho padrão definido. Você pode adicionar um controle ao seu formulário no tamanho de padrão do controle arrastando-o da **Caixa de ferramentas** para o formulário.  
  
### <a name="to-drag-a-control-to-a-form"></a>Arrastar um controle para um formulário  
  
1.  Abra o formulário. Para obter mais informações, consulte [Como exibir Windows Forms no Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Na **Caixa de ferramentas**, clique no controle que você deseja e arraste-o para o formulário.  
  
     O controle é adicionado ao formulário na localização e tamanho especificados.  
  
    > [!NOTE]
    >  Você pode clicar duas vezes em um controle na **Caixa de ferramentas** para adicioná-lo ao canto superior esquerdo do formulário com seu tamanho padrão.  
  
     Você também pode adicionar controles dinamicamente a um formulário no tempo de execução. No exemplo de código a seguir, uma <xref:System.Windows.Forms.TextBox> controle será adicionado ao formulário quando um <xref:System.Windows.Forms.Button> controle é clicado.  
  
    > [!NOTE]
    >  O procedimento a seguir requer a existência de um formulário com um controle **Botão**, `Button1`, já inserido nele.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Adicionar um controle a um formulário com programação  
  
1.  No método que trata o evento `Click` do botão na classe do formulário, insira código semelhante ao seguinte para adicionar uma referência à variável do controle, defina o `Location` do controle e adicione o controle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  Você também pode adicionar código para inicializar outras propriedades do controle.  
  
    > [!IMPORTANT]
    >  Você poderia expor seu computador local a um risco de segurança por meio da rede referenciando um `UserControl` mal-intencionado. Isso seria um problemas apenas no caso de uma pessoa mal-intencionada criar um controle personalizado prejudicial e você adicioná-lo por engano ao seu projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Como redimensionar controles no Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
