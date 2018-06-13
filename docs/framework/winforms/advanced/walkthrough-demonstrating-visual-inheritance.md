---
title: 'Instruções passo a passo: demonstrando herança visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 61239d9b547be73a14618d41feeb9aeea9f8ded6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529695"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Instruções passo a passo: demonstrando herança visual
A herança visual permite que você veja os controles no formulário de base e adicione novos controles. Neste passo a passo, você criará um formulário de base e o compilará em uma biblioteca de classes. Você importará esta biblioteca de classes em outro projeto e criará um novo formulário que herda do formulário de base. Durante este passo a passo, você aprenderá a:  
  
-   Criar um projeto de biblioteca de classes que contém um formulário de base.  
  
-   Adicionar um botão com propriedades que as classes derivadas do formulário de base podem modificar.  
  
-   Adicionar um botão que não pode ser modificado por herdeiros do formulário de base.  
  
-   Criar um projeto que contém um formulário que herda de `BaseForm`.  
  
 Por fim, este passo a passo demonstrará a diferença entre controles particulares e protegidos em um formulário herdado.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!CAUTION]
>  Nem todos os controles dão suporte à herança visual de um formulário de base. Os seguintes controles não dão suporte ao cenário descrito neste passo a passo:  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  Esses controles no formulário herdado sempre são somente leitura, independentemente dos modificadores que você usar (`private`, `protected` ou `public`).  
  
## <a name="scenario-steps"></a>Etapas do cenário  
 A primeira etapa é criar o formulário de base.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Para criar um projeto de biblioteca de classes que contém um formulário de base  
  
1.  No menu **Arquivo**, escolha **Novo** e selecione **Projeto** para abrir a caixa de diálogo **Novo Projeto**.  
  
2.  Crie um aplicativo dos Windows Forms chamado `BaseFormLibrary`.  
  
3.  Para criar uma biblioteca de classes em vez de um aplicativo padrão dos Windows Forms, no **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto **BaseFormLibrary** e, em seguida, selecione **Propriedades**.  
  
4.  Nas propriedades do projeto, altere o **Tipo de saída** de **Aplicativo do Windows** para **Biblioteca de Classes**.  
  
5.  No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto e os arquivos no local padrão.  
  
 Os dois procedimentos seguintes adicionam botões ao formulário de base. Para demonstrar a herança visual, você dará aos botões diferentes níveis de acesso configurando suas propriedades `Modifiers`.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Para adicionar um botão que os herdeiros do formulário de base podem modificar  
  
1.  Abra **Form1** no designer.  
  
2.  Na guia **Todos os Windows Forms** da **Caixa de Ferramentas**, clique duas vezes em **Botão** para adicionar um botão ao formulário. Use o mouse para posicionar e redimensionar o botão.  
  
3.  Na janela Propriedades, defina as seguintes propriedades do botão:  
  
    -   Defina a propriedade **Texto** como **Say Hello**.  
  
    -   Defina a propriedade **(Nome)** como **btnProtected**.  
  
    -   Defina a propriedade **Modificadores** como **Protegido**. Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnProtected**.  
  
4.  Clique duas vezes no botão **Say Hello** para adicionar um manipulador de eventos para o evento **Clique**.  
  
5.  Adicione a seguinte linha de código ao manipulador de eventos:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Para adicionar um botão que não pode ser modificado por herdeiros do formulário de base  
  
1.  Passe para o modo de exibição de Design clicando na guia **Form1.vb [Design], Form1.cs [Design] ou Form1.jsl [Design]** acima do editor de código ou pressionando F7.  
  
2.  Adicione um segundo botão e defina suas propriedades da seguinte maneira:  
  
    -   Defina a propriedade **Texto** como **Say Goodbye**.  
  
    -   Defina a propriedade **(Nome)** como **btnPrivate**.  
  
    -   Defina a propriedade **(Nome)** como **Particular**. Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnPrivate**.  
  
3.  Clique duas vezes no botão **Say Goodbye** para adicionar um manipulador de eventos para o evento **Clique**. Coloque a seguinte linha de código no procedimento do evento:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Do menu **Compilação**, escolha **Compilar Biblioteca de BaseForm** para compilar a biblioteca de classes.  
  
     Após a biblioteca ter sido compilada, você pode criar um novo projeto que herda do formulário que você acabou de criar.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Para criar um projeto que contém um formulário que herda do formulário de base  
  
1.  No menu **Arquivo**, escolha **Adicionar** e selecione **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.  
  
2.  Crie um aplicativo dos Windows Forms chamado `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Para adicionar um formulário herdado  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest**, selecione **Adicionar** e selecione **Novo Item**.  
  
2.  Na caixa de diálogo **Adicionar Novo Item**, selecione a categoria **Windows Forms** (se você tiver uma lista de categorias) e selecione o modelo **Formulário Herdado**.  
  
3.  Deixe o nome padrão `Form2` e clique em **Adicionar**.  
  
4.  Na caixa de diálogo **Selecionador de Herança**, selecione **Form1** do projeto **BaseFormLibrary** como o formulário do qual herdar e clique em **OK**.  
  
     Isso cria um formulário no projeto **InheritanceTest** que deriva de formulário em **BaseFormLibrary**.  
  
5.  Abra o formulário herdado (**Form2**) no designer clicando duas vezes nele, se ele ainda não estiver aberto.  
  
     No designer, os botões herdados têm um símbolo (![Captura de tela de VisualBasicInheritanceSymbol](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) no canto superior, indicando que são herdados.  
  
6.  Selecione o botão **Say Hello** e observe as alças de redimensionamento. Como esse botão é protegido, os herdeiros podem movê-lo, redimensioná-lo, alterar sua legenda e fazer outras modificações.  
  
7.  Selecione o botão particular **Say Goodbye** e observe que ele não tem alças de redimensionamento. Além disso, na janela **Propriedades**, as propriedades deste botão ficam cinza para indicar que não podem ser modificadas.  
  
8.  Se você estiver usando o Visual c#:  
  
    1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1** no projeto **InheritanceTest** e selecione **Excluir**. Na caixa de mensagem que aparece, clique em **OK** para confirmar a exclusão.  
  
    2.  Abra o arquivo Program.cs e altere a linha `Application.Run(new Form1());` para `Application.Run(new Form2());`.  
  
9. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Definir como projeto de inicialização**.  
  
10. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Propriedades**.  
  
11. Na página de propriedades de **InheritanceTest**, defina o **Objeto de Inicialização** para ser o formulário herdado (**Form2**).  
  
12. Pressione F5 para executar o aplicativo e observe o comportamento do formulário herdado.  
  
## <a name="next-steps"></a>Próximas etapas  
 A herança para controles de usuário funciona basicamente da mesma forma. Abra um novo projeto de biblioteca de classes e adicione um controle de usuário. Coloque os controles constituintes nele e compile o projeto. Abra outro novo projeto de biblioteca de classes e adicione uma referência à biblioteca de classes compilada. Além disso, tente adicionar um controle herdado (por meio da caixa de diálogo **Adicionar Novos Itens**) ao projeto e usar o **Selecionador de Herança**. Adicionar um controle de usuário e alterar o `Inherits` (`:` no Visual c#) instrução. Para mais informações, consulte [Como herdar Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como Herdar Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Herança Visual dos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
