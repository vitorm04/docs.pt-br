---
title: "Vis&#227;o geral do modelo de aplicativo do Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My.Application, Modelo de aplicativo do Visual Basic"
  - "Modelo de aplicativo do Visual Basic"
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral do modelo de aplicativo do Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece um modelo bem definido para controlar o comportamento de aplicativos Windows Forms: o  modelo de aplicativo do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Este modelo inclui eventos para tratar do aplicativo de inicialização e desligamento, assim como eventos para exceções de captura não tratadas.  Ele também fornece suporte para desenvolver aplicativos de instância única.  O modelo do aplicativo é extensível, então os desenvolvedores que precisam ter mais controle podem personalizar seus métodos substituíveis.  
  
## Usos Para o Modelo do Aplicativo  
 Um aplicativo comum precisa executar tarefas quando é inicializado e finalizado.  Por exemplo, quando ele inicializado, o aplicativo pode exibir um tela inicial, estabelecer conexões de banco de dados, carregar um estado salvo e assim por diante.  Quando o aplicativo desliga, ele pode fechar conexões de banco de dados, salvar o estado atual e assim por diante.  Além disso, o aplicativo pode executar código específico quando o aplicativo desliga inesperadamente, tais como durante uma exceção não tratada.  
  
 O modelo de aplicativo do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] torna fácil criar um aplicativo *single\-instance*.  Um aplicativo single\-instance difere de um aplicativo normal em que apenas uma instância do aplicativo pode estar executando ao mesmo tempo.  Uma tentativa de iniciar outra instância de um aplicativo de instância única resulta na instância original ser notificada — por meio do evento `StartupNextInstance` — que outra tentativa de abertura foi feita.  A notificação inclui a ocorrência subseqüente dos argumentos de linha de comando.  Então a ocorrência subseqüente do aplicativo é fechada para que qualquer inicialização possa ocorrer.  
  
 Um aplicativo single\-instance inicia e verifica se ele é a primeira instância ou uma ocorrência subseqüente do aplicativo:  
  
-   Se ele for a primeira instância, ele começa como de costume.  
  
-   Cada tentativa subseqüente para iniciar o aplicativo, enquanto a primeira instância executa, resulta em comportamentos muito diferentes.  A tentativa subseqüente notifica a primeira instância sobre os argumentos de linha de comando e, então, imediatamente sai.  A primeira instância manipula o evento `StartupNextInstance` para determinar quais foram os argumentos de linha de comando das instâncias subseqüente, e continuam a ser executados.  
  
     Este diagrama mostra como uma instância subseqüente sinaliza a primeira ocorrência.  
  
     ![Imagem do aplicativo de instância única](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.png "SingleInstance")  
  
 Ao manipular o evento `StartupNextInstance`, você pode controlar como se comporta seu aplicativo de instância única.  Por exemplo, Microsoft Outlook geralmente executa como um aplicativo de instância única; quando Outlook estiver sendo executado e você tentar iniciar o Outlook novamente, o foco será deslocado para a instância original, mas outra instância não abre.  
  
## Eventos no Modelo do Aplicativo  
 Os eventos a seguir são encontrados no modelo aplicativo:  
  
-   **Application startup**.  O aplicativo gera o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> quando ele.  Ao manipular esse evento, você pode adicionar o código que inicializa o aplicativo antes que o formulário principal seja carregado.  O evento `Startup` também fornece cancelando da execução do aplicativo durante essa fase do processo de inicialização, se desejado.  
  
     Você pode configurar o aplicativo para mostrar um tela inicial enquanto o aplicativo executa o código de inicialização.  Por padrão, o modelo do aplicativo suprime a tela inicial quando os argumentos de linha de comando `/nosplash` ou `-nosplash` são usados.  
  
-   **Single\-instance applications**.  O evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> é gerado quando uma instância subseqüente de um aplicativo de instância única.  O evento passa os argumentos de linha de comando da instância subseqüente.  
  
-   **Unhandled exceptions**.  Se o aplicativo encontra uma exceção não tratada, gera o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> .  O tratador daquele evento pode examinar a exceção e determinar se deseja continuar a execução.  
  
     O evento `UnhandledException` não é gerado em algumas circunstâncias.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Network\-connectivity changes**.  Se a disponibilidade da rede muda, o aplicativo gera o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> .  
  
     O evento `NetworkAvailabilityChanged` não é gerado em algumas circunstâncias.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Application shut down**.  O aplicativo fornece o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> para sinalizar quando está prestes a ser desligado.  Naquele tratador de eventos, é possível certificar\-se de que as operações que seu aplicativo precisa executar — fechar e salvar, por exemplo — estão concluídas.  Você pode configurar seu aplicativo para ser desligado quando o formulário principal fecha, ou para ser desligado somente quando todos os formulários fecham.  
  
## Disponibilidade  
 Por padrão, o modelo de aplicativo de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] está disponível para projetos Windows Forms.  Se você configurar o aplicativo para usar um objeto diferente de inicialização, ou iniciar o código do aplicativo com um `Sub Main` personalizado, então esse objeto ou classe talvez precise fornecer uma implementação da classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> para usar o modelo de aplicativo.  Para obter informações sobre como alterar o objeto de inicialização, consulte [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)