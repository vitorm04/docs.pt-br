---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 62d26b24b5d46427c1871fccf48b063c45781beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185119"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="a5cb5-102">Como fazer auditoria de eventos de segurança do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a5cb5-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="a5cb5-103">O Windows Communication Foundation (WCF) permite registrar eventos de segurança no registro de eventos do Windows, que podem ser visualizados usando o Visualizador de Eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="a5cb5-104">Este tópico explica como configurar um aplicativo para que ele registre eventos de segurança.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="a5cb5-105">Para obter mais informações sobre auditoria wcf, consulte [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="a5cb5-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="a5cb5-106">Para auditar eventos de segurança em código</span><span class="sxs-lookup"><span data-stu-id="a5cb5-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="a5cb5-107">Especifique o local do registro de auditoria.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-107">Specify the audit log location.</span></span> <span data-ttu-id="a5cb5-108">Para isso, defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> a <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> propriedade da <xref:System.ServiceModel.AuditLogLocation> classe como um dos valores de enumeração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="a5cb5-109">A <xref:System.ServiceModel.AuditLogLocation> enumeração tem `Application`três `Security`valores: , ou `Default`.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="a5cb5-110">O valor especifica um dos registros visíveis no Visualizador de Eventos, seja no registro de segurança ou no registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="a5cb5-111">Se você `Default` usar o valor, o registro real dependerá do sistema operacional em que o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="a5cb5-112">Se a auditoria estiver ativada e o local do `Security` log não for especificado, o padrão será o registro de plataformas que suportam a gravação no registro de segurança; caso contrário, ele vai `Application` escrever para o log.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="a5cb5-113">Apenas o Windows Server 2003 e o Windows Vista suportam a gravação no registro de segurança por padrão.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="a5cb5-114">Configure os tipos de eventos para auditoria.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-114">Set up the types of events to audit.</span></span> <span data-ttu-id="a5cb5-115">Você pode auditar simultaneamente eventos de nível de serviço ou eventos de autorização de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="a5cb5-116">Para isso, defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> a <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> propriedade ou <xref:System.ServiceModel.AuditLevel> a propriedade como um dos valores de enumeração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="a5cb5-117">Especifique se deve suprimir ou expor falhas ao aplicativo em relação a eventos de auditoria de log.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="a5cb5-118">Defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> a `true` propriedade `false`como ou, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="a5cb5-119">A `SuppressAuditFailure` propriedade `true`padrão é, de modo que a falha na auditoria não afete o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="a5cb5-120">Caso contrário, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="a5cb5-121">Para qualquer auditoria bem sucedida, um traço verboso é escrito.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="a5cb5-122">Para qualquer falha na auditoria, o rastreamento é escrito no nível de erro.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="a5cb5-123">Exclua o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existente da coleção de comportamentos encontrados <xref:System.ServiceModel.ServiceHost>na descrição de um .</span><span class="sxs-lookup"><span data-stu-id="a5cb5-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a5cb5-124">A coleta de comportamento <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> é acessada pelo imóvel, que por sua vez é acessado a <xref:System.ServiceModel.ServiceHostBase.Description%2A> partir do imóvel.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="a5cb5-125">Em seguida, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> adicione o novo à mesma coleção, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="a5cb5-126">Para configurar a auditoria na configuração</span><span class="sxs-lookup"><span data-stu-id="a5cb5-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="a5cb5-127">Para configurar a auditoria na [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) configuração, adicione um elemento de comportamento>aos [ \<comportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) seção do arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="a5cb5-128">Em seguida, adicione um [ \<elemento de>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) e defina os vários atributos, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="a5cb5-129">Você deve especificar o comportamento para o serviço, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a5cb5-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5cb5-130">Example</span></span>  
 <span data-ttu-id="a5cb5-131">O código a seguir <xref:System.ServiceModel.ServiceHost> cria uma instância <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> da classe e adiciona uma nova coleção de comportamentos.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="a5cb5-132">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5cb5-132">.NET Framework Security</span></span>  
 <span data-ttu-id="a5cb5-133">Definir <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> a `true`propriedade para, suprimir qualquer falha na geração `false`de auditorias de segurança (se definida para , uma exceção é lançada).</span><span class="sxs-lookup"><span data-stu-id="a5cb5-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="a5cb5-134">No entanto, se você habilitar a seguinte propriedade **configuração de configuração de segurança local** do Windows, uma falha na geração de eventos de auditoria fará com que o Windows seja desligado imediatamente:</span><span class="sxs-lookup"><span data-stu-id="a5cb5-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="a5cb5-135">**Auditoria: Desligar o sistema imediatamente se não for possível registrar auditorias de segurança**</span><span class="sxs-lookup"><span data-stu-id="a5cb5-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="a5cb5-136">Para definir a propriedade, abra a caixa de diálogo **Configurações de segurança local.**</span><span class="sxs-lookup"><span data-stu-id="a5cb5-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="a5cb5-137">Em **Configurações de segurança,** clique **em Políticas locais**.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="a5cb5-138">Em seguida, clique **em Opções de segurança**.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="a5cb5-139">Se <xref:System.ServiceModel.AuditLogLocation> a propriedade <xref:System.ServiceModel.AuditLogLocation.Security> estiver definida e o **Audit Object Access** não estiver definido na Política de Segurança **Local,** os eventos de auditoria não serão gravados no registro de segurança.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="a5cb5-140">Observe que nenhuma falha é retornada, mas as entradas de auditoria não estão escritas no registro de segurança.</span><span class="sxs-lookup"><span data-stu-id="a5cb5-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cb5-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5cb5-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="a5cb5-142">Auditoria</span><span class="sxs-lookup"><span data-stu-id="a5cb5-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
