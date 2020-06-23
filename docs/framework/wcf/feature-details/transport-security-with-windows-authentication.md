---
title: Segurança de transporte com autenticação do Windows
description: Examine este cenário, que mostra um cliente/serviço WCF protegido pela segurança do Windows. Neste exemplo, um serviço de intranet exibe informações de recursos humanos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: b6134d4cbdff0c1adea704a7f3aaff7e40fd75ec
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244758"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="7c0c4-104">Segurança de transporte com autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="7c0c4-104">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="7c0c4-105">O cenário a seguir mostra um cliente Windows Communication Foundation (WCF) e um serviço protegido pela segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="7c0c4-106">Para obter mais informações sobre programação, consulte [como proteger um serviço com credenciais do Windows](../how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="7c0c4-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="7c0c4-107">Um serviço Web de intranet exibe informações de recursos humanos.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="7c0c4-108">O cliente é um aplicativo do Windows Form.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-108">The client is a Windows Form application.</span></span> <span data-ttu-id="7c0c4-109">O aplicativo é implantado em um domínio com um controlador Kerberos protegendo o domínio.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Segurança de transporte com autenticação do Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="7c0c4-111">Característica</span><span class="sxs-lookup"><span data-stu-id="7c0c4-111">Characteristic</span></span>|<span data-ttu-id="7c0c4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c0c4-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7c0c4-113">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="7c0c4-113">Security Mode</span></span>|<span data-ttu-id="7c0c4-114">Transporte</span><span class="sxs-lookup"><span data-stu-id="7c0c4-114">Transport</span></span>|  
|<span data-ttu-id="7c0c4-115">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="7c0c4-115">Interoperability</span></span>|<span data-ttu-id="7c0c4-116">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="7c0c4-116">WCF only</span></span>|  
|<span data-ttu-id="7c0c4-117">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="7c0c4-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="7c0c4-118">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="7c0c4-118">Authentication (Client)</span></span>|<span data-ttu-id="7c0c4-119">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="7c0c4-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="7c0c4-120">Sim (usando a autenticação integrada do Windows)</span><span class="sxs-lookup"><span data-stu-id="7c0c4-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="7c0c4-121">Integridade</span><span class="sxs-lookup"><span data-stu-id="7c0c4-121">Integrity</span></span>|<span data-ttu-id="7c0c4-122">Yes</span><span class="sxs-lookup"><span data-stu-id="7c0c4-122">Yes</span></span>|  
|<span data-ttu-id="7c0c4-123">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="7c0c4-123">Confidentiality</span></span>|<span data-ttu-id="7c0c4-124">Yes</span><span class="sxs-lookup"><span data-stu-id="7c0c4-124">Yes</span></span>|  
|<span data-ttu-id="7c0c4-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="7c0c4-125">Transport</span></span>|<span data-ttu-id="7c0c4-126">Virtual. Protocol</span><span class="sxs-lookup"><span data-stu-id="7c0c4-126">NET.TCP</span></span>|  
|<span data-ttu-id="7c0c4-127">Associação</span><span class="sxs-lookup"><span data-stu-id="7c0c4-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="7c0c4-128">Serviço</span><span class="sxs-lookup"><span data-stu-id="7c0c4-128">Service</span></span>  
 <span data-ttu-id="7c0c4-129">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7c0c4-130">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="7c0c4-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="7c0c4-131">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="7c0c4-132">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7c0c4-133">Código</span><span class="sxs-lookup"><span data-stu-id="7c0c4-133">Code</span></span>  
 <span data-ttu-id="7c0c4-134">O código a seguir mostra como criar um ponto de extremidade de serviço que usa uma segurança do Windows.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="7c0c4-135">Configuração</span><span class="sxs-lookup"><span data-stu-id="7c0c4-135">Configuration</span></span>  
 <span data-ttu-id="7c0c4-136">A configuração a seguir pode ser usada em vez do código para configurar o ponto de extremidade de serviço:</span><span class="sxs-lookup"><span data-stu-id="7c0c4-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="7c0c4-137">Cliente</span><span class="sxs-lookup"><span data-stu-id="7c0c4-137">Client</span></span>  
 <span data-ttu-id="7c0c4-138">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7c0c4-139">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="7c0c4-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="7c0c4-140">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="7c0c4-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="7c0c4-141">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="7c0c4-142">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="7c0c4-143">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c0c4-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="7c0c4-144">Código</span><span class="sxs-lookup"><span data-stu-id="7c0c4-144">Code</span></span>  
 <span data-ttu-id="7c0c4-145">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-145">The following code creates the client.</span></span> <span data-ttu-id="7c0c4-146">A associação é configurada para usar a segurança do modo de transporte, com o transporte TCP, com o tipo de credencial do cliente definido como Windows.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="7c0c4-147">Configuração</span><span class="sxs-lookup"><span data-stu-id="7c0c4-147">Configuration</span></span>  
 <span data-ttu-id="7c0c4-148">A configuração a seguir pode ser usada em vez do código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7c0c4-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c0c4-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="7c0c4-149">See also</span></span>

- [<span data-ttu-id="7c0c4-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="7c0c4-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="7c0c4-151">Como proteger um serviço com credenciais Windows</span><span class="sxs-lookup"><span data-stu-id="7c0c4-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="7c0c4-152">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7c0c4-152">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
