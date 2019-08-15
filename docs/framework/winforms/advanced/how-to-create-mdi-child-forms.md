---
title: 'Como: criar formulários filho MDI'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040106"
---
# <a name="how-to-create-mdi-child-forms"></a>Como: Criar formulários filho MDI

Os formulários filho MDI são um elemento essencial de [aplicativos de interface de vários documentos (MDI)](multiple-document-interface-mdi-applications.md), pois esses formulários são o centro da interação do usuário.

No procedimento a seguir, você usará o Visual Studio para criar um formulário filho MDI que exibe <xref:System.Windows.Forms.RichTextBox> um controle, semelhante à maioria dos aplicativos de processamento de texto. Ao substituir o <xref:System.Windows.Forms> controle por outros controles, como o <xref:System.Windows.Forms.DataGridView> controle ou uma mistura de controles, você pode criar janelas filho MDI (e, por extensão, aplicativos MDI) com diversas possibilidades.

## <a name="create-mdi-child-forms"></a>Criar formulários filho MDI

1. Crie um novo projeto de aplicativo Windows Forms no Visual Studio. Na janela **Propriedades** do formulário, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> defina sua propriedade como `true` e sua `WindowsState` Propriedade como `Maximized`.

   Isso designa o formulário como um recipiente MDI para janelas filho.

2. No, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário. `Toolbox` Defina sua propriedade `Text` para o **Arquivo**.

3. Clique nas reticências (...) ao lado da propriedade Items e clique em **Adicionar** para adicionar dois itens de menu da ferramenta filho. Defina a propriedade `Text` para esses itens como **Novo** e **Janela**.

4. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.

5. Na caixa de diálogo **Adicionar novo item** , selecione **Windows Form** (no Visual Basic ou no Visual C#) ou **Windows Forms aplicativo (.net)** (no Visual C++) no painel **modelos** . Na caixa **Nome**, dê o nome **Form2** ao formulário. Selecione **abrir** para adicionar o formulário ao projeto.

    > [!NOTE]
    > O formulário MDI filho criado nesta etapa é um formulário padrão do Windows. Assim, ele tem uma <xref:System.Windows.Forms.Form.Opacity%2A> Propriedade, que permite controlar a transparência do formulário. No entanto <xref:System.Windows.Forms.Form.Opacity%2A> , a propriedade foi projetada para janelas de nível superior. Não use-a com formulários filho MDI, pois podem ocorrer problemas de pintura.

     Este formulário será o modelo para seus formulários filho MDI.

     O **Designer de Formulários do Windows** é aberto, exibindo **Form2**.

6. Na **Caixa de Ferramentas**, arraste um controle **RichTextBox** para o formulário.

7. Na janela **Propriedades**, defina a propriedade `Anchor` como **Superior, Esquerda** e a propriedade `Dock` como **Preenchimento**.

   Isso faz com <xref:System.Windows.Forms.RichTextBox> que o controle preencha completamente a área do formulário filho MDI, mesmo quando o formulário é redimensionado.

8. Clique duas vezes no **novo** item de menu para <xref:System.Windows.Forms.Control.Click> criar um manipulador de eventos para ele.

9. Insira um código semelhante ao seguinte para criar um novo formulário filho MDI quando o usuário clicar no item de menu **Novo**.

   > [!NOTE]
   > No exemplo a seguir, o manipulador de eventos manipula <xref:System.Windows.Forms.Control.Click> o evento `MenuItem2`para. Lembre-se de que, dependendo das especificidades da arquitetura de seu aplicativo, seu item de menu **Novo** não poderá ser `MenuItem2`.

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   No C++, adicione a seguinte `#include` diretiva na parte superior de Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. Na lista suspensa na parte superior da janela **Propriedades** , selecione a faixa de menu que corresponde à faixa de menu **arquivo** e defina a <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade para a janela. <xref:System.Windows.Forms.ToolStripMenuItem>

    Isso permite que o menu **janela** mantenha uma lista de janelas filho MDI abertas com uma marca de seleção ao lado da janela filho ativa.

11. Pressione **F5** para executar o aplicativo. Ao selecionar **Novo** do menu **Arquivo**, você pode criar novos formulários filho MDI, que são mantidos no item de menu **Janela**.

    > [!NOTE]
    > Quando um formulário filho MDI tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, uma estrutura de menu de itens de menu) e é aberto em um formulário pai MDI que tem <xref:System.Windows.Forms.MainMenu> um componente (com, normalmente, uma estrutura de menu de itens de menu), os itens de menu serão mesclados automaticamente Se você tiver definido a <xref:System.Windows.Forms.MenuItem.MergeType%2A> Propriedade (e, opcionalmente, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> a propriedade). Defina a <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade de ambos <xref:System.Windows.Forms.MainMenu> os componentes e todos os itens de menu do formulário filho como <xref:System.Windows.Forms.MenuMerge.MergeItems>. Além disso, defina <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> a propriedade para que os itens de menu de ambos os menus apareçam na ordem desejada. Além disso, tenha em mente que quando você fecha um formulário pai MDI, cada um dos formulários filho MDI gera <xref:System.Windows.Forms.Form.Closing> um evento antes <xref:System.Windows.Forms.Form.Closing> que o evento para o pai MDI seja gerado. <xref:System.Windows.Forms.Form.Closing> Cancelar o evento de um filho MDI não impedirá que o evento <xref:System.Windows.Forms.Form.Closing> do pai MDI seja gerado; no entanto, o <xref:System.ComponentModel.CancelEventArgs> argumento para o <xref:System.Windows.Forms.Form.Closing> evento do pai MDI agora será `true`definido como. Você pode forçar o fechamento do pai MDI e todos os formulários filho MDI ao definir <xref:System.ComponentModel.CancelEventArgs> o argumento `false`como.

## <a name="see-also"></a>Consulte também

- [Aplicativos da interface MDI (Interface de Vários Documentos)](multiple-document-interface-mdi-applications.md)
- [Como: Criar formulários pai MDI](how-to-create-mdi-parent-forms.md)
- [Como: Determinar o filho MDI ativo](how-to-determine-the-active-mdi-child.md)
- [Como: Enviar dados para o filho MDI ativo](how-to-send-data-to-the-active-mdi-child.md)
- [Como: Organizar formulários filho MDI](how-to-arrange-mdi-child-forms.md)
