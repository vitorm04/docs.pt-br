---
title: Solucionando problemas de criação do controle e do componente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: 9100d6dc41f982af340d747ad447009a183b3c7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540973"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Solucionando problemas de criação do controle e do componente
Este tópico lista os seguintes problemas comuns que podem surgir ao desenvolver componentes e controles. Para obter mais informações, consulte [Programando com componentes](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
-   Não é possível adicionar o controle à caixa de ferramentas  
  
-   Não é possível depurar o componente nem o controle de usuário do Windows Forms  
  
-   O evento é gerado duas vezes no componente ou no controle herdado  
  
-   Erro de tempo de design: "Falha em criar o componente '*Nome do Componente*'"  
  
-   STAThreadAttribute  
  
-   O ícone do componente não aparece na caixa de ferramentas  
  
## <a name="cannot-add-control-to-toolbox"></a>Não é possível adicionar o controle à caixa de ferramentas  
 Se você quiser adicionar um controle personalizado criado em outro projeto ou um controle de terceiros à **Caixa de Ferramentas**, faça isso manualmente. Se o projeto atual contiver seu controle ou componente, ele deverá aparecer na **Caixa de Ferramentas** automaticamente. Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Para adicionar um controle à Caixa de Ferramentas  
  
1.  Clique com o botão direito do mouse em **Caixa de Ferramentas** e selecione **Escolher Itens** no menu de atalho.  
  
2.  Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, adicione o componente:  
  
    -   Se você quiser adicionar um controle ou um componente do .NET Framework, clique na guia **Componentes do .NET Framework**.  
  
         – ou –  
  
    -   Se você quiser adicionar um componente COM ou um controle ActiveX, clique na guia **Componentes COM**.  
  
3.  Se o controle estiver listado na caixa de diálogo, confirme que ele está selecionado e, em seguida, clique em **OK**.  
  
     O controle é adicionado à **Caixa de Ferramentas**.  
  
4.  Se seu controle não estiver listado na caixa de diálogo, faça o seguinte:  
  
    1.  Clique no botão **Procurar**.  
  
    2.  Navegue até a pasta que contém o arquivo .dll com o controle.  
  
    3.  Selecione o arquivo .dll e clique em **Abrir**.  
  
         Seu controle aparece na caixa de diálogo.  
  
    4.  Confirme que o controle está selecionado e, em seguida, clique em **OK**.  
  
         Seu controle é adicionado à **Caixa de Ferramentas**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Não é possível depurar o componente nem o controle de usuário do Windows Forms  
 Se o seu controle deriva o <xref:System.Windows.Forms.UserControl> classe, você pode depurar seu comportamento de tempo de execução com o contêiner de teste. Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).  
  
 Outros controles e componentes personalizados não são projetos autônomos. Eles devem ser hospedados por um aplicativo como um projeto do Windows Forms. Para depurar um controle ou um componente, adicione-o a um projeto do Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Para depurar um controle ou um componente  
  
1.  No menu **Compilar**, clique em **Compilar Solução** para compilar sua solução.  
  
2.  No menu **Arquivo**, escolha **Adicionar** e, em seguida, **Novo Projeto** para adicionar um projeto de teste ao seu aplicativo.  
  
3.  Na caixa de diálogo **Adicionar Novo Projeto**, escolha **Aplicativos do Windows** para o tipo de projeto.  
  
4.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** para o novo projeto. No menu de atalho, clique em **Adicionar Referência** para adicionar uma referência ao projeto que contém o controle ou o componente.  
  
5.  Crie uma instância do seu controle ou componente no projeto de teste. Se o componente estiver na **Toolbox**, você poderá arrastá-lo para a superfície do designer ou criar a instância programaticamente, conforme mostrado no exemplo de código a seguir.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Agora você pode depurar seu componente ou controle como de costume.  
  
 Para obter mais informações sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) e [Passo a passo: depurando personalizar controles personalizados do Windows Forms no tempo de design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>O evento é gerado duas vezes no componente ou no controle herdado  
 Isso provavelmente é devido a uma cláusula `Handles` duplicada. Para obter mais informações, consulte [Solução de problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Erro de tempo de design: "Falha em criar o componente 'Nome do Componente'"  
 Seu componente ou controle deve fornecer um construtor padrão sem parâmetros. Quando o ambiente de design cria uma instância do seu componente ou controle, ele não tenta fornecer nenhum parâmetro para as sobrecargas do construtor que aceitam parâmetros.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 O <xref:System.STAThreadAttribute> informa o common language runtime (CLR) do Windows Forms usa o modelo STA. Você poderá perceber um comportamento não intencional se não aplicar esse atributo ao método `Main` do aplicativo do Windows Forms. Por exemplo, imagens de plano de fundo não podem aparecer para controles como <xref:System.Windows.Forms.ListView>. Alguns controles também podem exigir esse atributo para um comportamento correto de Preenchimento Automático e do tipo "arrastar e soltar".  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>O ícone do componente não aparece na caixa de ferramentas  
 Quando você usa <xref:System.Drawing.ToolboxBitmapAttribute> para associar um ícone ao seu componente personalizado, o bitmap não aparece na caixa de ferramentas para componentes gerado automaticamente. Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**. Para obter mais informações, consulte [Como fornecer um bitmap da caixa de ferramentas para um controle](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Como testar o comportamento de tempo de execução de um UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [Criação de componentes](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [Desenvolvimento de tempo de Design de solução de problemas](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Programação com componentes](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
