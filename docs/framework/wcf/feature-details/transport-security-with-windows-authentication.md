---
title: Segurança de transporte com autenticação do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: bd4e12a861207e5318e8f3f34b38204f6724e7b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652586"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="5f0f2-102">Segurança de transporte com autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="5f0f2-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="5f0f2-103">O cenário a seguir mostra um serviço protegidos pela segurança do Windows e o cliente do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5f0f2-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="5f0f2-104">Para obter mais informações sobre a programação, consulte [como: Proteger um serviço com credenciais do Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="5f0f2-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="5f0f2-105">Um serviço Web de intranet exibe informações de recursos humanos.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="5f0f2-106">O cliente é um aplicativo de formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-106">The client is a Windows Form application.</span></span> <span data-ttu-id="5f0f2-107">O aplicativo é implantado em um domínio com um controlador de Kerberos a proteção do domínio.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="5f0f2-108">![Segurança com a autenticação do Windows de transporte](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="5f0f2-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="5f0f2-109">Característica</span><span class="sxs-lookup"><span data-stu-id="5f0f2-109">Characteristic</span></span>|<span data-ttu-id="5f0f2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f0f2-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5f0f2-111">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="5f0f2-111">Security Mode</span></span>|<span data-ttu-id="5f0f2-112">Transporte</span><span class="sxs-lookup"><span data-stu-id="5f0f2-112">Transport</span></span>|  
|<span data-ttu-id="5f0f2-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5f0f2-113">Interoperability</span></span>|<span data-ttu-id="5f0f2-114">Somente o WCF</span><span class="sxs-lookup"><span data-stu-id="5f0f2-114">WCF only</span></span>|  
|<span data-ttu-id="5f0f2-115">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="5f0f2-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="5f0f2-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="5f0f2-116">Authentication (Client)</span></span>|<span data-ttu-id="5f0f2-117">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="5f0f2-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="5f0f2-118">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="5f0f2-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="5f0f2-119">Integridade</span><span class="sxs-lookup"><span data-stu-id="5f0f2-119">Integrity</span></span>|<span data-ttu-id="5f0f2-120">Sim</span><span class="sxs-lookup"><span data-stu-id="5f0f2-120">Yes</span></span>|  
|<span data-ttu-id="5f0f2-121">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="5f0f2-121">Confidentiality</span></span>|<span data-ttu-id="5f0f2-122">Sim</span><span class="sxs-lookup"><span data-stu-id="5f0f2-122">Yes</span></span>|  
|<span data-ttu-id="5f0f2-123">Transporte</span><span class="sxs-lookup"><span data-stu-id="5f0f2-123">Transport</span></span>|<span data-ttu-id="5f0f2-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="5f0f2-124">NET.TCP</span></span>|  
|<span data-ttu-id="5f0f2-125">Associação</span><span class="sxs-lookup"><span data-stu-id="5f0f2-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5f0f2-126">Serviço</span><span class="sxs-lookup"><span data-stu-id="5f0f2-126">Service</span></span>  
 <span data-ttu-id="5f0f2-127">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5f0f2-128">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5f0f2-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5f0f2-129">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5f0f2-130">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f0f2-131">Código</span><span class="sxs-lookup"><span data-stu-id="5f0f2-131">Code</span></span>  
 <span data-ttu-id="5f0f2-132">O código a seguir mostra como criar um ponto de extremidade de serviço que usa uma segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="5f0f2-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="5f0f2-133">Configuration</span></span>  
 <span data-ttu-id="5f0f2-134">A configuração a seguir pode ser usada em vez do código para configurar o ponto de extremidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="5f0f2-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="5f0f2-135">Cliente</span><span class="sxs-lookup"><span data-stu-id="5f0f2-135">Client</span></span>  
 <span data-ttu-id="5f0f2-136">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5f0f2-137">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5f0f2-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5f0f2-138">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="5f0f2-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5f0f2-139">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5f0f2-140">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5f0f2-141">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5f0f2-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5f0f2-142">Código</span><span class="sxs-lookup"><span data-stu-id="5f0f2-142">Code</span></span>  
 <span data-ttu-id="5f0f2-143">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-143">The following code creates the client.</span></span> <span data-ttu-id="5f0f2-144">A associação está configurada para usar a segurança de modo de transporte, com o transporte TCP, com o tipo de credencial de cliente definido como Windows.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="5f0f2-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="5f0f2-145">Configuration</span></span>  
 <span data-ttu-id="5f0f2-146">A configuração a seguir pode ser usada em vez do código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5f0f2-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f0f2-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f0f2-147">See also</span></span>
- [<span data-ttu-id="5f0f2-148">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="5f0f2-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5f0f2-149">Como: Proteger um serviço com credenciais do Windows</span><span class="sxs-lookup"><span data-stu-id="5f0f2-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [<span data-ttu-id="5f0f2-150">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5f0f2-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
