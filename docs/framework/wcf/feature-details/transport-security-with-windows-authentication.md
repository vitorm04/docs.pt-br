---
title: Segurança de transporte com autenticação do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6392ea0f17596406a8671a039bd78777d9e11e42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742651"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="0bfd3-102">Segurança de transporte com autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="0bfd3-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="0bfd3-103">O cenário a seguir mostra um cliente Windows Communication Foundation (WCF) e um serviço protegido pela segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="0bfd3-104">Para obter mais informações sobre programação, consulte [como proteger um serviço com credenciais do Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="0bfd3-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="0bfd3-105">Um serviço Web de intranet exibe informações de recursos humanos.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="0bfd3-106">O cliente é um aplicativo do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-106">The client is a Windows Form application.</span></span> <span data-ttu-id="0bfd3-107">O aplicativo é implantado em um domínio com um controlador Kerberos protegendo o domínio.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Segurança de transporte com autenticação do Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="0bfd3-109">Característica</span><span class="sxs-lookup"><span data-stu-id="0bfd3-109">Characteristic</span></span>|<span data-ttu-id="0bfd3-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bfd3-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0bfd3-111">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="0bfd3-111">Security Mode</span></span>|<span data-ttu-id="0bfd3-112">Transporte</span><span class="sxs-lookup"><span data-stu-id="0bfd3-112">Transport</span></span>|  
|<span data-ttu-id="0bfd3-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="0bfd3-113">Interoperability</span></span>|<span data-ttu-id="0bfd3-114">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="0bfd3-114">WCF only</span></span>|  
|<span data-ttu-id="0bfd3-115">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="0bfd3-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="0bfd3-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="0bfd3-116">Authentication (Client)</span></span>|<span data-ttu-id="0bfd3-117">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="0bfd3-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="0bfd3-118">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="0bfd3-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="0bfd3-119">Integridade</span><span class="sxs-lookup"><span data-stu-id="0bfd3-119">Integrity</span></span>|<span data-ttu-id="0bfd3-120">Sim</span><span class="sxs-lookup"><span data-stu-id="0bfd3-120">Yes</span></span>|  
|<span data-ttu-id="0bfd3-121">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="0bfd3-121">Confidentiality</span></span>|<span data-ttu-id="0bfd3-122">Sim</span><span class="sxs-lookup"><span data-stu-id="0bfd3-122">Yes</span></span>|  
|<span data-ttu-id="0bfd3-123">Transporte</span><span class="sxs-lookup"><span data-stu-id="0bfd3-123">Transport</span></span>|<span data-ttu-id="0bfd3-124">Virtual. Protocol</span><span class="sxs-lookup"><span data-stu-id="0bfd3-124">NET.TCP</span></span>|  
|<span data-ttu-id="0bfd3-125">Associação</span><span class="sxs-lookup"><span data-stu-id="0bfd3-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="0bfd3-126">Service</span><span class="sxs-lookup"><span data-stu-id="0bfd3-126">Service</span></span>  
 <span data-ttu-id="0bfd3-127">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="0bfd3-128">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="0bfd3-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="0bfd3-129">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="0bfd3-130">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0bfd3-131">Código</span><span class="sxs-lookup"><span data-stu-id="0bfd3-131">Code</span></span>  
 <span data-ttu-id="0bfd3-132">O código a seguir mostra como criar um ponto de extremidade de serviço que usa uma segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="0bfd3-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="0bfd3-133">Configuration</span></span>  
 <span data-ttu-id="0bfd3-134">A configuração a seguir pode ser usada em vez do código para configurar o ponto de extremidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="0bfd3-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="0bfd3-135">Cliente</span><span class="sxs-lookup"><span data-stu-id="0bfd3-135">Client</span></span>  
 <span data-ttu-id="0bfd3-136">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="0bfd3-137">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="0bfd3-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="0bfd3-138">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="0bfd3-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="0bfd3-139">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="0bfd3-140">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="0bfd3-141">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0bfd3-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="0bfd3-142">Código</span><span class="sxs-lookup"><span data-stu-id="0bfd3-142">Code</span></span>  
 <span data-ttu-id="0bfd3-143">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-143">The following code creates the client.</span></span> <span data-ttu-id="0bfd3-144">A associação é configurada para usar a segurança do modo de transporte, com o transporte TCP, com o tipo de credencial do cliente definido como Windows.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="0bfd3-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="0bfd3-145">Configuration</span></span>  
 <span data-ttu-id="0bfd3-146">A configuração a seguir pode ser usada em vez do código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="0bfd3-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0bfd3-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bfd3-147">See also</span></span>

- [<span data-ttu-id="0bfd3-148">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="0bfd3-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="0bfd3-149">Como proteger um serviço com credenciais Windows</span><span class="sxs-lookup"><span data-stu-id="0bfd3-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="0bfd3-150">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0bfd3-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
