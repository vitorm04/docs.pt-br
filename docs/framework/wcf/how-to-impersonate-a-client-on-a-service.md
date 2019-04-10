---
title: 'Como: representar um cliente em um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: d58f25f279bf2baa1caa7744cea94b909f48866f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310571"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Como: representar um cliente em um serviço
Representando um cliente em um serviço do Windows Communication Foundation (WCF) permite que o serviço executar ações em nome do cliente. Para ações sujeita ao acesso (ACL) lista de controle verificações, como acesso a diretórios e arquivos em um computador ou acesso a um banco de dados do SQL Server, a verificação ACL é contra a conta de usuário do cliente. Este tópico mostra as etapas básicas necessárias para permitir que um cliente em um domínio do Windows definir um nível de representação do cliente. Para obter um exemplo de funcionamento de isso, consulte [representar o cliente](../../../docs/framework/wcf/samples/impersonating-the-client.md). Para obter mais informações sobre representação do cliente, consulte [delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Quando o cliente e o serviço estiver executando no mesmo computador e o cliente está em execução sob uma conta do sistema (ou seja, `Local System` ou `Network Service`), o cliente não pode ser representado quando uma sessão segura é estabelecida com tokens de contexto de segurança com monitoração de estado. Um aplicativo de console ou WinForms normalmente é executado sob a conta conectada no momento, para que a conta pode ser representada por padrão. No entanto, quando o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] nessa página e página é hospedado no [!INCLUDE[iis601](../../../includes/iis601-md.md)] ou o IIS 7.0 e, em seguida, o cliente é executado no `Network Service` conta por padrão. Todas as associações fornecidas pelo sistema que dão suporte a sessões seguras usam um token de contexto de segurança sem monitoração de estado por padrão. No entanto, se o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página e sessões seguras com tokens de contexto de segurança com monitoração de estado são usadas, o cliente não pode ser representado. Para obter mais informações sobre como usar tokens de contexto de segurança com monitoração de estado em uma sessão segura, consulte [como: Criar um contexto de segurança para uma sessão segura Token](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Para habilitar a representação de um cliente de um token em cache do Windows em um serviço  
  
1. Criar o serviço. Para obter um tutorial deste procedimento básico, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2. Usar uma associação que usa a autenticação do Windows e cria uma sessão, como <xref:System.ServiceModel.NetTcpBinding> ou <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Ao criar a implementação da interface do serviço, se aplicam a <xref:System.ServiceModel.OperationBehaviorAttribute> classe para o método que exige a representação do cliente. Defina a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> como <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Para definir o nível de representação permitido no cliente  
  
1. Criar código de cliente de serviço usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Para obter mais informações, consulte [serviços de acesso usando um cliente WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2. Depois de criar o cliente do WCF, defina as <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade do <xref:System.ServiceModel.Security.WindowsClientCredential> classe para um do <xref:System.Security.Principal.TokenImpersonationLevel> valores de enumeração.  
  
    > [!NOTE]
    >  Para usar <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negociado a autenticação Kerberos (às vezes chamado de *multi-segmentos* ou *várias etapas* Kerberos) deve ser usado. Para obter uma descrição de como implementar isso, consulte [práticas recomendadas de segurança](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Representando o cliente](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
