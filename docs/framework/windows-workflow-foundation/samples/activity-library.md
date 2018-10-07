---
title: Biblioteca de Atividades
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e8777d0068e6cca9c9324a6fd2668e6ff9e9da7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844014"
---
# <a name="activity-library"></a>Biblioteca de Atividades
Esta seção contém exemplos que demonstram atividades personalizados avançados no Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>Nesta seção

 [Atividade personalizado de SendMail](../../../../docs/framework/windows-workflow-foundation/samples/sendmail-custom-activity.md)  
 Demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho.  
  
 [Paralelo estrangulado ForEach](../../../../docs/framework/windows-workflow-foundation/samples/throttled-parallel-foreach.md)  
 Demonstra como atividade de `ThrottleParallelForEach` é semelhante à atividade de <xref:System.Activities.Statements.ParallelForEach%601> com uma exceção que permite que define um fator de simultaneidade para restringir o número de ramificações simultâneas para executar.
  
 [Atividades de acesso de banco de dados](../../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)  
 Demonstra como criar atividades que permitem acessar bancos de dados para recuperar ou modificar as informações e usar [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) para acessar o banco de dados.  
  
 [Atividade de política exteriorizada no .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/externalized-policy-activity-in-net-framework-4-5.md)  
 Demonstra como a atividade ExternalizedPolicy4 permite executar o Windows Workflow Foundation existente no [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objetos no Windows Workflow Foundation no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (4,5 WCF) diretamente usando as mecanismo de regras que é enviado em WF 3,5. 
  
 [ForEach não genérico](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)  
 Demonstra como criar uma versão não genérico de atividade de <xref:System.Activities.Statements.ForEach%601> .  
  
 [ParallelForEach não genérico](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)  
 Demonstra como criar uma versão não genérico de atividade de <xref:System.Activities.Statements.ParallelForEach%601> .  
  
 [Obter WorkflowInstanceId](../../../../docs/framework/windows-workflow-foundation/samples/get-workflowinstanceid.md)  
 Demonstra como usar a atividade personalizado, `GetWorkflowInstanceId`, para retornar a identificação de instância de fluxo de trabalho
