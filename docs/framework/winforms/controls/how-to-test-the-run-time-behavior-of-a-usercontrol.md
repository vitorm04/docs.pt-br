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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015774"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Como: Testar o comportamento de tempo de execução de um UserControl

Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução. É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente. Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio. Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.

> [!IMPORTANT]
> Para que o contêiner de teste carregue <xref:System.Windows.Forms.UserControl>seu, o controle deve ter pelo menos um construtor público.

> [!NOTE]
> Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testar o comportamento de tempo de execução de um UserControl

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample**.

2. Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Label> controle da caixa de **ferramentas** para a superfície de design do controle.

3. Pressione **F5** para compilar o projeto e executar o **contêiner de teste do UserControl**. O contêiner de teste é exibido <xref:System.Windows.Forms.UserControl> com seu no painel de **Visualização** .

4. Selecione a <xref:System.Windows.Forms.Control.BackColor%2A> propriedade exibida <xref:System.Windows.Forms.PropertyGrid> no controle à direita do painel de **Visualização** . Altere seu valor para **ControlDark**. Observe que o controle é alterado para uma cor mais escura. Tente alterar outros valores de propriedade e observar o efeito em seu controle.

5. Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**. Observe que o controle é redimensionado para preencher o painel. Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.

6. Feche o contêiner de teste.

7. Adicione outro controle de usuário ao projeto **TestContainerExample**.

8. Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.Button> controle da caixa de **ferramentas** para a superfície de design do controle.

9. Pressione **F5** para compilar o projeto e executar o contêiner de teste.

10. Clique<xref:System.Windows.Forms.ComboBox> no **controle Selecionar usuário** para alternar entre os dois controles de usuário.

## <a name="test-user-controls-from-another-project"></a>Testar controles de usuário de outro projeto

É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample2**.

2. Na **Designer de formulários do Windows**, arraste um <xref:System.Windows.Forms.RadioButton> controle da caixa de **ferramentas** para a superfície de design do controle.

3. Pressione **F5** para compilar o projeto e executar o contêiner de teste. O contêiner de teste é exibido <xref:System.Windows.Forms.UserControl> com seu no painel de **Visualização** .

4. Clique no botão **Carregar**.

5. Na caixa de diálogo **Abrir**, navegue até **TestContainerExample**.dll que você criou no procedimento anterior. Selecione **TestContainerExample**.dll e clique no botão **Abrir** para carregar os controles de usuário

6. Use<xref:System.Windows.Forms.ComboBox> o **controle Selecionar usuário** para alternar entre os dois controles de usuário do projeto **TestContainerExample** .

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.UserControl>
- [Como: Controles de composição de autor](how-to-author-composite-controls.md)
- [Passo a passo: Criando um controle composto](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
