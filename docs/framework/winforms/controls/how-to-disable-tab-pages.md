---
title: Como desabilitar páginas de guia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182167"
---
# <a name="how-to-disable-tab-pages"></a>Como desabilitar páginas de guia
Em algumas ocasiões, pode ser útil restringir o acesso aos dados que estão disponíveis no seu Aplicativo do Windows Forms. Um exemplo disso seria quando você tem dados exibidos nas páginas da guia de um controle guia. Os administradores poderiam ter informações em uma página da guia que você gostaria de proibir para convidados ou usuários de nível inferior.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Desabilitar páginas de guia com programação  
  
1. Escreva código para lidar com <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> o evento do controle da guia. Esse é o evento que é gerado quando o usuário alterna de uma guia para a próxima.  
  
2. Verifique as credenciais. Dependendo das informações apresentadas, pode ser útil verificar o nome de usuário com que o usuário fez logon ou alguma outra credencial antes de permitir que o usuário exiba a guia.  
  
3. Se o usuário tiver as credenciais apropriadas, exiba a guia que foi clicada. Se o usuário não tiver as credenciais apropriadas, exibirá uma caixa de mensagem ou alguma outra interface do usuário indicando que eles não têm acesso e retorne à guia inicial.  
  
    > [!NOTE]
    > Quando você implementa essa funcionalidade em seus aplicativos de produção, você pode <xref:System.Windows.Forms.Form.Load> executar essa verificação de credencial durante o evento do formulário. Isso permitirá que você oculte a guia antes de exibir qualquer interface do usuário, que é uma abordagem muito mais simples do que programação. A metodologia utilizada abaixo (verificando credenciais <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> e desabilitando a guia durante o evento) é para fins ilustrativos.  
  
4. Opcionalmente, se você tiver mais de duas páginas da guia, exiba uma página da guia diferente da original.  
  
     No exemplo abaixo, <xref:System.Windows.Forms.CheckBox> um controle é usado em vez de verificar as credenciais, pois os critérios de acesso à guia variam de acordo com a aplicação. Quando <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> o evento é levantado, se a verificação de credencial for verdadeira (ou `TabPage2` seja, a caixa de seleção `TabPage2` é verificada) e a guia selecionada é (a guia com as informações confidenciais, neste exemplo), então é exibida. Caso contrário, `TabPage3` será exibido e uma caixa de mensagem será exibida para o usuário, indicando que ele não tem os privilégios de acesso apropriados. O código abaixo assume um <xref:System.Windows.Forms.CheckBox> formulário`CredentialCheck`com <xref:System.Windows.Forms.TabControl> um controle ( ) e um controle com três páginas de guia.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Confira também

- [Visão geral do controle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Como adicionar um controle a uma página da guia](how-to-add-a-control-to-a-tab-page.md)
- [Como adicionar e remover guias com o controle TabControl dos Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Como alterar a aparência do TabControl dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
