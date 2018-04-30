---
title: Segurança de transporte com autenticação básica
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
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
caps.latest.revision: 18
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 7430767c80515d14ae23e17ae2b94e0acc97ff30
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="86fea-102">Segurança de transporte com autenticação básica</span><span class="sxs-lookup"><span data-stu-id="86fea-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="86fea-103">A ilustração a seguir mostra um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="86fea-103">The following illustration shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client.</span></span> <span data-ttu-id="86fea-104">O servidor precisa de um certificado x. 509 válido que pode ser usado para Secure Sockets Layer (SSL) e os clientes devem confiar em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="86fea-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="86fea-105">Além disso, o serviço Web já tem uma implementação de SSL que pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="86fea-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="86fea-106">Para obter mais informações sobre como habilitar a autenticação básica no Internet Information Services (IIS), consulte [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="86fea-106">For more information about enabling basic authentication on Internet Information Services (IIS), see [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="86fea-107">![Segurança com a autenticação básica de transporte](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="86fea-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="86fea-108">Característica</span><span class="sxs-lookup"><span data-stu-id="86fea-108">Characteristic</span></span>|<span data-ttu-id="86fea-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="86fea-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="86fea-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="86fea-110">Security Mode</span></span>|<span data-ttu-id="86fea-111">Transporte</span><span class="sxs-lookup"><span data-stu-id="86fea-111">Transport</span></span>|  
|<span data-ttu-id="86fea-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="86fea-112">Interoperability</span></span>|<span data-ttu-id="86fea-113">Com os serviços e clientes de serviço da Web existentes</span><span class="sxs-lookup"><span data-stu-id="86fea-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="86fea-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="86fea-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="86fea-115">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="86fea-115">Authentication (Client)</span></span>|<span data-ttu-id="86fea-116">Sim (usando HTTPS)</span><span class="sxs-lookup"><span data-stu-id="86fea-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="86fea-117">Sim (por meio do nome de usuário/senha)</span><span class="sxs-lookup"><span data-stu-id="86fea-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="86fea-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="86fea-118">Integrity</span></span>|<span data-ttu-id="86fea-119">Sim</span><span class="sxs-lookup"><span data-stu-id="86fea-119">Yes</span></span>|  
|<span data-ttu-id="86fea-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="86fea-120">Confidentiality</span></span>|<span data-ttu-id="86fea-121">Sim</span><span class="sxs-lookup"><span data-stu-id="86fea-121">Yes</span></span>|  
|<span data-ttu-id="86fea-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="86fea-122">Transport</span></span>|<span data-ttu-id="86fea-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="86fea-123">HTTPS</span></span>|  
|<span data-ttu-id="86fea-124">Associação</span><span class="sxs-lookup"><span data-stu-id="86fea-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="86fea-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="86fea-125">Service</span></span>  
 <span data-ttu-id="86fea-126">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="86fea-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="86fea-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="86fea-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="86fea-128">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="86fea-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="86fea-129">Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86fea-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="86fea-130">Código</span><span class="sxs-lookup"><span data-stu-id="86fea-130">Code</span></span>  
 <span data-ttu-id="86fea-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa um nome de usuário de domínio do Windows e uma senha para a segurança de transferência.</span><span class="sxs-lookup"><span data-stu-id="86fea-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="86fea-132">Observe que o serviço requer um certificado x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="86fea-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="86fea-133">Para obter mais informações, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="86fea-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="86fea-134">Configuração</span><span class="sxs-lookup"><span data-stu-id="86fea-134">Configuration</span></span>  
 <span data-ttu-id="86fea-135">O exemplo a seguir configura um serviço para usar a autenticação básica com segurança em nível de transporte:</span><span class="sxs-lookup"><span data-stu-id="86fea-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="86fea-136">Cliente</span><span class="sxs-lookup"><span data-stu-id="86fea-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="86fea-137">Código</span><span class="sxs-lookup"><span data-stu-id="86fea-137">Code</span></span>  
 <span data-ttu-id="86fea-138">O código a seguir mostra o código de cliente que inclui o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="86fea-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="86fea-139">Observe que o usuário deve fornecer um nome de usuário do Windows e senha válidas.</span><span class="sxs-lookup"><span data-stu-id="86fea-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="86fea-140">O código para retornar o nome de usuário e a senha não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="86fea-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="86fea-141">Use uma caixa de diálogo ou outra interface para consultar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="86fea-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86fea-142">Nome de usuário e senha só podem ser definidas usando código.</span><span class="sxs-lookup"><span data-stu-id="86fea-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="86fea-143">Configuração</span><span class="sxs-lookup"><span data-stu-id="86fea-143">Configuration</span></span>  
 <span data-ttu-id="86fea-144">O código a seguir mostra a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="86fea-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86fea-145">Você não pode usar a configuração para definir o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="86fea-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="86fea-146">A configuração mostrada aqui deve ser aumentada usando código para definir o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="86fea-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86fea-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86fea-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="86fea-148">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="86fea-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="86fea-149">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="86fea-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="86fea-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="86fea-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="86fea-151">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="86fea-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="86fea-152">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="86fea-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
