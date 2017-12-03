---
title: "Segurança de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47d06950f8aa9b85420d873adcc4b1acb89a5219
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-security"></a>Segurança de fluxo de trabalho
[!INCLUDE[wf](../../../includes/wf-md.md)] está integrado com várias tecnologias diferentes, como o Microsoft SQL Server e [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Interagir com essas tecnologias pode gerar problemas de segurança no fluxo de trabalho se feito de modo inadequado.  
  
## <a name="persistence-security-concerns"></a>Problemas de segurança de persistência  
  
1.  Fluxos de trabalho que usam uma necessidade de atividade e de persistência <xref:System.Activities.Statements.Delay> de ser reactivated por um serviço. Windows AppFabric usa o serviço de gerenciamento (WMS) de fluxo de trabalho para reativar fluxos de trabalho com timers expirados. WMS cria <xref:System.ServiceModel.WorkflowServiceHost> para hospedar o fluxo de trabalho reactivated. Se o serviço de WMS é interrompida, os fluxos de trabalho mantidas não reactivated quando seus timers eles expiram.  
  
2.  Acesso a métodos de como exemplo de bens deve ser protegido contra as entidades mal-intencionados externos ao domínio do aplicativo. Além disso, os desenvolvedores devem garantir que o código mal-intencionado não pode ser executado no mesmo domínio de aplicativo que o código de instâncias durável.  
  
3.  Citar como exemplo de bens não deve ser executado com permissões elevadas (de administrador).  
  
4.  Os dados que estão sendo processadas fora do domínio de aplicativo devem ser protegidos.  
  
5.  Aplicativos que requerem isolamento de segurança não devem compartilhar a mesma instância de abstração de esquema. Esses aplicativos devem usar diferentes provedores de armazenamento, ou provedores de armazenamento configurados para usar instanciações diferentes de armazenamento.  
  
## <a name="sql-server-security-concerns"></a>Problemas de segurança do SQL Server  
  
-   Quando um grande número de atividades filhos, locais, indexadores, hospedam extensões, ou os escopos são usados, ou quando os indicadores com as carrega úteis muito grandes são usados, a memória pode ser esgotada, ou as quantidades inadequadas do espaço de base de dados podem ser atribuídas durante a persistência. Isso pode ser abrandado utilizando em nível de objeto e a segurança de base de dados - nível.  
  
-   Ao usar <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, o armazenamento de instância deve ser protegido. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Práticas recomendadas do SQL Server](http://go.microsoft.com/fwlink/?LinkId=164972).  
  
-   Dados confidenciais no armazenamento de instância devem ser criptografados. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Criptografia de segurança do SQL](http://go.microsoft.com/fwlink/?LinkId=164976).  
  
-   Desde que a cadeia de conexão caracteres de base de dados é incluída com frequência em um arquivo de configuração, a segurança do windows nível (ACL) deve ser usada para garantir que o arquivo de configuração (Web.Config) geralmente é seguro, e que o logon e informações de senha não estão incluídos na cadeia de conexão. A autenticação do Windows deve ser usada entre o base de dados e o servidor web em vez disso.  
  
## <a name="considerations-for-workflowservicehost"></a>Considerações para WorkflowServiceHost  
  
-   os pontos de extremidade de[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usados em fluxos de trabalho devem ser protegidos. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Visão geral de segurança do WCF](http://go.microsoft.com/fwlink/?LinkID=164975).  
  
-   Autorização do nível pode ser implementada usando <xref:System.ServiceModel.ServiceAuthorizationManager>. Consulte [como: criar um Gerenciador de autorização personalizada para um serviço](http://go.microsoft.com/fwlink/?LinkId=192228) para obter detalhes. Isso também é demonstrado no exemplo a seguir: [protegendo serviços de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).  
  
-   O ServiceSecurityContext para a mensagem de entrada também está disponível no fluxo de trabalho acessando OperationContext.  Consulte [acessando OperationContext de um serviço de fluxo de trabalho](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) para obter detalhes.  
  
## <a name="wf-security-pack-ctp"></a>Bloco CTP de segurança de WF  
 O Microsoft WF segurança Pack CTP 1 é a versão primeiro community technology preview (CTP) de um conjunto de atividades e sua implementação baseada em [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)na [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF 4) e o [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx).  O bloco CTP 1 de segurança do Microsoft WF contém ambas as atividades e seus designers que ilustram como facilmente ative vários cenários relacionados a segurança usando o fluxo de trabalho, incluindo:  
  
1.  Representando uma identidade de cliente no fluxo de trabalho  
  
2.  Autorização de Em- fluxo de trabalho, como PrincipalPermission e validação de reivindicações  
  
3.  Autenticada mensagem usando ClientCredentials especificado no fluxo de trabalho, como o nome de usuário ou senha/um token recuperado de um serviço (STS) de símbolo de segurança  
  
4.  Fluxo um símbolo de segurança de cliente a um serviço back-end (delegação reivindicação- base) usando a ws-trust Ata  
  
Para obter mais informações e baixar o CTP de pacote de segurança do WF, consulte: [CTP de pacote de segurança de WF](http://wf.codeplex.com/releases/view/48114)