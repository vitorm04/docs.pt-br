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
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797114"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="96384-102">Como: criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="96384-102">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="96384-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) dá suporte a um modelo de autorização baseado em declarações extensível.</span><span class="sxs-lookup"><span data-stu-id="96384-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="96384-104">As declarações são extraídas de tokens e, opcionalmente, processadas por políticas de <xref:System.IdentityModel.Policy.AuthorizationContext>autorização personalizadas e, em seguida, colocadas em um.</span><span class="sxs-lookup"><span data-stu-id="96384-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="96384-105">Um Gerenciador de autorização examina as declarações no <xref:System.IdentityModel.Policy.AuthorizationContext> para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="96384-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="96384-106">Por padrão, as decisões de autorização são feitas <xref:System.ServiceModel.ServiceAuthorizationManager> pela classe; no entanto, essas decisões podem ser substituídas por meio da criação de um Gerenciador de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="96384-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="96384-107">Para criar um Gerenciador de autorização personalizado, crie uma classe que derive <xref:System.ServiceModel.ServiceAuthorizationManager> de e <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> implemente o método.</span><span class="sxs-lookup"><span data-stu-id="96384-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="96384-108">As <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> decisões de autorização são feitas no método, que `true` retorna quando o acesso é `false` concedido e quando o acesso é negado.</span><span class="sxs-lookup"><span data-stu-id="96384-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="96384-109">Se a decisão de autorização depender do conteúdo do corpo da mensagem, use o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método.</span><span class="sxs-lookup"><span data-stu-id="96384-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="96384-110">Devido a problemas de desempenho, se possível, você deve reprojetar seu aplicativo para que a decisão de autorização não exija acesso ao corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="96384-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="96384-111">O registro do Gerenciador de autorização personalizado para um serviço pode ser feito no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="96384-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="96384-112">Para criar um Gerenciador de autorização personalizado</span><span class="sxs-lookup"><span data-stu-id="96384-112">To create a custom authorization manager</span></span>

1. <span data-ttu-id="96384-113">Derive uma classe da <xref:System.ServiceModel.ServiceAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="96384-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="96384-114">Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29>.</span><span class="sxs-lookup"><span data-stu-id="96384-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="96384-115">Use o <xref:System.ServiceModel.OperationContext> que é passado para o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> método para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="96384-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="96384-116">O exemplo de código a seguir <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> usa o método para localizar a `http://www.contoso.com/claims/allowedoperation` declaração personalizada para tomar uma decisão de autorização.</span><span class="sxs-lookup"><span data-stu-id="96384-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="96384-117">Para registrar um Gerenciador de autorização personalizado usando código</span><span class="sxs-lookup"><span data-stu-id="96384-117">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="96384-118">Crie uma instância do Gerenciador de autorização personalizado e atribua-a à <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="96384-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="96384-119">O <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> pode ser acessado usando <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="96384-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="96384-120">O exemplo de código a seguir `MyServiceAuthorizationManager` registra o Gerenciador de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="96384-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="96384-121">Para registrar um Gerenciador de autorização personalizado usando a configuração</span><span class="sxs-lookup"><span data-stu-id="96384-121">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="96384-122">Abra o arquivo de configuração para o serviço.</span><span class="sxs-lookup"><span data-stu-id="96384-122">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="96384-123">Adicione um [ \<> de autorização](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) para os [ \<comportamentos >](../../configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="96384-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="96384-124">Para a [ \<> de autorização](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), adicione um `serviceAuthorizationManagerType` atributo e defina seu valor para o tipo que representa o Gerenciador de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="96384-124">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="96384-125">Adicione uma associação que proteja a comunicação entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="96384-125">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="96384-126">A associação escolhida para essa comunicação determina as declarações que são adicionadas ao <xref:System.IdentityModel.Policy.AuthorizationContext>, que o Gerenciador de autorização personalizado usa para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="96384-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="96384-127">Para obter mais detalhes sobre as associações fornecidas pelo sistema, consulte [associações fornecidas pelo sistema](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="96384-127">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="96384-128">Associe o comportamento a um ponto de extremidade de serviço, adicionando um elemento de [ \<> de serviço](../../configure-apps/file-schema/wcf/service.md) e defina `behaviorConfiguration` o valor do atributo como o valor do atributo Name para o [ \<elemento de comportamento >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="96384-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="96384-129">Para obter mais informações sobre como configurar um ponto de [extremidade de serviço, consulte Como: Criar um ponto de extremidade de](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="96384-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="96384-130">O exemplo de código a seguir registra o Gerenciador `Samples.MyServiceAuthorizationManager`de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="96384-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

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
    > <span data-ttu-id="96384-131">Observe que, quando você especifica o serviceAuthorizationManagerType, a cadeia de caracteres deve conter o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="96384-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="96384-132">uma vírgula e o nome do assembly no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="96384-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="96384-133">Se você sair do nome do assembly, o WCF tentará carregar o tipo de System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="96384-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="96384-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96384-134">Example</span></span>

<span data-ttu-id="96384-135">O exemplo de código a seguir demonstra uma implementação básica <xref:System.ServiceModel.ServiceAuthorizationManager> de uma classe que inclui <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> a substituição do método.</span><span class="sxs-lookup"><span data-stu-id="96384-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="96384-136">O código de exemplo examina o <xref:System.IdentityModel.Policy.AuthorizationContext> para uma declaração personalizada e retorna `true` quando o recurso dessa declaração personalizada corresponde ao valor da ação do <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="96384-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="96384-137">Para obter uma implementação mais completa de <xref:System.ServiceModel.ServiceAuthorizationManager> uma classe, consulte [política de autorização](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="96384-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="96384-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96384-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="96384-139">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="96384-139">Authorization Policy</span></span>](../samples/authorization-policy.md)
