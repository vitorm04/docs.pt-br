---
title: Segurança de transporte com autenticação básica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f29087b01dbd55f936462d3c4ee2a26bbfe97b9a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558959"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="22dcf-102">Segurança de transporte com autenticação básica</span><span class="sxs-lookup"><span data-stu-id="22dcf-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="22dcf-103">A ilustração a seguir mostra um serviço Windows Communication Foundation (WCF) e um cliente.</span><span class="sxs-lookup"><span data-stu-id="22dcf-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="22dcf-104">O servidor precisa de um certificado X.509 válido que pode ser usado para Secure Sockets Layer (SSL) e os clientes devem confiar em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="22dcf-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="22dcf-105">Além disso, o serviço Web já tem uma implementação de SSL que pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="22dcf-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="22dcf-106">Para obter mais informações sobre como habilitar a autenticação básica no Internet Information Services (IIS), consulte [ https://go.microsoft.com/fwlink/?LinkId=83822 ](https://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="22dcf-106">For more information about enabling basic authentication on Internet Information Services (IIS), see [https://go.microsoft.com/fwlink/?LinkId=83822](https://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="22dcf-107">![Com a autenticação básica de segurança do transporte](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="22dcf-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="22dcf-108">Característica</span><span class="sxs-lookup"><span data-stu-id="22dcf-108">Characteristic</span></span>|<span data-ttu-id="22dcf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="22dcf-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="22dcf-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="22dcf-110">Security Mode</span></span>|<span data-ttu-id="22dcf-111">Transporte</span><span class="sxs-lookup"><span data-stu-id="22dcf-111">Transport</span></span>|  
|<span data-ttu-id="22dcf-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="22dcf-112">Interoperability</span></span>|<span data-ttu-id="22dcf-113">Com os serviços e clientes de serviço Web existentes</span><span class="sxs-lookup"><span data-stu-id="22dcf-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="22dcf-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="22dcf-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="22dcf-115">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="22dcf-115">Authentication (Client)</span></span>|<span data-ttu-id="22dcf-116">Sim (usando HTTPS)</span><span class="sxs-lookup"><span data-stu-id="22dcf-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="22dcf-117">Sim (por meio do nome de usuário/senha)</span><span class="sxs-lookup"><span data-stu-id="22dcf-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="22dcf-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="22dcf-118">Integrity</span></span>|<span data-ttu-id="22dcf-119">Sim</span><span class="sxs-lookup"><span data-stu-id="22dcf-119">Yes</span></span>|  
|<span data-ttu-id="22dcf-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="22dcf-120">Confidentiality</span></span>|<span data-ttu-id="22dcf-121">Sim</span><span class="sxs-lookup"><span data-stu-id="22dcf-121">Yes</span></span>|  
|<span data-ttu-id="22dcf-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="22dcf-122">Transport</span></span>|<span data-ttu-id="22dcf-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="22dcf-123">HTTPS</span></span>|  
|<span data-ttu-id="22dcf-124">Associação</span><span class="sxs-lookup"><span data-stu-id="22dcf-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="22dcf-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="22dcf-125">Service</span></span>  
 <span data-ttu-id="22dcf-126">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="22dcf-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="22dcf-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="22dcf-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="22dcf-128">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="22dcf-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="22dcf-129">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="22dcf-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="22dcf-130">Código</span><span class="sxs-lookup"><span data-stu-id="22dcf-130">Code</span></span>  
 <span data-ttu-id="22dcf-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa um nome de usuário de domínio do Windows e uma senha para segurança de transferência.</span><span class="sxs-lookup"><span data-stu-id="22dcf-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="22dcf-132">Observe que o serviço requer um certificado x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="22dcf-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="22dcf-133">Para obter mais informações, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="22dcf-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="22dcf-134">Configuração</span><span class="sxs-lookup"><span data-stu-id="22dcf-134">Configuration</span></span>  
 <span data-ttu-id="22dcf-135">O exemplo a seguir configura um serviço para usar a autenticação básica com segurança em nível de transporte:</span><span class="sxs-lookup"><span data-stu-id="22dcf-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="22dcf-136">Cliente</span><span class="sxs-lookup"><span data-stu-id="22dcf-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="22dcf-137">Código</span><span class="sxs-lookup"><span data-stu-id="22dcf-137">Code</span></span>  
 <span data-ttu-id="22dcf-138">O código a seguir mostra o código do cliente que inclui o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="22dcf-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="22dcf-139">Observe que o usuário deve fornecer um nome de usuário do Windows e uma senha válida.</span><span class="sxs-lookup"><span data-stu-id="22dcf-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="22dcf-140">O código para retornar o nome de usuário e a senha não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="22dcf-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="22dcf-141">Use uma caixa de diálogo ou outra interface para consultar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="22dcf-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22dcf-142">Nome de usuário e senha só podem ser definidos usando código.</span><span class="sxs-lookup"><span data-stu-id="22dcf-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="22dcf-143">Configuração</span><span class="sxs-lookup"><span data-stu-id="22dcf-143">Configuration</span></span>  
 <span data-ttu-id="22dcf-144">O código a seguir mostra a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="22dcf-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22dcf-145">Você não pode usar a configuração para definir o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="22dcf-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="22dcf-146">A configuração mostrada aqui deve ser aumentada usando código para definir o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="22dcf-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22dcf-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22dcf-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="22dcf-148">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="22dcf-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="22dcf-149">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="22dcf-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="22dcf-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="22dcf-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="22dcf-151">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="22dcf-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="22dcf-152">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="22dcf-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
