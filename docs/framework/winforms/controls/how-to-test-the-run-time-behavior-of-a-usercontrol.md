---
title: 'Como: Testar o comportamento de tempo de execução de um UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: fece6fda33ddb86e0aff0584af97ba085dfa9e1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506362"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Como: Testar o comportamento de tempo de execução de um UserControl
Quando você desenvolve um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução. É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente. Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio. Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.  
  
> [!IMPORTANT]
>  Para o contêiner de teste carregar seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!NOTE]
>  Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>Testar o comportamento de tempo de execução de um UserControl  
  
1.  Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample**. Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Label> controlar dos **caixa de ferramentas** na superfície de design do controle.  
  
3.  Pressione F5 para compilar o projeto e executar o **Contêiner de teste do UserControl**. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.  
  
4.  Selecione o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade exibida na <xref:System.Windows.Forms.PropertyGrid> controle à direita do **visualização** painel. Altere seu valor para `ControlDark`. Observe que o controle é alterado para uma cor mais escura. Tente alterar outros valores de propriedade e observar o efeito em seu controle.  
  
5.  Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**. Observe que o controle é redimensionado para preencher o painel. Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.  
  
6.  Feche o contêiner de teste.  
  
7.  Adicione outro controle de usuário ao projeto **TestContainerExample**. Para obter detalhes, consulte [NIB: como: Adicionar itens existentes a um projeto](https://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
8.  No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Button> controlar dos **caixa de ferramentas** na superfície de design do controle.  
  
9. Pressione F5 para compilar o projeto e execute o contêiner de teste.  
  
10. Clique o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário.  
  
## <a name="testing-user-controls-from-another-project"></a>Testando controles de usuário de outro projeto  
 É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.  
  
#### <a name="to-test-user-controls-from-another-project"></a>Testar controles de outro projeto  
  
1.  Crie um projeto de biblioteca de controles do Windows chamado **TestContainerExample2**. Para obter detalhes, consulte [Modelo da Biblioteca de Controles do Windows](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  No **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.RadioButton> controlar dos **caixa de ferramentas** na superfície de design do controle.  
  
3.  Pressione F5 para compilar o projeto e execute o contêiner de teste. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no **visualização** painel.  
  
4.  Clique no botão **Carregar**.  
  
5.  Na caixa de diálogo **Abrir**, navegue até **TestContainerExample**.dll que você criou no procedimento anterior. Selecione **TestContainerExample**.dll e clique no botão **Abrir** para carregar os controles de usuário  
  
6.  Use o **Selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário da **TestContainerExample** projeto.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.UserControl>
- [Como: Criar controles compostos](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)
- [Passo a passo: Criando um controle composto com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Passo a passo: Criando um controle composto com VisualC#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Designer de Controle de Usuário](https://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
