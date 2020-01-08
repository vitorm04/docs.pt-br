---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 7071aaf88346ee217226632501ebd6c82cfc1cb8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346754"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="48e74-102">Como fazer auditoria de eventos de segurança do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="48e74-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="48e74-103">O Windows Communication Foundation (WCF) permite que você registre eventos de segurança no log de eventos do Windows, que pode ser exibido usando o Visualizador de Eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="48e74-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="48e74-104">Este tópico explica como configurar um aplicativo para que ele registre eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e74-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="48e74-105">Para obter mais informações sobre a auditoria do WCF, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="48e74-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="48e74-106">Para auditar eventos de segurança no código</span><span class="sxs-lookup"><span data-stu-id="48e74-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="48e74-107">Especifique o local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="48e74-107">Specify the audit log location.</span></span> <span data-ttu-id="48e74-108">Para fazer isso, defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> da classe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> como um dos valores de enumeração <xref:System.ServiceModel.AuditLogLocation>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="48e74-109">A enumeração <xref:System.ServiceModel.AuditLogLocation> tem três valores: `Application`, `Security`ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="48e74-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="48e74-110">O valor especifica um dos logs visíveis no Visualizador de Eventos, o log de segurança ou o log do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48e74-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="48e74-111">Se você usar o valor `Default`, o log real dependerá do sistema operacional em que o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="48e74-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="48e74-112">Se a auditoria estiver habilitada e o local do log não for especificado, o padrão será o log de `Security` para as plataformas que dão suporte à gravação no log de segurança; caso contrário, ele gravará no log de `Application`.</span><span class="sxs-lookup"><span data-stu-id="48e74-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="48e74-113">Somente o Windows Server 2003 e o Windows Vista dão suporte à gravação no log de segurança por padrão.</span><span class="sxs-lookup"><span data-stu-id="48e74-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="48e74-114">Configure os tipos de eventos para auditar.</span><span class="sxs-lookup"><span data-stu-id="48e74-114">Set up the types of events to audit.</span></span> <span data-ttu-id="48e74-115">Você pode auditar simultaneamente eventos de nível de serviço ou eventos de autorização no nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="48e74-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="48e74-116">Para fazer isso, defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> ou a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> como um dos valores de enumeração <xref:System.ServiceModel.AuditLevel>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="48e74-117">Especifique se deseja suprimir ou expor falhas ao aplicativo em relação aos eventos de auditoria de log.</span><span class="sxs-lookup"><span data-stu-id="48e74-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="48e74-118">Defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> como `true` ou `false`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="48e74-119">A propriedade de `SuppressAuditFailure` padrão é `true`, para que a falha na auditoria não afete o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48e74-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="48e74-120">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="48e74-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="48e74-121">Para qualquer auditoria bem-sucedida, um rastreamento detalhado é gravado.</span><span class="sxs-lookup"><span data-stu-id="48e74-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="48e74-122">Para qualquer falha na auditoria, o rastreamento é gravado no nível de erro.</span><span class="sxs-lookup"><span data-stu-id="48e74-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="48e74-123">Exclua o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existente da coleção de comportamentos encontrados na descrição de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="48e74-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="48e74-124">A coleção de comportamento é acessada pela propriedade <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, que, por sua vez, é acessada pela propriedade <xref:System.ServiceModel.ServiceHostBase.Description%2A>.</span><span class="sxs-lookup"><span data-stu-id="48e74-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="48e74-125">Em seguida, adicione o novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à mesma coleção, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="48e74-126">Para configurar a auditoria na configuração</span><span class="sxs-lookup"><span data-stu-id="48e74-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="48e74-127">Para configurar a auditoria na configuração, adicione um elemento de [comportamento de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) à seção [\<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) do arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="48e74-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="48e74-128">Em seguida, adicione um elemento [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) e defina os vários atributos, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="48e74-129">Você deve especificar o comportamento para o serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="48e74-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="48e74-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48e74-130">Example</span></span>  
 <span data-ttu-id="48e74-131">O código a seguir cria uma instância da classe <xref:System.ServiceModel.ServiceHost> e adiciona uma nova <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sua coleção de comportamentos.</span><span class="sxs-lookup"><span data-stu-id="48e74-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="48e74-132">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48e74-132">.NET Framework Security</span></span>  
 <span data-ttu-id="48e74-133">Definir a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> como `true`, suprime qualquer falha ao gerar auditorias de segurança (se definido como `false`, uma exceção é lançada).</span><span class="sxs-lookup"><span data-stu-id="48e74-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="48e74-134">No entanto, se você habilitar a seguinte propriedade de **configuração de segurança local** do Windows, uma falha ao gerar eventos de auditoria fará com que o Windows seja desligado imediatamente:</span><span class="sxs-lookup"><span data-stu-id="48e74-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="48e74-135">**Auditoria: desligar o sistema imediatamente se não for possível registrar auditorias de segurança**</span><span class="sxs-lookup"><span data-stu-id="48e74-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="48e74-136">Para definir a propriedade, abra a caixa de diálogo **configurações de segurança local** .</span><span class="sxs-lookup"><span data-stu-id="48e74-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="48e74-137">Em **configurações de segurança**, clique em **políticas locais**.</span><span class="sxs-lookup"><span data-stu-id="48e74-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="48e74-138">Em seguida, clique em **Opções de segurança**.</span><span class="sxs-lookup"><span data-stu-id="48e74-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="48e74-139">Se a propriedade <xref:System.ServiceModel.AuditLogLocation> for definida como <xref:System.ServiceModel.AuditLogLocation.Security> e o **acesso ao objeto de auditoria** não estiver definido na política de **segurança local**, os eventos de auditoria não serão gravados no log de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e74-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="48e74-140">Observe que nenhuma falha é retornada, mas as entradas de auditoria não são gravadas no log de segurança.</span><span class="sxs-lookup"><span data-stu-id="48e74-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e74-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="48e74-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="48e74-142">Auditoria</span><span class="sxs-lookup"><span data-stu-id="48e74-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
