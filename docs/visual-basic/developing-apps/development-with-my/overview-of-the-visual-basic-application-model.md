---
title: "Visão geral do modelo de aplicativo do Visual Basic | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0925bb102c148480d82128b91cbf1762de24e7ec
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-the-visual-basic-application-model"></a>Visão geral do modelo de aplicativo do Visual Basic
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um modelo bem definido para controlar o comportamento de aplicativos Windows Forms: o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelo de aplicativo. Esse modelo inclui eventos para tratar do aplicativo inicialização e desligamento, bem como eventos para capturar exceções sem tratamento. Ele também fornece suporte para desenvolver aplicativos de instância única. O modelo de aplicativo é extensível, para que os desenvolvedores que precisam de mais controle podem personalizar seus métodos substituíveis.  
  
## <a name="uses-for-the-application-model"></a>Usa o modelo de aplicativo  
 Um aplicativo comum precisa executar tarefas quando ele é iniciado e desligado. Por exemplo, quando ele é inicializado, o aplicativo pode exibir uma tela inicial, estabelecer conexões de banco de dados, carregar um estado salvo e assim por diante. Quando o aplicativo é desligado, ele pode fechar conexões de banco de dados, salvar o estado atual e assim por diante. Além disso, o aplicativo pode executar código específico quando o aplicativo desliga para baixo inesperadamente, tais como durante uma exceção não tratada.  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Application model torna fácil criar um *instância única* aplicativo. Um aplicativo single-instance difere de um aplicativo normal em que apenas uma instância do aplicativo pode ser executado em uma hora. Uma tentativa de iniciar outra instância de um aplicativo de instância única resulta na instância original ser notificada — por meio do `StartupNextInstance` evento — que outra tentativa de lançamento foi feita. A notificação inclui argumentos de linha de comando da instância subsequente. A instância subsequente do aplicativo é fechada antes que qualquer inicialização possa ocorrer.  
  
 Um aplicativo single-instance inicia e verifica se ele é a primeira instância ou uma ocorrência subsequente do aplicativo:  
  
-   Se for a primeira instância, ele começa como de costume.  
  
-   Cada tentativa subsequente para iniciar o aplicativo, enquanto a primeira instância executa, resulta em comportamentos muito diferentes. A tentativa subsequente notifica a primeira instância sobre os argumentos de linha de comando e, em seguida, sai imediatamente. A primeira instância manipula o `StartupNextInstance` evento para determinar que argumentos de linha de comando da instância subsequente foram e continuará a ser executado.  
  
     Este diagrama mostra como uma instância subsequente sinaliza a primeira ocorrência.  
  
     ![Única imagem de aplicativo de instância](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 Manipulando o `StartupNextInstance` evento, você pode controlar como se comporta seu aplicativo de instância única. Por exemplo, Microsoft Outlook geralmente executa como um aplicativo de instância única; Quando o Outlook está em execução e você tentar iniciar o Outlook novamente, foco é deslocado para a instância original, mas outra instância não abre.  
  
## <a name="events-in-the-application-model"></a>Eventos no modelo do aplicativo  
 Os seguintes eventos são encontrados no modelo de aplicativo:  
  
-   **Inicialização do aplicativo**. A aplicativo gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>evento quando ele for iniciado.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> Ao manipular esse evento, você pode adicionar código que inicializa o aplicativo antes que o formulário principal seja carregado. O `Startup` evento também fornece execução para cancelamento do aplicativo durante essa fase do processo de inicialização, se desejado.  
  
     Você pode configurar o aplicativo para mostrar uma tela inicial, enquanto o código de inicialização do aplicativo é executado. Por padrão, o modelo do aplicativo suprime a abertura da tela quando tanto o `/nosplash` ou `-nosplash` argumento de linha de comando é usado.  
  
-   **Aplicativos de única instância**. O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>é gerado quando uma instância subsequente de um aplicativo de instância única é iniciado.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> O evento passa os argumentos de linha de comando da instância subsequente.  
  
-   **Exceções não tratadas**. Se o aplicativo encontra uma exceção não tratada, ele gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> O manipulador para esse evento pode examinar a exceção e determinar se deseja continuar a execução.  
  
     O `UnhandledException` evento não é aumentado em algumas circunstâncias. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
  
-   **Alterações de conectividade de rede**. Se a disponibilidade da rede do computador for alterado, o aplicativo gera o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
     O `NetworkAvailabilityChanged` evento não é aumentado em algumas circunstâncias. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
-   **Aplicativo encerrado**. O aplicativo fornece o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>evento para sinalizar quando ele está prestes a desligar.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> Nesse caso manipulador, você pode ter certeza de que as operações que seu aplicativo precisa para executar — fechar e salvar, por exemplo — são concluídas. Você pode configurar seu aplicativo para desligado quando o formulário principal fecha, ou para desligado somente quando todos os formulários fecham.  
  
## <a name="availability"></a>Disponibilidade  
 Por padrão, o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Application model está disponível para projetos Windows Forms. Se você configurar o aplicativo para usar um objeto inicialização diferente, ou iniciar o código do aplicativo com um personalizado `Sub Main`, então esse objeto ou classe talvez precise fornecer uma implementação de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe para usar o modelo de aplicativo.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Para obter informações sobre como alterar o objeto de inicialização, consulte [página de aplicativo, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
