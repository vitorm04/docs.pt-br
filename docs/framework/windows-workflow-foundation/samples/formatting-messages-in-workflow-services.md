---
title: "Mensagens de formatação em serviços de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726ce98f3fe11bbc3cd13d90cdae335c0741efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="formatting-messages-in-workflow-services"></a>Mensagens de formatação em serviços de fluxo de trabalho
Este exemplo mostra como os tipos de usuário diferentes podem ser usados em atividades de mensagem (de serviços WCF). O serviço de exemplo é um serviço simples de aprovação de despesas e expõe três operações. `ApproveExpense` utiliza um tipo de contrato de dados e mostra como usar tipos conhecidos. Retorna `true` ou `false` da operação com base na quantidade de despesas. `ApprovePO`usa um tipo de XmlSerializer e retorna `true` ou `false` com base no valor de despesas.`ApprovedVendor` usa um tipo de contrato de mensagem e retorna `true` ou `false` se ele estiver na lista de fornecedores aprovados ou se originou a solicitação do departamento de Finanças (o departamento financeiro pode usar qualquer fornecedor).  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.  
  
2.  Executa serviço, gerado em [] do diretório da solução FormatterService \ \ bin \ debug \  
  
3.  Segundo, executa aplicativo cliente gerado em [] do diretório da solução FormatterClient \ \ bin \ debug.  
  
4.  O cliente chama três operações no serviço e imprime os resultados. Quando completo, pressione ENTER para sair do cliente e o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`