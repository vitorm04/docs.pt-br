---
title: 'Tarefa 1: Crie um aplicativo do windows presentation foundation do windows'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031889"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Tarefa 1: Crie um aplicativo do windows presentation foundation do windows

Nesta tarefa, você criará um aplicativo Windows Presentation Foundation (WPF) vazio usando o modelo do Visual Studio de aplicativo WPF e adicionará referências aos assemblies de fluxo de trabalho de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] apropriados.  
  
## <a name="to-create-the-wpf-application-project"></a>Para criar o projeto de aplicativo de WPF

1. Abra o Visual Studio e, no menu **arquivo** , aponte para **novo**e clique em **projeto**.

2. Na caixa de diálogo **novo projeto** , selecione **Visual C#**  ou **Visual Basic** no painel **modelos instalados** no lado esquerdo da caixa. Se o idioma de sua escolha não aparecer, procure em **outros idiomas**.

3. Selecione **Windows** no painel **modelos instalados** .

4. No painel superior, confirme que (o valor padrão) **.NET Framework 4** foi selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.

5. Defina o nome do projeto como **HostingApplication** na parte inferior da janela.

6. Defina o nome da solução como **RehostingTheDesigner**.

7. Clique em **OK** para criar o projeto de aplicativo. O Visual Studio cria uma interface do usuário básica do WPF para seu aplicativo e inclui os arquivos XAML e code-behind apropriados.

8. Adicione referências a assemblies **WorkflowModel** . Para fazer isso, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **HostingApplication** e selecione **Adicionar referência**.

9. Na caixa de diálogo **Adicionar referência** , clique na guia **.net** , mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e clique em **OK**:

    - System.Activities
    - System.Activities.Presentation
    - System.Activities.Core.Presentation

10. Consulte [tarefa 2: hospedar o designer de fluxo de trabalho](task-2-host-the-workflow-designer.md) para saber como hospedar a tela de design do designer de fluxo de trabalho.

## <a name="see-also"></a>Consulte também

- [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)
- [Tarefa 2: Hospedar o Designer de Fluxo de Trabalho](task-2-host-the-workflow-designer.md)
