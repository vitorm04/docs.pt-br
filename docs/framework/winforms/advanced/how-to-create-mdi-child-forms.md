---
title: 'Como: Criar formulários filho MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 6ff5873fc2e0a321ad682805457be87c609972fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708451"
---
# <a name="how-to-create-mdi-child-forms"></a>Como: Criar formulários filho MDI
Os formulários filho MDI são um elemento essencial dos [Aplicativos de Interface MDI](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), pois esses formulários são o centro da interação do usuário.  
  
 No procedimento a seguir, você criará um formulário filho MDI que exibe um <xref:System.Windows.Forms.RichTextBox> controle, semelhante aos aplicativos de processamento de texto. Substituindo o <xref:System.Windows.Forms> controlar com outros controles, como o <xref:System.Windows.Forms.DataGridView> controle ou uma mistura de controles permite que você crie janelas filho MDI (e, por extensão, aplicativos MDI) com diversas possibilidades.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-mdi-child-forms"></a>Para criar formulários filho MDI  
  
1.  Criar um novo projeto dos Windows Forms. No **as propriedades do Windows** para o formulário, defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade a ser `true`e seu `WindowsState` propriedade `Maximized`.  
  
     Isso designa o formulário como um recipiente MDI para janelas filho.  
  
2.  Dos `Toolbox`, arraste um <xref:System.Windows.Forms.MenuStrip> controle ao formulário. Defina sua propriedade `Text` para o **Arquivo**.  
  
3.  Clique nas reticências (...) ao lado da propriedade **Itens** e clique em **Adicionar** para adicionar dois itens de menu filho da faixa de ferramentas. Defina a propriedade `Text` para esses itens como **Novo** e **Janela**.  
  
4.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Adicionar novo item**.  
  
5.  No **Adicionar Novo Item** caixa de diálogo, selecione **formulário do Windows** (no Visual Basic ou no Visual c#) ou **aplicativo de formulários do Windows (.NET)** (em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) do  **Modelos** painel. Na caixa **Nome**, dê o nome **Form2** ao formulário. Clique no botão **Abrir** para adicionar o formulário ao projeto.  
  
    > [!NOTE]
    >  O formulário MDI filho criado nesta etapa é um formulário padrão do Windows. Como tal, ele tem um <xref:System.Windows.Forms.Form.Opacity%2A> propriedade, que permite que você controle a transparência do formulário. No entanto, o <xref:System.Windows.Forms.Form.Opacity%2A> propriedade foi projetada para janelas de nível superior. Não use-a com formulários filho MDI, pois podem ocorrer problemas de pintura.  
  
     Este formulário será o modelo para seus formulários filho MDI.  
  
     O **Designer de Formulários do Windows** é aberto, exibindo **Form2**.  
  
6.  Na **Caixa de Ferramentas**, arraste um controle **RichTextBox** para o formulário.  
  
7.  Na janela **Propriedades**, defina a propriedade `Anchor` como **Superior, Esquerda** e a propriedade `Dock` como **Preenchimento**.  
  
     Isso faz com que o <xref:System.Windows.Forms.RichTextBox> controle para preencher completamente a área do formulário filho MDI, mesmo quando o formulário é redimensionado.  
  
8.  Clique duas vezes o **New** item de menu para criar um <xref:System.Windows.Forms.Control.Click> manipulador de eventos para ele.  
  
9. Insira um código semelhante ao seguinte para criar um novo formulário filho MDI quando o usuário clicar no item de menu **Novo**.  
  
    > [!NOTE]
    >  No exemplo a seguir, o manipulador de eventos manipula o <xref:System.Windows.Forms.Control.Click> evento para `MenuItem2`. Lembre-se de que, dependendo das especificidades da arquitetura de seu aplicativo, seu item de menu **Novo** não poderá ser `MenuItem2`.  
  
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
  
     Em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], adicione a seguinte diretiva `#include` na parte superior do Form1.h:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. Na lista suspensa na parte superior da **propriedades** janela, selecione a faixa de menu que corresponde à **arquivo** faixa do menu e defina o <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade na janela <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Isso permitirá que o menu **Janela** mantenha uma lista de janelas filho MDI abertas com uma marca de seleção próxima à janela filho ativa.  
  
11. Pressione F5 para executar o aplicativo. Ao selecionar **Novo** do menu **Arquivo**, você pode criar novos formulários filho MDI, que são mantidos no item de menu **Janela**.  
  
    > [!NOTE]
    >  Quando um formulário MDI filho tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, uma estrutura de menu de itens de menu) e ele é aberto em um formulário pai MDI que tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, uma estrutura de menu de itens de menu), o menu itens mesclará automaticamente Se você tiver definido o <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade (e, opcionalmente, o <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> propriedade). Defina as <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade de ambos <xref:System.Windows.Forms.MainMenu> componentes e todos os itens de menu do formulário filho para <xref:System.Windows.Forms.MenuMerge.MergeItems>. Além disso, defina o <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> propriedade para que os itens de menu de ambos os menus aparecem na ordem desejada. Além disso, tenha em mente que, quando você fecha um formulário pai MDI, cada um dos filhos MDI forms gera uma <xref:System.Windows.Forms.Form.Closing> evento antes do <xref:System.Windows.Forms.Form.Closing> é gerado para o pai da MDI. Cancelando um filho MDI <xref:System.Windows.Forms.Form.Closing> evento não impedirá que o pai MDI <xref:System.Windows.Forms.Form.Closing> evento seja gerado; no entanto, o <xref:System.ComponentModel.CancelEventArgs> argumento para o pai MDI <xref:System.Windows.Forms.Form.Closing> evento agora será definido como `true`. Você pode forçar o pai MDI e todos os filhos MDI, configurando o <xref:System.ComponentModel.CancelEventArgs> argumento para `false`.  
  
## <a name="see-also"></a>Consulte também
- [Aplicativos da interface MDI (Interface de Vários Documentos)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [Como: Criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Como: Determinar o filho MDI ativo](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [Como: Enviar dados para o filho MDI ativo](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
- [Como: Organizar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
