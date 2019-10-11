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
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180203"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Como: Testar o comportamento de tempo de execução de um UserControl

Ao desenvolver um <xref:System.Windows.Forms.UserControl>, você precisa testar seu comportamento de tempo de execução. É possível criar um projeto de aplicativo separado do Windows e colocar o controle em um formulário de teste, porém esse procedimento é inconveniente. Uma maneira mais rápida e fácil é usar o **Contêiner de teste de UserControl** fornecido pelo Visual Studio. Esse contêiner de teste é iniciado diretamente do seu projeto de biblioteca de controles do Windows.

> [!IMPORTANT]
> Para que o contêiner de teste carregue seu <xref:System.Windows.Forms.UserControl>, o controle deve ter pelo menos um construtor público.

> [!NOTE]
> Não é possível testar um controle do Visual C++ usando o **Contêiner de teste de UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Testar o comportamento de tempo de execução de um UserControl

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample**.

2. Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.Label> da caixa de **ferramentas** para a superfície de design do controle.

3. Pressione <kbd>F5</kbd> para compilar o projeto e executar o **contêiner de teste do UserControl**. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .

4. Selecione a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> exibida no controle <xref:System.Windows.Forms.PropertyGrid> à direita do painel de **Visualização** . Altere seu valor para **ControlDark**. Observe que o controle é alterado para uma cor mais escura. Tente alterar outros valores de propriedade e observar o efeito em seu controle.

5. Clique na caixa de seleção **Controle de usuário Dock Fill** abaixo do painel **Visualização**. Observe que o controle é redimensionado para preencher o painel. Redimensione o contêiner de teste e observe como o controle é redimensionado com o painel.

6. Feche o contêiner de teste.

7. Adicione outro controle de usuário ao projeto **TestContainerExample**.

8. Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.Button> da caixa de **ferramentas** para a superfície de design do controle.

9. Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste.

10. Clique em **selecionar controle de usuário** <xref:System.Windows.Forms.ComboBox> para alternar entre os dois controles de usuário.

## <a name="test-user-controls-from-another-project"></a>Testar controles de usuário de outro projeto

É possível testar os controles de usuário de outros projetos no contêiner de teste do seu projeto atual.

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **TestContainerExample2**.

2. Na **Designer de formulários do Windows**, arraste um controle <xref:System.Windows.Forms.RadioButton> da caixa de **ferramentas** para a superfície de design do controle.

3. Pressione <kbd>F5</kbd> para compilar o projeto e executar o contêiner de teste. O contêiner de teste é exibido com seu <xref:System.Windows.Forms.UserControl> no painel de **Visualização** .

4. Clique no botão **Carregar**.

5. Na caixa de diálogo **abrir** , navegue até *TestContainerExample. dll*, que você criou no procedimento anterior. Selecione *TestContainerExample. dll* e clique no botão **abrir** para carregar os controles de usuário.

6. Use o @no__t de **controle Selecionar usuário** -1 para alternar entre os dois controles de usuário do projeto **TestContainerExample** .

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.UserControl>
- [Como: Criar controles de composição @ no__t-0
- [Passo a passo: Criando um controle composto @ no__t-0
- [Designer de Controle de Usuário](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
