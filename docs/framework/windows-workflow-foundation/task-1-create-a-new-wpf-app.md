---
title: 'Tarefa 1: Criar um aplicativo do Windows Presentation Foundation do Windows'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 63b84e4fd2c88d98fbf417ee1f55ec203d295116
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320373"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Tarefa 1: Criar um aplicativo do Windows Presentation Foundation do Windows
Nesta tarefa, você criará um aplicativo vazio do Windows Presentation Foundation (WPF) usando o modelo de aplicativo WPF Visual Studio e adicionar referências a apropriado [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] assemblies de fluxo de trabalho.  
  
### <a name="to-create-the-wpf-application-project"></a>Para criar o projeto de aplicativo de WPF  
  
1. Abra o Visual Studio e, na **arquivo** , aponte para **New**e, em seguida, clique em **projeto**.  
  
2. No **novo projeto** diálogo caixa, selecione **Visual C#**  ou **Visual Basic** do **modelos instalados** painel à esquerda lado da caixa. Se o idioma de sua escolha não aparecer, procure **outras linguagens**.  
  
3. Selecione **Windows** na **modelos instalados** painel.  
  
4. No painel superior, confirme se (o valor padrão) **.NET Framework 4** tiver sido selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.  
  
5. Defina o nome do projeto para **HostingApplication** na parte inferior da janela.  
  
6. Defina o nome da solução **RehostingTheDesigner**.  
  
7. Clique em **Okey** para criar o projeto de aplicativo. Visual Studio cria uma UI WPF básica para seu aplicativo e inclui o XAML apropriado e arquivos code-behind.  
  
8. Adicione referências aos **WorkflowModel** assemblies. Para fazer isso, em **Gerenciador de soluções**, clique com botão direito do **HostingApplication** do projeto e selecione **adicionar referência**.  
  
9. No **adicionar referência** caixa de diálogo, clique o **.NET** guia, mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e, em seguida, clique em **Okey**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Clique em **OK**.  
  
11. Consulte [tarefa 2: Hospedar o Designer de fluxo de trabalho](task-2-host-the-workflow-designer.md) para aprender a hospedar a tela de design do designer de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também

- [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)
- [Tarefa 2: Hospedar o Designer de fluxo de trabalho](task-2-host-the-workflow-designer.md)
