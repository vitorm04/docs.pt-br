---
title: Atraso absoluto
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 3a104f6b879e9cdc899bad2201ad1ed320a38a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518379"
---
# <a name="absolute-delay"></a>Atraso absoluto
O principal cenário para esse exemplo é atrasar até <xref:System.DateTime> especificado usando temporizadores duráveis em um aplicativo de fluxo de trabalho. Isso é diferente de usar a atividade interno de <xref:System.Activities.Statements.Delay> porque isso permitirá que você atrasar apenas para <xref:System.TimeSpan> determinado (ou o número de minutos/segundos).  
  
 Alguns cenários da vida real em que você pode querer fazer essa distinção incluir o seguinte:  
  
1.  Você deseja atrasar enviar um email por 30 segundos para certificar-se de que você não tiver feito erros.  
  
2.  Você está trabalhando fora do tempo estipulado e deseja atrasar todos os seus email até que horários de negócios normais (como am 8).  
  
## <a name="demonstrates"></a>Demonstra  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension> para implementar o atraso absoluto  
  
2.  Persistência de foundation usando <xref:System.Activities.WorkflowApplication> para timers duráveis  
  
3.  Uso de <xref:System.Activities.NativeActivity%601> para usar pontos de extensibilidade  
  
4.  Uso de <xref:System.Activities.CodeActivity%601> na atividade de SendEmail  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Fluxo de trabalho XAML-only  
  
 Este exemplo demonstra como criar uma atividade personalizado que reduz <xref:System.DateTime> e use timers duráveis para registrar a duração de atraso. Ao usar timers duráveis, você deve usar <xref:System.Activities.NativeActivity> para criar um marcador, porque você precisará registrar este indexador com a extensão timer. Nesse exemplo, quando o timer durável expira, o método de `OnTimerExpired` será chamado. Certifique-se de que você está adicionando a extensão do timer o evento de <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> para garantir que você está fornecendo o tempo de execução essas informações. O único o outro detalhes de implementação é que você precisará implementar a lógica para converter de <xref:System.DateTime> a <xref:System.TimeSpan>, como timers duráveis recolhem somente <xref:System.DateTime>. Observe que há um lapso pequeno com precisão fazendo  
  
> [!NOTE]
>  Há uma perda de precisão pequena converter de <xref:System.DateTime> a <xref:System.TimeSpan>.  
  
 Este exemplo também demonstra como ativar persistência para <xref:System.Activities.WorkflowApplication>. Para esse exemplo específico, nós estaremos usando timers duráveis em que dados de fluxo de trabalho serão descarregados na base de dados de persistência durante o tempo ocioso enquanto aguarda o timer para expirar. Essa implementação também pode ser usada para outras ações de persistência. Este exemplo mostra como configurar a cadeia de conexão de persistência com SQL Server, e como criar o armazenamento de instância para persistir os dados para o fluxo de trabalho instância. A lógica é fornecida em como proceder o fluxo de trabalho depois que um evento é gerado que faz a instância de fluxo de trabalho viável.  
  
 Como você percorrer este exemplo, você verá a hora em que o atraso interno começa e for concluído, que por sua vez fará com que uma mensagem de email a ser enviada. A partir de aí, a atividade de AbsoluteDelay paralisará até <xref:System.DateTime> especificado (ou os 0 se <xref:System.DateTime> expirou) que por sua vez eles farão com que um email em cima de expiração. Isso mostrará os dois exemplos diferentes de uso da funcionalidade interna de <xref:System.Activities.Statements.Delay> contra o uso de uma atividade de AbsoluteDelay.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Garanta que você tenha SQL Server Express (ou superior) instalado em seu computador  
  
2.  Executar setup.cmd (de WF/Basic/Services/AbsoluteDelay/CS) em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] para criar o base de dados de AbsoluteDelaySampleDB, crie o esquema de persistência e criar a lógica de persistência.  
  
3.  Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Especificar a duração da atividade do atraso.  
  
5.  Especificar o ExpirationTime na atividade de AbsoluteDelay.  
  
6.  Atualizar os campos de SendMailTo, de SendMailFrom, de SendMailSubject, de SendMailBody, e de SmtpHost na atividade de SendMail.  
  
    > [!NOTE]
    >  Se você não incorpora um host válido SMTP, o aplicativo irá acionar uma exceção SMTP.  
  
7.  Compile a solução selecionando **criar**, **compilar solução**.  
  
8.  Executar a solução pressionando **F5**.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
