---
title: Mensagens de formatação em serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389131"
---
# <a name="formatting-messages-in-workflow-services"></a>Mensagens de formatação em serviços de fluxo de trabalho
Este exemplo mostra como os tipos de usuário diferentes podem ser usados em atividades de mensagem (de serviços WCF). O serviço de exemplo é um serviço simples de aprovação de despesas e expõe três operações. `ApproveExpense` utiliza um tipo de contrato de dados e mostra como usar tipos conhecidos. Retorna `true` ou `false` da operação com base na quantidade de despesas. `ApprovePO` usa um tipo de XmlSerializer e retorna `true` ou `false` com base na quantidade de despesas.`ApprovedVendor` usa um tipo de contrato de mensagem e retorna `true` ou `false` se o fornecedor estiver na lista de fornecedores aprovados ou se a solicitação origina-se do departamento de Finanças (do departamento financeiro pode usar qualquer fornecedor).  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`