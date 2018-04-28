---
title: Como personificar um cliente em um serviço
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 95330e062ff0ab6ba080deeb01a73bb64fac4dfc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="b6062-102">Como personificar um cliente em um serviço</span><span class="sxs-lookup"><span data-stu-id="b6062-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="b6062-103">Representar um cliente em um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço permite que o serviço executar ações em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6062-103">Impersonating a client on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="b6062-104">Para ações sujeitos a acesso (ACL) da lista de controle verifica, como acesso a diretórios e arquivos em um computador ou acesso a um banco de dados do SQL Server, a verificação ACL é em relação à conta de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6062-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="b6062-105">Este tópico mostra as etapas básicas necessárias para permitir que um cliente em um domínio do Windows definir um nível de representação do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6062-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="b6062-106">Para um exemplo de isso, consulte [representar o cliente](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b6062-107"> representação do cliente, consulte [delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-107"> client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6062-108">Quando o cliente e o serviço estiverem em execução no mesmo computador e o cliente é executado sob uma conta de sistema (ou seja, `Local System` ou `Network Service`), o cliente não pode ser representado quando uma sessão segura é estabelecida com tokens de contexto de segurança com monitoração de estado.</span><span class="sxs-lookup"><span data-stu-id="b6062-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="b6062-109">Um aplicativo de console ou WinForms normalmente é executado sob a conta conectada no momento, para que a conta pode ser representada por padrão.</span><span class="sxs-lookup"><span data-stu-id="b6062-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="b6062-110">No entanto, quando o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página e que é hospedado no [!INCLUDE[iis601](../../../includes/iis601-md.md)] ou IIS 7.0 e, em seguida, o cliente é executado sob o `Network Service` conta por padrão.</span><span class="sxs-lookup"><span data-stu-id="b6062-110">However, when the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and that page is hosted in [!INCLUDE[iis601](../../../includes/iis601-md.md)] or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="b6062-111">Todas as associações fornecidas pelo sistema que oferecem suporte a sessões seguras usam um token de contexto de segurança sem monitoração de estado por padrão.</span><span class="sxs-lookup"><span data-stu-id="b6062-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="b6062-112">No entanto, se o cliente é um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sessões seguras com tokens de contexto de segurança com monitoração de estado e página são usadas, o cliente não pode ser representado.</span><span class="sxs-lookup"><span data-stu-id="b6062-112">However, if the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b6062-113"> usando tokens de contexto de segurança com monitoração de estado em uma sessão segura, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-113"> using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="b6062-114">Para habilitar a representação de um cliente de um token do Windows em cache em um serviço</span><span class="sxs-lookup"><span data-stu-id="b6062-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1.  <span data-ttu-id="b6062-115">Crie o serviço.</span><span class="sxs-lookup"><span data-stu-id="b6062-115">Create the service.</span></span> <span data-ttu-id="b6062-116">Para obter um tutorial deste procedimento básico, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="b6062-117">Usar uma associação que usa a autenticação do Windows e cria uma sessão, como <xref:System.ServiceModel.NetTcpBinding> ou <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b6062-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="b6062-118">Ao criar a implementação da interface do serviço, se aplicam a <xref:System.ServiceModel.OperationBehaviorAttribute> classe para o método que requer a representação do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6062-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="b6062-119">Defina a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> como <xref:System.ServiceModel.ImpersonationOption.Required>.</span><span class="sxs-lookup"><span data-stu-id="b6062-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="b6062-120">Para definir o nível de representação permitidos no cliente</span><span class="sxs-lookup"><span data-stu-id="b6062-120">To set the allowed impersonation level on the client</span></span>  
  
1.  <span data-ttu-id="b6062-121">Criar código de cliente de serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b6062-122">Para obter mais informações, consulte [Acessando serviços usando um cliente WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-122">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="b6062-123">Depois de criar o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente, definir o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade o <xref:System.ServiceModel.Security.WindowsClientCredential> classe para um do <xref:System.Security.Principal.TokenImpersonationLevel> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="b6062-123">After creating the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b6062-124">Para usar <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negociado a autenticação Kerberos (às vezes chamado de *multi-segmento* ou *várias etapas* Kerberos) deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="b6062-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="b6062-125">Para obter uma descrição de como implementar isso, consulte [práticas recomendadas de segurança](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="b6062-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b6062-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6062-126">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [<span data-ttu-id="b6062-127">Representar o cliente</span><span class="sxs-lookup"><span data-stu-id="b6062-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [<span data-ttu-id="b6062-128">Delegação e representação</span><span class="sxs-lookup"><span data-stu-id="b6062-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
