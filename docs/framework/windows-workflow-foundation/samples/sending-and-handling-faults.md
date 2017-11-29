---
title: Enviando e manipulando falhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57d522918d280c9a8a68fcd420b7216cc48216d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## <a name="see-also"></a>Consulte também
