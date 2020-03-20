---
title: Segurança de mensagem com um nome de usuário cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 3dd21268d4ea7dc59c74889ac94dc86678e91865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184634"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="10025-102">Segurança de mensagem com um nome de usuário cliente</span><span class="sxs-lookup"><span data-stu-id="10025-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="10025-103">A ilustração a seguir mostra um serviço da Windows Communication Foundation (WCF) e um cliente protegido usando segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="10025-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="10025-104">O serviço é autenticado com um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="10025-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="10025-105">O cliente autentica usando um nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="10025-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="10025-106">Para obter um aplicativo de exemplo, consulte [Nome do usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="10025-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="10025-107">![Segurança de mensagem usando autenticação de nome de usuário](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="10025-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="10025-108">Característica</span><span class="sxs-lookup"><span data-stu-id="10025-108">Characteristic</span></span>|<span data-ttu-id="10025-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="10025-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="10025-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="10025-110">Security Mode</span></span>|<span data-ttu-id="10025-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="10025-111">Message</span></span>|  
|<span data-ttu-id="10025-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="10025-112">Interoperability</span></span>|<span data-ttu-id="10025-113">Windows Communication Foundation (WCF) apenas</span><span class="sxs-lookup"><span data-stu-id="10025-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="10025-114">Autenticação (Servidor)</span><span class="sxs-lookup"><span data-stu-id="10025-114">Authentication (Server)</span></span>|<span data-ttu-id="10025-115">Negociação inicial requer autenticação do servidor</span><span class="sxs-lookup"><span data-stu-id="10025-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="10025-116">Autenticação (Cliente)</span><span class="sxs-lookup"><span data-stu-id="10025-116">Authentication (Client)</span></span>|<span data-ttu-id="10025-117">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="10025-117">User name/password</span></span>|  
|<span data-ttu-id="10025-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="10025-118">Integrity</span></span>|<span data-ttu-id="10025-119">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="10025-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="10025-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="10025-120">Confidentiality</span></span>|<span data-ttu-id="10025-121">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="10025-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="10025-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="10025-122">Transport</span></span>|<span data-ttu-id="10025-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="10025-123">HTTP</span></span>|  
|<span data-ttu-id="10025-124">Associação</span><span class="sxs-lookup"><span data-stu-id="10025-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="10025-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="10025-125">Service</span></span>  
 <span data-ttu-id="10025-126">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="10025-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="10025-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="10025-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="10025-128">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="10025-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="10025-129">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.</span><span class="sxs-lookup"><span data-stu-id="10025-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="10025-130">Código</span><span class="sxs-lookup"><span data-stu-id="10025-130">Code</span></span>  
 <span data-ttu-id="10025-131">O código a seguir mostra como criar um ponto final de serviço que usa a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="10025-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="10025-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="10025-132">Configuration</span></span>  
 <span data-ttu-id="10025-133">A seguinte configuração pode ser usada em vez do código:</span><span class="sxs-lookup"><span data-stu-id="10025-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="10025-134">Cliente</span><span class="sxs-lookup"><span data-stu-id="10025-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="10025-135">Código</span><span class="sxs-lookup"><span data-stu-id="10025-135">Code</span></span>  
 <span data-ttu-id="10025-136">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="10025-136">The following code creates the client.</span></span> <span data-ttu-id="10025-137">A vinculação é para a segurança do modo de `UserName`mensagem, e o tipo de credencial do cliente está definido como .</span><span class="sxs-lookup"><span data-stu-id="10025-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="10025-138">O nome de usuário e a senha só podem ser especificados usando código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="10025-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="10025-139">O código para devolver o nome de usuário e a senha não é mostrado aqui porque deve ser feito no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10025-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="10025-140">Por exemplo, use uma caixa de diálogo Formulários do Windows para consultar os dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="10025-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="10025-141">Configuração</span><span class="sxs-lookup"><span data-stu-id="10025-141">Configuration</span></span>  
 <span data-ttu-id="10025-142">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="10025-142">The following code configures the client.</span></span> <span data-ttu-id="10025-143">A vinculação é para a segurança do modo de `UserName`mensagem, e o tipo de credencial do cliente está definido como .</span><span class="sxs-lookup"><span data-stu-id="10025-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="10025-144">O nome de usuário e a senha só podem ser especificados usando código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="10025-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10025-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="10025-145">See also</span></span>

- [<span data-ttu-id="10025-146">Visão geral da segurança</span><span class="sxs-lookup"><span data-stu-id="10025-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="10025-147">Nome de usuário de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="10025-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="10025-148">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="10025-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="10025-149">\<>de identidade</span><span class="sxs-lookup"><span data-stu-id="10025-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="10025-150">[Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="10025-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
