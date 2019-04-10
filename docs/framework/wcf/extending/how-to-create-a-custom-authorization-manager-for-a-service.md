---
title: 'Como: criar gerenciador de autorização personalizado para um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: e3d0143cd68bc94c6ff07e65ca5a3c8971b45f23
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337832"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="965d4-102">Como: criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="965d4-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="965d4-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) oferece suporte a um modelo de autorização extensível baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="965d4-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="965d4-104">Declarações são extraídas de tokens e, opcionalmente, processadas por diretivas de autorização personalizado e, em seguida, colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="965d4-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="965d4-105">Um Gerenciador de autorização examina as declarações no <xref:System.IdentityModel.Policy.AuthorizationContext> para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="965d4-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="965d4-106">Por padrão, as decisões de autorização são feitas pelo <xref:System.ServiceModel.ServiceAuthorizationManager> classe; no entanto essas decisões podem ser substituídas, criando uma autorização personalizada manager.</span><span class="sxs-lookup"><span data-stu-id="965d4-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="965d4-107">Para criar uma autorização personalizada manager, crie uma classe que deriva de <xref:System.ServiceModel.ServiceAuthorizationManager> e implementar <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="965d4-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="965d4-108">Decisões de autorização são feitas as <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método, que retorna `true` quando o acesso é concedido e `false` quando o acesso é negado.</span><span class="sxs-lookup"><span data-stu-id="965d4-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="965d4-109">Se a decisão de autorização depende do conteúdo do corpo da mensagem, use o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método.</span><span class="sxs-lookup"><span data-stu-id="965d4-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="965d4-110">Devido a problemas de desempenho, se possível você deve recriar seu aplicativo para que a decisão de autorização não requer acesso ao corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="965d4-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="965d4-111">Registro do Gerenciador de autorização personalizada para um serviço pode ser feito no código ou configuração.</span><span class="sxs-lookup"><span data-stu-id="965d4-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="965d4-112">Para criar uma autorização personalizada Gerenciador</span><span class="sxs-lookup"><span data-stu-id="965d4-112">To create a custom authorization manager</span></span>  
  
1. <span data-ttu-id="965d4-113">Derive uma classe do <xref:System.ServiceModel.ServiceAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="965d4-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2. <span data-ttu-id="965d4-114">Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29>.</span><span class="sxs-lookup"><span data-stu-id="965d4-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="965d4-115">Use o <xref:System.ServiceModel.OperationContext> que é passado para o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> método para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="965d4-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="965d4-116">O seguinte exemplo de código usa o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> método para encontrar a declaração personalizada `http://www.contoso.com/claims/allowedoperation` para tomar uma decisão de autorização.</span><span class="sxs-lookup"><span data-stu-id="965d4-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="965d4-117">Para registrar um Gerenciador de autorização personalizada usando código</span><span class="sxs-lookup"><span data-stu-id="965d4-117">To register a custom authorization manager using code</span></span>  
  
1. <span data-ttu-id="965d4-118">Crie uma instância da autorização personalizada Gerenciador e atribuí-lo para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="965d4-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="965d4-119">O <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> podem ser acessados usando <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="965d4-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="965d4-120">O seguinte código de exemplo registra o `MyServiceAuthorizationManager` Gerenciador de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="965d4-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="965d4-121">Para registrar um Gerenciador de autorização personalizada usando a configuração</span><span class="sxs-lookup"><span data-stu-id="965d4-121">To register a custom authorization manager using configuration</span></span>  
  
1. <span data-ttu-id="965d4-122">Abra o arquivo de configuração para o serviço.</span><span class="sxs-lookup"><span data-stu-id="965d4-122">Open the configuration file for the service.</span></span>  
  
2. <span data-ttu-id="965d4-123">Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="965d4-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="965d4-124">Para o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), adicione um `serviceAuthorizationManagerType` de atributos e defina seu valor para o tipo que representa o Gerenciador de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="965d4-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3. <span data-ttu-id="965d4-125">Adicione uma associação que protege a comunicação entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="965d4-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="965d4-126">A associação que é escolhida para essa comunicação determina as declarações que são adicionadas à <xref:System.IdentityModel.Policy.AuthorizationContext>, que usa o Gerenciador de autorização personalizada para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="965d4-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="965d4-127">Para obter mais detalhes sobre as associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="965d4-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4. <span data-ttu-id="965d4-128">Associar o comportamento de um ponto de extremidade de serviço, adicionando um [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento e defina o valor da `behaviorConfiguration` para o valor do atributo de nome de atributo a [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="965d4-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="965d4-129">Para obter mais informações sobre como configurar um ponto de extremidade de serviço, consulte [como: Criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="965d4-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="965d4-130">O exemplo de código a seguir registra o Gerenciador de autorização personalizado `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="965d4-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="965d4-131">Observe que, quando você especificar serviceAuthorizationManagerType, a cadeia de caracteres deve conter o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="965d4-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="965d4-132">uma vírgula e o nome do assembly no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="965d4-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="965d4-133">Se você deixar o nome do assembly, o WCF tentará carregar o tipo do ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="965d4-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="965d4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="965d4-134">Example</span></span>  
 <span data-ttu-id="965d4-135">O exemplo de código a seguir demonstra uma implementação básica de um <xref:System.ServiceModel.ServiceAuthorizationManager> classe que inclui substituindo o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="965d4-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="965d4-136">O código de exemplo examina a <xref:System.IdentityModel.Policy.AuthorizationContext> para um personalizado de declaração e retorna `true` quando o recurso para essa declaração personalizada corresponde ao valor de ação do <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="965d4-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="965d4-137">Para uma implementação mais completa de um <xref:System.ServiceModel.ServiceAuthorizationManager> classe, consulte [política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="965d4-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="965d4-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="965d4-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="965d4-139">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="965d4-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
