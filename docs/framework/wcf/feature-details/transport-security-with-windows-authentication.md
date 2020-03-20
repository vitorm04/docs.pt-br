---
title: Segurança de transporte com autenticação do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184308"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="f2bd1-102">Segurança de transporte com autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="f2bd1-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="f2bd1-103">O cenário a seguir mostra um cliente e serviço da Windows Communication Foundation (WCF) protegido pela segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="f2bd1-104">Para obter mais informações sobre programação, consulte [Como: Proteger um serviço com credenciais do Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="f2bd1-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="f2bd1-105">Um serviço web intranet exibe informações sobre recursos humanos.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="f2bd1-106">O cliente é um aplicativo do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-106">The client is a Windows Form application.</span></span> <span data-ttu-id="f2bd1-107">O aplicativo é implantado em um domínio com um controlador Kerberos protegendo o domínio.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Segurança de transporte com autenticação do Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="f2bd1-109">Característica</span><span class="sxs-lookup"><span data-stu-id="f2bd1-109">Characteristic</span></span>|<span data-ttu-id="f2bd1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2bd1-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f2bd1-111">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="f2bd1-111">Security Mode</span></span>|<span data-ttu-id="f2bd1-112">Transporte</span><span class="sxs-lookup"><span data-stu-id="f2bd1-112">Transport</span></span>|  
|<span data-ttu-id="f2bd1-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="f2bd1-113">Interoperability</span></span>|<span data-ttu-id="f2bd1-114">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="f2bd1-114">WCF only</span></span>|  
|<span data-ttu-id="f2bd1-115">Autenticação (Servidor)</span><span class="sxs-lookup"><span data-stu-id="f2bd1-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="f2bd1-116">Autenticação (Cliente)</span><span class="sxs-lookup"><span data-stu-id="f2bd1-116">Authentication (Client)</span></span>|<span data-ttu-id="f2bd1-117">Sim (usando autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="f2bd1-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="f2bd1-118">Sim (usando autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="f2bd1-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="f2bd1-119">Integridade</span><span class="sxs-lookup"><span data-stu-id="f2bd1-119">Integrity</span></span>|<span data-ttu-id="f2bd1-120">Sim</span><span class="sxs-lookup"><span data-stu-id="f2bd1-120">Yes</span></span>|  
|<span data-ttu-id="f2bd1-121">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="f2bd1-121">Confidentiality</span></span>|<span data-ttu-id="f2bd1-122">Sim</span><span class="sxs-lookup"><span data-stu-id="f2bd1-122">Yes</span></span>|  
|<span data-ttu-id="f2bd1-123">Transporte</span><span class="sxs-lookup"><span data-stu-id="f2bd1-123">Transport</span></span>|<span data-ttu-id="f2bd1-124">Net. Tcp</span><span class="sxs-lookup"><span data-stu-id="f2bd1-124">NET.TCP</span></span>|  
|<span data-ttu-id="f2bd1-125">Associação</span><span class="sxs-lookup"><span data-stu-id="f2bd1-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f2bd1-126">Serviço</span><span class="sxs-lookup"><span data-stu-id="f2bd1-126">Service</span></span>  
 <span data-ttu-id="f2bd1-127">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f2bd1-128">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="f2bd1-129">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f2bd1-130">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f2bd1-131">Código</span><span class="sxs-lookup"><span data-stu-id="f2bd1-131">Code</span></span>  
 <span data-ttu-id="f2bd1-132">O código a seguir mostra como criar um ponto final de serviço que usa uma segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="f2bd1-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="f2bd1-133">Configuration</span></span>  
 <span data-ttu-id="f2bd1-134">A configuração a seguir pode ser usada em vez do código para configurar o ponto final do serviço:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f2bd1-135">Cliente</span><span class="sxs-lookup"><span data-stu-id="f2bd1-135">Client</span></span>  
 <span data-ttu-id="f2bd1-136">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f2bd1-137">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="f2bd1-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="f2bd1-138">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="f2bd1-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="f2bd1-139">Crie um cliente que não defina nenhum endereço de ponto final.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f2bd1-140">Em vez disso, use o construtor cliente que toma o nome da configuração como argumento.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f2bd1-141">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="f2bd1-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f2bd1-142">Código</span><span class="sxs-lookup"><span data-stu-id="f2bd1-142">Code</span></span>  
 <span data-ttu-id="f2bd1-143">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-143">The following code creates the client.</span></span> <span data-ttu-id="f2bd1-144">A vinculação é configurada para usar a segurança do modo transporte, com o transporte TCP, com o tipo de credencial do cliente definido como Windows.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="f2bd1-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="f2bd1-145">Configuration</span></span>  
 <span data-ttu-id="f2bd1-146">A configuração a seguir pode ser usada em vez do código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f2bd1-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2bd1-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2bd1-147">See also</span></span>

- [<span data-ttu-id="f2bd1-148">Visão geral da segurança</span><span class="sxs-lookup"><span data-stu-id="f2bd1-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="f2bd1-149">Como proteger um serviço com credenciais Windows</span><span class="sxs-lookup"><span data-stu-id="f2bd1-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="f2bd1-150">[Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f2bd1-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
