---
title: 'Tarefa 1: Crie um aplicativo do windows presentation foundation do windows'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517943"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Tarefa 1: Crie um aplicativo do windows presentation foundation do windows
Nesta tarefa, você criará um aplicativo do Windows Presentation Foundation (WPF) vazio usando o modelo de aplicativo WPF Visual Studio e adicionar referências ao apropriado [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] assemblies de fluxo de trabalho.  
  
### <a name="to-create-the-wpf-application-project"></a>Para criar o projeto de aplicativo de WPF  
  
1.  Abra o Visual Studio e no **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, selecione o **Visual C#** ou **Visual Basic** do **modelos instalados** painel no lado esquerdo do a caixa. Se o idioma de sua escolha não aparecer, procure em **outras linguagens**.  
  
3.  Selecione **Windows** no **modelos instalados** painel.  
  
4.  No painel superior, confirme se (o valor padrão) **.NET Framework 4** tiver sido selecionado na caixa de listagem suspensa e, em seguida, selecione **aplicativo WPF**.  
  
5.  Defina o nome do projeto para **HostingApplication** na parte inferior da janela.  
  
6.  Defina o nome de solução para **RehostingTheDesigner**.  
  
7.  Clique em **Okey** para criar o projeto de aplicativo. Visual Studio cria uma UI WPF básica para seu aplicativo e inclui o XAML apropriado e os arquivos code-behind.  
  
8.  Adicione referências a **WorkflowModel** assemblies. Para fazer isso, em **Solution Explorer**, com o botão direito do **HostingApplication** do projeto e selecione **adicionar referência**.  
  
9. No **adicionar referência** caixa de diálogo, clique o **.NET** guia, mantenha pressionada a tecla CTRL, selecione os seguintes assemblies e, em seguida, clique em **Okey**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Clique em **OK**.  
  
11. Consulte [tarefa 2: hospedar Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) para aprender a hospedar a tela de design do designer de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedando novamente o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Tarefa 2: Hospedar o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
