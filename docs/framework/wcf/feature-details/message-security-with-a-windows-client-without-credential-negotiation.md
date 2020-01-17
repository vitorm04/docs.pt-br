---
title: Segurança de mensagem com um cliente Windows sem negociação de credencial
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: d3b05a1786131a119d516edeba0d6e8e24289f87
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212037"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="fb436-102">Segurança de mensagem com um cliente Windows sem negociação de credencial</span><span class="sxs-lookup"><span data-stu-id="fb436-102">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="fb436-103">O cenário a seguir mostra um cliente Windows Communication Foundation (WCF) e um serviço protegido pelo protocolo Kerberos.</span><span class="sxs-lookup"><span data-stu-id="fb436-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="fb436-104">O serviço e o cliente estão no mesmo domínio ou em domínios confiáveis.</span><span class="sxs-lookup"><span data-stu-id="fb436-104">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="fb436-105">A diferença entre esse cenário e a [segurança da mensagem com um cliente do Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) é que esse cenário não negocia a credencial do serviço com o serviço antes de enviar a mensagem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb436-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="fb436-106">Além disso, como isso requer o protocolo Kerberos, esse cenário requer um ambiente de domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="fb436-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="fb436-107">![Segurança de mensagem sem negociação de credencial](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="fb436-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="fb436-108">Característica</span><span class="sxs-lookup"><span data-stu-id="fb436-108">Characteristic</span></span>|<span data-ttu-id="fb436-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb436-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="fb436-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="fb436-110">Security Mode</span></span>|<span data-ttu-id="fb436-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="fb436-111">Message</span></span>|
|<span data-ttu-id="fb436-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="fb436-112">Interoperability</span></span>|<span data-ttu-id="fb436-113">Sim, WS-Security com clientes compatíveis com o perfil de token Kerberos</span><span class="sxs-lookup"><span data-stu-id="fb436-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="fb436-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="fb436-114">Authentication (Server)</span></span>|<span data-ttu-id="fb436-115">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="fb436-115">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="fb436-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="fb436-116">Authentication (Client)</span></span>|<span data-ttu-id="fb436-117">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="fb436-117">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="fb436-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="fb436-118">Integrity</span></span>|<span data-ttu-id="fb436-119">Sim</span><span class="sxs-lookup"><span data-stu-id="fb436-119">Yes</span></span>|
|<span data-ttu-id="fb436-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="fb436-120">Confidentiality</span></span>|<span data-ttu-id="fb436-121">Sim</span><span class="sxs-lookup"><span data-stu-id="fb436-121">Yes</span></span>|
|<span data-ttu-id="fb436-122">Transport</span><span class="sxs-lookup"><span data-stu-id="fb436-122">Transport</span></span>|<span data-ttu-id="fb436-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="fb436-123">HTTP</span></span>|
|<span data-ttu-id="fb436-124">Binding</span><span class="sxs-lookup"><span data-stu-id="fb436-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="fb436-125">Service</span><span class="sxs-lookup"><span data-stu-id="fb436-125">Service</span></span>

<span data-ttu-id="fb436-126">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="fb436-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fb436-127">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="fb436-127">Do one of the following:</span></span>

- <span data-ttu-id="fb436-128">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="fb436-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="fb436-129">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fb436-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="fb436-130">Código</span><span class="sxs-lookup"><span data-stu-id="fb436-130">Code</span></span>

<span data-ttu-id="fb436-131">O código a seguir cria um ponto de extremidade de serviço que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fb436-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="fb436-132">O código desabilita a negociação de credencial de serviço e o estabelecimento de um símbolo de contexto de segurança (SCT).</span><span class="sxs-lookup"><span data-stu-id="fb436-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="fb436-133">Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso ao SPN (nome da entidade de serviço) registrado com o domínio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb436-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="fb436-134">Você pode fazer isso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="fb436-134">You can do this in two ways:</span></span>

