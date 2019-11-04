---
title: Como testar o comportamento de tempo de execução de um UserControl
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be6c913c43e3559806bc9f38a9c3152b544e4c07
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455528"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Como testar o comportamento em tempo de execução de um UserControl

Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução. É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente. Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio. Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.

> [!IMPORTANT]
> Para que o contêiner de teste carregue seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.

> [!NOTE]
> Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testar o comportamento de tempo de execução de um UserControl

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample**.

2. Na **Designer de formulários do Windows**, arraste um controle de <xref:System.Windows.Forms.Label> da **caixa de ferramentas** para a superfície de design do controle.

3. Pressione <kbd>F5</kbd> para compilar o projeto e executar o **contêiner de teste do UserControl**. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .

4. Selecione a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> exibida no controle de <xref:System.Windows.Forms.PropertyGrid> à direita do painel de **Visualização** . Altere seu valor para **ControlDark**. Observe que o controle é alterado para uma cor mais escura. Tente alterar outros valores de propriedade e observar o efeito em seu controle.

5. Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**. Observe que o controle é redimensionado para preencher o painel. Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.

6. Feche o contêiner de teste.

7. Adicione outro controle de usuário ao projeto **TestContainerExample**.

8. Na **Designer de formulários do Windows**, arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para a superfície de design do controle.

9. Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste.

10. Clique no <xref:System.Windows.Forms.ComboBox> **selecionar controle do usuário** para alternar entre os dois controles de usuário.

## <a name="test-user-controls-from-another-project"></a>Testar controles de usuário de outro projeto

É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample2**.

2. Na **Designer de formulários do Windows**, arraste um controle de <xref:System.Windows.Forms.RadioButton> da **caixa de ferramentas** para a superfície de design do controle.

3. Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .

4. Clique no botão **Carregar**.

5. Na caixa de diálogo **abrir** , navegue até *TestContainerExample. dll*, que você criou no procedimento anterior. Selecione *TestContainerExample. dll* e clique no botão **abrir** para carregar os controles de usuário.

6. Use a <xref:System.Windows.Forms.ComboBox> **selecionar controle de usuário** para alternar entre os dois controles de usuário do projeto **TestContainerExample** .

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.UserControl>
- [Como criar controles de composição](how-to-author-composite-controls.md)
- [Walkthrough: Criando um controle composto](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
