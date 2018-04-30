---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
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
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 19
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 72eff4af38636577dc9e3b35af1f1155d5ed892c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="47685-102">Como fazer auditoria de eventos de segurança do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="47685-102">How to: Audit Windows Communication Foundation Security Events</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="47685-103"> permite registrar eventos de segurança para o log de eventos do Windows, que pode ser visualizado usando o Visualizador de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="47685-103"> allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="47685-104">Este tópico explica como configurar um aplicativo para que ele registra eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="47685-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="47685-105">Para obter mais informações sobre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditoria, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="47685-105">For more information about [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="47685-106">A auditoria de eventos de segurança no código</span><span class="sxs-lookup"><span data-stu-id="47685-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="47685-107">Especifique o local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="47685-107">Specify the audit log location.</span></span> <span data-ttu-id="47685-108">Para fazer isso, defina o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> propriedade o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> classe para uma da <xref:System.ServiceModel.AuditLogLocation> valores de enumeração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="47685-109">O <xref:System.ServiceModel.AuditLogLocation> enumeração tem três valores: `Application`, `Security`, ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="47685-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="47685-110">O valor especifica um dos logs visíveis no Visualizador de eventos, ou o log de segurança ou o log de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47685-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="47685-111">Se você usar o `Default` valor, o log real depende o sistema operacional que o aplicativo está em execução no.</span><span class="sxs-lookup"><span data-stu-id="47685-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="47685-112">Se a auditoria está habilitada e o local do log não for especificado, o padrão é o `Security` log para plataformas que oferece suporte à gravação no log de segurança; caso contrário, ele gravará o `Application` log.</span><span class="sxs-lookup"><span data-stu-id="47685-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="47685-113">Somente [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)] suporte para gravação no log de segurança por padrão.</span><span class="sxs-lookup"><span data-stu-id="47685-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="47685-114">Configure os tipos de eventos para auditoria.</span><span class="sxs-lookup"><span data-stu-id="47685-114">Set up the types of events to audit.</span></span> <span data-ttu-id="47685-115">Você pode auditar simultaneamente eventos de nível de serviço ou eventos de autorização de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="47685-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="47685-116">Para fazer isso, defina o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> propriedade ou o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> propriedade para um do <xref:System.ServiceModel.AuditLevel> valores de enumeração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="47685-117">Especifique se deseja suprimir ou expor falhas para o aplicativo com relação a eventos de auditoria de log.</span><span class="sxs-lookup"><span data-stu-id="47685-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="47685-118">Definir o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade como `true` ou `false`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="47685-119">O padrão `SuppressAuditFailure` é de propriedade `true`, de modo que a falha de auditoria não afeta o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47685-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="47685-120">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="47685-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="47685-121">Para qualquer auditoria com êxito, um rastreamento detalhado é escrito.</span><span class="sxs-lookup"><span data-stu-id="47685-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="47685-122">Para qualquer falha de auditoria, o rastreamento é gravado no nível de erro.</span><span class="sxs-lookup"><span data-stu-id="47685-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="47685-123">Exclua o existente <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> da coleção de comportamentos encontrado na descrição de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="47685-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="47685-124">A coleção de comportamento é acessada pelo <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade, que por sua vez é acessada a partir do <xref:System.ServiceModel.ServiceHostBase.Description%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="47685-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="47685-125">Em seguida, adicione o novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> na mesma coleção, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="47685-126">Para configurar a auditoria na configuração</span><span class="sxs-lookup"><span data-stu-id="47685-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="47685-127">Para configurar a auditoria na configuração, adicione uma [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) seção do arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="47685-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="47685-128">Em seguida, adicione um [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elemento e defina os vários atributos, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="47685-129">Você deve especificar o comportamento de serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="47685-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="47685-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47685-130">Example</span></span>  
 <span data-ttu-id="47685-131">O código a seguir cria uma instância do <xref:System.ServiceModel.ServiceHost> classe e adiciona um novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sua coleção de comportamentos.</span><span class="sxs-lookup"><span data-stu-id="47685-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="47685-132">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47685-132">.NET Framework Security</span></span>  
 <span data-ttu-id="47685-133">Definindo o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade `true`, suprime qualquer falha ao gerar auditorias de segurança (se definido como `false`, uma exceção será lançada).</span><span class="sxs-lookup"><span data-stu-id="47685-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="47685-134">No entanto, se você habilitar as seguintes janelas **configuração de segurança Local**propriedade, uma falha ao gerar eventos de auditoria fará com que o Windows desligar imediatamente:</span><span class="sxs-lookup"><span data-stu-id="47685-134">However, if you enable the following Windows **Local Security Setting**property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="47685-135">**Auditoria: Desligar o sistema imediatamente se não for possível registrar auditorias de segurança**</span><span class="sxs-lookup"><span data-stu-id="47685-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="47685-136">Para definir a propriedade, abra o **configurações de segurança Local** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="47685-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="47685-137">Em **as configurações de segurança**, clique em **políticas locais**.</span><span class="sxs-lookup"><span data-stu-id="47685-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="47685-138">Em seguida, clique em **opções de segurança**.</span><span class="sxs-lookup"><span data-stu-id="47685-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="47685-139">Se o <xref:System.ServiceModel.AuditLogLocation> está definida como <xref:System.ServiceModel.AuditLogLocation.Security> e **de auditoria de acesso a objetos** não está definido no **política de segurança Local**, não os eventos de auditoria serão gravados no log de segurança.</span><span class="sxs-lookup"><span data-stu-id="47685-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="47685-140">Observe que nenhuma falha é retornada, mas as entradas de auditoria não são gravadas no log de segurança.</span><span class="sxs-lookup"><span data-stu-id="47685-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47685-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47685-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="47685-142">Auditoria</span><span class="sxs-lookup"><span data-stu-id="47685-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
