---
title: Segurança de transporte com um cliente anônimo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 858ceb217ce30708a7d24c62ca18f8f59ba49d4c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183055"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="198e6-102">Segurança de transporte com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="198e6-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="198e6-103">Este cenário do Windows Communication Foundation (WCF) usa a segurança de transporte (HTTPS) para garantir a confidencialidade e integridade.</span><span class="sxs-lookup"><span data-stu-id="198e6-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="198e6-104">O servidor deve ser autenticado com um certificado Secure Sockets Layer (SSL) e os clientes devem confiar em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="198e6-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="198e6-105">O cliente não está autenticado por qualquer mecanismo e é, portanto, anônimo.</span><span class="sxs-lookup"><span data-stu-id="198e6-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="198e6-106">Para um aplicativo de exemplo, consulte [segurança de transporte WS](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="198e6-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> <span data-ttu-id="198e6-107">Para obter mais informações sobre a segurança de transporte, consulte [visão geral da segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198e6-107">For more information about transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 <span data-ttu-id="198e6-108">Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="198e6-108">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="198e6-109">![Usando a segurança de transporte com um cliente anônimo](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="198e6-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="198e6-110">Característica</span><span class="sxs-lookup"><span data-stu-id="198e6-110">Characteristic</span></span>|<span data-ttu-id="198e6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="198e6-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="198e6-112">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="198e6-112">Security Mode</span></span>|<span data-ttu-id="198e6-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="198e6-113">Transport</span></span>|  
|<span data-ttu-id="198e6-114">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="198e6-114">Interoperability</span></span>|<span data-ttu-id="198e6-115">Com clientes e serviços Web existentes</span><span class="sxs-lookup"><span data-stu-id="198e6-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="198e6-116">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="198e6-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="198e6-117">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="198e6-117">Authentication (Client)</span></span>|<span data-ttu-id="198e6-118">Sim</span><span class="sxs-lookup"><span data-stu-id="198e6-118">Yes</span></span><br /><br /> <span data-ttu-id="198e6-119">Nível de aplicativo (não há suporte do WCF)</span><span class="sxs-lookup"><span data-stu-id="198e6-119">Application level (no WCF support)</span></span>|  
|<span data-ttu-id="198e6-120">Integridade</span><span class="sxs-lookup"><span data-stu-id="198e6-120">Integrity</span></span>|<span data-ttu-id="198e6-121">Sim</span><span class="sxs-lookup"><span data-stu-id="198e6-121">Yes</span></span>|  
|<span data-ttu-id="198e6-122">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="198e6-122">Confidentiality</span></span>|<span data-ttu-id="198e6-123">Sim</span><span class="sxs-lookup"><span data-stu-id="198e6-123">Yes</span></span>|  
|<span data-ttu-id="198e6-124">Transporte</span><span class="sxs-lookup"><span data-stu-id="198e6-124">Transport</span></span>|<span data-ttu-id="198e6-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="198e6-125">HTTPS</span></span>|  
|<span data-ttu-id="198e6-126">Associação</span><span class="sxs-lookup"><span data-stu-id="198e6-126">Binding</span></span>|<span data-ttu-id="198e6-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="198e6-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="198e6-128">Serviço</span><span class="sxs-lookup"><span data-stu-id="198e6-128">Service</span></span>  
 <span data-ttu-id="198e6-129">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="198e6-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="198e6-130">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="198e6-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="198e6-131">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="198e6-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="198e6-132">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="198e6-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="198e6-133">Código</span><span class="sxs-lookup"><span data-stu-id="198e6-133">Code</span></span>  
 <span data-ttu-id="198e6-134">O código a seguir mostra como criar um ponto de extremidade usando a segurança de transporte:</span><span class="sxs-lookup"><span data-stu-id="198e6-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="198e6-135">Configuração</span><span class="sxs-lookup"><span data-stu-id="198e6-135">Configuration</span></span>  
 <span data-ttu-id="198e6-136">O código a seguir define o mesmo ponto de extremidade usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="198e6-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="198e6-137">O cliente não está autenticado por qualquer mecanismo e, portanto, é anônimo.</span><span class="sxs-lookup"><span data-stu-id="198e6-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="https://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="198e6-138">Cliente</span><span class="sxs-lookup"><span data-stu-id="198e6-138">Client</span></span>  
 <span data-ttu-id="198e6-139">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="198e6-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="198e6-140">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="198e6-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="198e6-141">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="198e6-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="198e6-142">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="198e6-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="198e6-143">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="198e6-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="198e6-144">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="198e6-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="198e6-145">Código</span><span class="sxs-lookup"><span data-stu-id="198e6-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="198e6-146">Configuração</span><span class="sxs-lookup"><span data-stu-id="198e6-146">Configuration</span></span>  
 <span data-ttu-id="198e6-147">A configuração a seguir pode ser usada em vez do código para configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="198e6-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
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
  
## <a name="see-also"></a><span data-ttu-id="198e6-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="198e6-148">See Also</span></span>  
 [<span data-ttu-id="198e6-149">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="198e6-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="198e6-150">Segurança de transporte de WS</span><span class="sxs-lookup"><span data-stu-id="198e6-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="198e6-151">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="198e6-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="198e6-152">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="198e6-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
