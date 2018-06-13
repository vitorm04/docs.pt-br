---
title: Enviando e manipulando falhas
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516120"
---
# <a name="sending-and-handling-faults"></a>Enviando e manipulando falhas
Este exemplo demonstra como usar as atividades de mensagem de <xref:System.ServiceModel.Activities.SendReply> e de <xref:System.ServiceModel.Activities.ReceiveReply> para enviar e receber falhas previstas e inesperado. Nesse cenário, os primeiros resultados da solicitação de cliente em uma falha esperada que é incluída na sua coleção de <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> . As próximas solicitações de cliente levam a receber falhas inesperados, antes que a solicitação foi bem-sucedida final.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.  
  
2.  Abra o arquivo de solução de Faults.sln.  
  
3.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
4.  Executar o projeto de serviço.  
  
    1.  Em **Solution Explorer**, com o botão direito do `FaultService` do projeto e selecione **definir como projeto de inicialização**.  
  
    2.  Pressione CTRL+F5.  
  
5.  Abrir outra cópia do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.  
  
6.  Abra o arquivo de solução de Faults.sln.  
  
7.  Executar o projeto do cliente.  
  
    1.  Em **Solution Explorer**, com o botão direito do `FaultClient` do projeto e selecione **definir como projeto de inicialização**.  
  
    2.  Pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`