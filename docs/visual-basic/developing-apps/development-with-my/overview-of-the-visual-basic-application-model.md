---
title: Visão geral do modelo de aplicativo do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 5194810574f594e2c117fef8d8998b7ecebbc981
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591593"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visão geral do modelo de aplicativo do Visual Basic
Visual Basic fornece um modelo bem definido para controlar o comportamento de aplicativos Windows Forms: o modelo de aplicativo do Visual Basic. Esse modelo inclui eventos para lidar com o aplicativo inicialização e desligamento, bem como dos eventos para capturar exceções não manipuladas. Ele também fornece suporte para desenvolver aplicativos de instância única. O modelo de aplicativo é extensível, para que os desenvolvedores que precisam de mais controle podem personalizar seus métodos substituíveis.  
  
## <a name="uses-for-the-application-model"></a>Usos para o modelo de aplicativo  
 Precisa de um aplicativo típico para executar tarefas quando ele é iniciado e desligado. Por exemplo, quando ele é iniciado, o aplicativo pode exibir uma tela inicial, estabelecer conexões de banco de dados, carregar um estado salvo e assim por diante. Quando o aplicativo é desligado, ele pode fechar conexões de banco de dados, salvar o estado atual e assim por diante. Além disso, o aplicativo pode executar código específico quando o aplicativo for suspenso inesperadamente, tais como durante uma exceção sem tratamento.  
  
 O modelo de aplicativo do Visual Basic torna fácil criar um *instância única* aplicativo. Um aplicativo de instância única difere de um aplicativo normal em que apenas uma instância do aplicativo pode ser executado em um momento. Uma tentativa de iniciar outra instância de um aplicativo de instância única resulta na instância original ser notificada — por meio do `StartupNextInstance` evento — que outra tentativa de lançamento foi feita. A notificação inclui argumentos de linha de comando da instância subsequente. A instância subsequente do aplicativo é fechada antes que qualquer inicialização possa ocorrer.  
  
 Um aplicativo de instância única inicia e verifica se ele é a primeira instância ou uma instância subsequente do aplicativo:  
  
-   Se for a primeira instância, ele começa como de costume.  
  
-   Cada tentativa subsequente para iniciar o aplicativo, enquanto a primeira instância executa, resulta em comportamento muito diferente. A tentativa subsequente notifica a primeira instância sobre os argumentos de linha de comando e, em seguida, sai imediatamente. A primeira instância manipula o `StartupNextInstance` evento para determinar que argumentos de linha de comando da instância subsequente foram e continuará a ser executado.  
  
     Este diagrama mostra como uma instância subsequente sinaliza a primeira instância.  
  
     ![Imagem de aplicativo de instância única de](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 Manipulando o `StartupNextInstance` eventos, você pode controlar o comportamento do seu aplicativo de instância única. Por exemplo, Microsoft Outlook normalmente é executado como um aplicativo de instância única. Quando o Outlook está em execução e você tentar iniciar o Outlook novamente, o foco muda para a instância original mas outra instância não abre.  
  
## <a name="events-in-the-application-model"></a>Eventos no modelo do aplicativo  
 Os eventos a seguir são encontrados no modelo de aplicativo:  
  
-   **Inicialização do aplicativo**. A aplicativo gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> evento quando ele for iniciado. Manipulando esse evento, você pode adicionar o código que inicializa o aplicativo antes que o formulário principal seja carregado. O `Startup` evento também fornece execução para cancelamento do aplicativo durante essa fase do processo de inicialização, se desejado.  
  
     Você pode configurar o aplicativo para mostrar uma tela inicial, enquanto o código de inicialização do aplicativo é executado. Por padrão, o modelo do aplicativo suprime a tela tela quando tanto o `/nosplash` ou `-nosplash` argumento de linha de comando é usado.  
  
-   **Aplicativos de única instância**. O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> é gerado quando uma instância subsequente de um aplicativo de instância única é iniciado. O evento passa os argumentos de linha de comando da instância subsequente.  
  
-   **Exceções não tratadas**. Se o aplicativo encontra uma exceção sem tratamento, ele gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> evento. O manipulador para esse evento pode examinar a exceção e determinar se deseja continuar a execução.  
  
     O `UnhandledException` evento não é gerado em algumas circunstâncias. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Alterações de conectividade de rede**. Se a disponibilidade da rede do computador for alterada, o aplicativo gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> evento.  
  
     O `NetworkAvailabilityChanged` evento não é gerado em algumas circunstâncias. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Aplicativo encerrado**. O aplicativo fornece o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> evento para sinalizar quando ele está prestes a desligar. Nesse evento manipulador, você pode ter certeza de que as operações que seu aplicativo precisa para executar — fechar e salvar, por exemplo — são concluídas. Você pode configurar seu aplicativo para desligado quando fecha o formulário principal ou para desligado somente quando todos os formulários fecham.  
  
## <a name="availability"></a>Disponibilidade  
 Por padrão, o modelo de aplicativo do Visual Basic está disponível para projetos de formulários do Windows. Se você configurar o aplicativo para usar um objeto diferente de inicialização, ou o código do aplicativo com um personalizado `Sub Main`, então esse objeto ou classe talvez precise fornecer uma implementação de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe para usar o modelo de aplicativo. Para obter informações sobre como alterar o objeto de inicialização, consulte [página de aplicativo, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
