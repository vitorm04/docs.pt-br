---
title: Segurança de mensagem com um nome de usuário cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 872283f55ae6f085b2cdf5c64c229b9d459b71f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701268"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="18a93-102">Segurança de mensagem com um nome de usuário cliente</span><span class="sxs-lookup"><span data-stu-id="18a93-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="18a93-103">A ilustração a seguir mostra um serviço Windows Communication Foundation (WCF) e o cliente protegido usando a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="18a93-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="18a93-104">O serviço é autenticado com um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="18a93-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="18a93-105">O cliente é autenticado usando um nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="18a93-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="18a93-106">Para um aplicativo de exemplo, consulte [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="18a93-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="18a93-107">![Segurança de mensagem usando a autenticação de nome de usuário](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="18a93-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="18a93-108">Característica</span><span class="sxs-lookup"><span data-stu-id="18a93-108">Characteristic</span></span>|<span data-ttu-id="18a93-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="18a93-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="18a93-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="18a93-110">Security Mode</span></span>|<span data-ttu-id="18a93-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="18a93-111">Message</span></span>|  
|<span data-ttu-id="18a93-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="18a93-112">Interoperability</span></span>|<span data-ttu-id="18a93-113">Windows Communication Foundation (WCF) apenas</span><span class="sxs-lookup"><span data-stu-id="18a93-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="18a93-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="18a93-114">Authentication (Server)</span></span>|<span data-ttu-id="18a93-115">Negociação inicial exige a autenticação de servidor</span><span class="sxs-lookup"><span data-stu-id="18a93-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="18a93-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="18a93-116">Authentication (Client)</span></span>|<span data-ttu-id="18a93-117">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="18a93-117">User name/password</span></span>|  
|<span data-ttu-id="18a93-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="18a93-118">Integrity</span></span>|<span data-ttu-id="18a93-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="18a93-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="18a93-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="18a93-120">Confidentiality</span></span>|<span data-ttu-id="18a93-121">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="18a93-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="18a93-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="18a93-122">Transport</span></span>|<span data-ttu-id="18a93-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="18a93-123">HTTP</span></span>|  
|<span data-ttu-id="18a93-124">Associação</span><span class="sxs-lookup"><span data-stu-id="18a93-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="18a93-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="18a93-125">Service</span></span>  
 <span data-ttu-id="18a93-126">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="18a93-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="18a93-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="18a93-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="18a93-128">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="18a93-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="18a93-129">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="18a93-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18a93-130">Código</span><span class="sxs-lookup"><span data-stu-id="18a93-130">Code</span></span>  
 <span data-ttu-id="18a93-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="18a93-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="18a93-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="18a93-132">Configuration</span></span>  
 <span data-ttu-id="18a93-133">A configuração a seguir pode ser usada em vez do código:</span><span class="sxs-lookup"><span data-stu-id="18a93-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="18a93-134">Cliente</span><span class="sxs-lookup"><span data-stu-id="18a93-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="18a93-135">Código</span><span class="sxs-lookup"><span data-stu-id="18a93-135">Code</span></span>  
 <span data-ttu-id="18a93-136">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="18a93-136">The following code creates the client.</span></span> <span data-ttu-id="18a93-137">A associação é a segurança de modo de mensagem e o tipo de credencial de cliente é definido como `UserName`.</span><span class="sxs-lookup"><span data-stu-id="18a93-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="18a93-138">O nome de usuário e a senha só podem ser especificados usando o código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="18a93-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="18a93-139">O código para retornar o nome de usuário e a senha não é mostrado aqui porque ele deve ser feito no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18a93-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="18a93-140">Por exemplo, use uma caixa de diálogo do Windows Forms para consultar o usuário para os dados.</span><span class="sxs-lookup"><span data-stu-id="18a93-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="18a93-141">Configuração</span><span class="sxs-lookup"><span data-stu-id="18a93-141">Configuration</span></span>  
 <span data-ttu-id="18a93-142">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="18a93-142">The following code configures the client.</span></span> <span data-ttu-id="18a93-143">A associação é a segurança de modo de mensagem e o tipo de credencial de cliente é definido como `UserName`.</span><span class="sxs-lookup"><span data-stu-id="18a93-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="18a93-144">O nome de usuário e a senha só podem ser especificados usando o código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="18a93-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a93-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18a93-145">See also</span></span>
- [<span data-ttu-id="18a93-146">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="18a93-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="18a93-147">Nome de usuário de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="18a93-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="18a93-148">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="18a93-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="18a93-149">\<identity></span><span class="sxs-lookup"><span data-stu-id="18a93-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [<span data-ttu-id="18a93-150">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="18a93-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