1. <span data-ttu-id="fb436-135">Use a conta `NetworkService` ou `LocalSystem` para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="fb436-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="fb436-136">Como essas contas têm acesso ao SPN do computador que é estabelecido quando o computador ingressa no domínio de Active Directory, o WCF gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade do serviço nos metadados do serviço (descrição de serviços Web Idioma ou WSDL).</span><span class="sxs-lookup"><span data-stu-id="fb436-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="fb436-137">Use uma conta de domínio Active Directory arbitrária para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="fb436-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="fb436-138">Nesse caso, você precisa estabelecer um SPN para essa conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="fb436-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="fb436-139">Uma maneira de fazer isso é usar a ferramenta utilitário SetSPN. exe.</span><span class="sxs-lookup"><span data-stu-id="fb436-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="fb436-140">Depois que o SPN for criado para a conta do serviço, configure o WCF para publicar esse SPN nos clientes do serviço por meio de seus metadados (WSDL).</span><span class="sxs-lookup"><span data-stu-id="fb436-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="fb436-141">Isso é feito definindo a identidade do ponto de extremidade para o ponto de extremidade exposto, por meio de um arquivo ou código de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb436-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="fb436-142">O exemplo a seguir publica a identidade programaticamente.</span><span class="sxs-lookup"><span data-stu-id="fb436-142">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="fb436-143">Para obter mais informações sobre SPNs, o protocolo Kerberos e Active Directory, consulte [complemento técnico Kerberos para Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="fb436-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="fb436-144">Para obter mais informações sobre identidades de ponto de extremidade, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="fb436-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="fb436-145">Configuração do</span><span class="sxs-lookup"><span data-stu-id="fb436-145">Configuration</span></span>

<span data-ttu-id="fb436-146">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="fb436-146">The following configuration can be used instead of the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="fb436-147">Cliente</span><span class="sxs-lookup"><span data-stu-id="fb436-147">Client</span></span>

<span data-ttu-id="fb436-148">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="fb436-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fb436-149">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="fb436-149">Do one of the following:</span></span>

- <span data-ttu-id="fb436-150">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="fb436-150">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="fb436-151">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fb436-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="fb436-152">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="fb436-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="fb436-153">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fb436-153">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="fb436-154">Código</span><span class="sxs-lookup"><span data-stu-id="fb436-154">Code</span></span>

<span data-ttu-id="fb436-155">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="fb436-155">The following code configures the client.</span></span> <span data-ttu-id="fb436-156">O modo de segurança é definido como mensagem e o tipo de credencial do cliente é definido como Windows.</span><span class="sxs-lookup"><span data-stu-id="fb436-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="fb436-157">Observe que as propriedades <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> e <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> são definidas como `false`.</span><span class="sxs-lookup"><span data-stu-id="fb436-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="fb436-158">Para usar o tipo de credencial do Windows sem negociação, o cliente deve ser configurado com o SPN da conta do serviço antes de iniciar a comunicação com o serviço.</span><span class="sxs-lookup"><span data-stu-id="fb436-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="fb436-159">O cliente usa o SPN para obter o token Kerberos para autenticar e proteger a comunicação com o serviço.</span><span class="sxs-lookup"><span data-stu-id="fb436-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="fb436-160">O exemplo a seguir mostra como configurar o cliente com o SPN do serviço.</span><span class="sxs-lookup"><span data-stu-id="fb436-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="fb436-161">Se você estiver usando a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o cliente, o SPN do serviço será propagado automaticamente para o cliente por meio dos metadados do serviço (WSDL), se os metadados do serviço contiverem essas informações.</span><span class="sxs-lookup"><span data-stu-id="fb436-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="fb436-162">Para obter mais informações sobre como configurar o serviço para incluir seu SPN nos metadados do serviço, consulte a seção "serviço" mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="fb436-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="fb436-163">Para obter mais informações sobre SPNs, Kerberos e Active Directory, consulte [complemento técnico do Kerberos para Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="fb436-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="fb436-164">Para obter mais informações sobre identidades de ponto de extremidade, consulte o tópico [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) .</span><span class="sxs-lookup"><span data-stu-id="fb436-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="fb436-165">Configuração do</span><span class="sxs-lookup"><span data-stu-id="fb436-165">Configuration</span></span>

<span data-ttu-id="fb436-166">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="fb436-166">The following code configures the client.</span></span> <span data-ttu-id="fb436-167">Observe que o elemento [\<serviceprincipalname >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) deve ser definido para corresponder ao SPN do serviço como registrado para a conta do serviço no domínio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fb436-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fb436-168">Veja também</span><span class="sxs-lookup"><span data-stu-id="fb436-168">See also</span></span>

- [<span data-ttu-id="fb436-169">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="fb436-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="fb436-170">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="fb436-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- <span data-ttu-id="fb436-171">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fb436-171">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
