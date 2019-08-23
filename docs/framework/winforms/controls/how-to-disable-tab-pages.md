---
title: 'Como: Desabilitar páginas de guia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967144"
---
# <a name="how-to-disable-tab-pages"></a>Como: Desabilitar páginas de guia
Em algumas ocasiões, pode ser útil restringir o acesso aos dados que estão disponíveis no seu Aplicativo do Windows Forms. Um exemplo disso seria quando você tem dados exibidos nas páginas da guia de um controle guia. Os administradores poderiam ter informações em uma página da guia que você gostaria de proibir para convidados ou usuários de nível inferior.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Desabilitar páginas de guia com programação  
  
1. Escreva o código para manipular o evento do <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> controle da guia. Esse é o evento que é gerado quando o usuário alterna de uma guia para a próxima.  
  
2. Verifique as credenciais. Dependendo das informações apresentadas, pode ser útil verificar o nome de usuário com que o usuário fez logon ou alguma outra credencial antes de permitir que o usuário exiba a guia.  
  
3. Se o usuário tiver as credenciais apropriadas, exiba a guia que foi clicada. Se o usuário não tiver as credenciais apropriadas, exibirá uma caixa de mensagem ou alguma outra interface do usuário indicando que eles não têm acesso e retorne à guia inicial.  
  
    > [!NOTE]
    > Ao implementar essa funcionalidade em seus aplicativos de produção, você pode executar essa verificação de credencial durante o <xref:System.Windows.Forms.Form.Load> evento do formulário. Isso permitirá que você oculte a guia antes de exibir qualquer interface do usuário, que é uma abordagem muito mais simples do que programação. A metodologia usada abaixo (verificando as credenciais e desabilitando a guia <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> durante o evento) é para fins ilustrativos.  
  
4. Opcionalmente, se você tiver mais de duas páginas da guia, exiba uma página da guia diferente da original.  
  
     No exemplo a seguir, um <xref:System.Windows.Forms.CheckBox> controle é usado no lugar da verificação das credenciais, uma vez que os critérios de acesso à guia variam de acordo com o aplicativo. Quando o <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> evento for gerado, se a verificação de credencial for verdadeira (ou seja, a caixa de seleção estiver marcada) e a `TabPage2` guia selecionada for (a guia com as informações confidenciais, neste exemplo) `TabPage2` , será exibida. Caso contrário, `TabPage3` será exibido e uma caixa de mensagem será exibida para o usuário, indicando que ele não tem os privilégios de acesso apropriados. O código a seguir pressupõe um formulário com <xref:System.Windows.Forms.CheckBox> um controle`CredentialCheck`() e <xref:System.Windows.Forms.TabControl> um controle com três páginas de guia.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Como: Adicionar um controle a uma página de guia](how-to-add-a-control-to-a-tab-page.md)
- [Como: Adicionar e remover guias com o TabControl Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Como: Alterar a aparência do TabControl Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
