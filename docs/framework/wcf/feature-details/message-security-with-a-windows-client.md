---
title: Segurança de mensagem com um cliente do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 794a3d8e118cadd2a2752e1bbf85ef930deb2f27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922780"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="5a4f0-102">Segurança de mensagem com um cliente do Windows</span><span class="sxs-lookup"><span data-stu-id="5a4f0-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="5a4f0-103">Este cenário mostra que um cliente do Windows Communication Foundation (WCF) e o servidor protegido pelo modo de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="5a4f0-104">O cliente e o serviço são autenticados usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="5a4f0-105">![Segurança com um cliente do Windows da mensagem](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="5a4f0-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="5a4f0-106">Característica</span><span class="sxs-lookup"><span data-stu-id="5a4f0-106">Characteristic</span></span>|<span data-ttu-id="5a4f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a4f0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5a4f0-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="5a4f0-108">Security Mode</span></span>|<span data-ttu-id="5a4f0-109">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5a4f0-109">Message</span></span>|  
|<span data-ttu-id="5a4f0-110">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5a4f0-110">Interoperability</span></span>|<span data-ttu-id="5a4f0-111">Somente o WCF</span><span class="sxs-lookup"><span data-stu-id="5a4f0-111">WCF Only</span></span>|  
|<span data-ttu-id="5a4f0-112">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="5a4f0-112">Authentication (Server)</span></span>|<span data-ttu-id="5a4f0-113">Autenticação mútua do servidor e cliente</span><span class="sxs-lookup"><span data-stu-id="5a4f0-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="5a4f0-114">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="5a4f0-114">Authentication (Client)</span></span>|<span data-ttu-id="5a4f0-115">Autenticação mútua do servidor e cliente</span><span class="sxs-lookup"><span data-stu-id="5a4f0-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="5a4f0-116">Integridade</span><span class="sxs-lookup"><span data-stu-id="5a4f0-116">Integrity</span></span>|<span data-ttu-id="5a4f0-117">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="5a4f0-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="5a4f0-118">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="5a4f0-118">Confidentiality</span></span>|<span data-ttu-id="5a4f0-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="5a4f0-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="5a4f0-120">Transporte</span><span class="sxs-lookup"><span data-stu-id="5a4f0-120">Transport</span></span>|<span data-ttu-id="5a4f0-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="5a4f0-121">NET.TCP</span></span>|  
|<span data-ttu-id="5a4f0-122">Associação</span><span class="sxs-lookup"><span data-stu-id="5a4f0-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5a4f0-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="5a4f0-123">Service</span></span>  
 <span data-ttu-id="5a4f0-124">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5a4f0-125">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5a4f0-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5a4f0-126">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5a4f0-127">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5a4f0-128">Código</span><span class="sxs-lookup"><span data-stu-id="5a4f0-128">Code</span></span>  
 <span data-ttu-id="5a4f0-129">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem para estabelecer um contexto de seguro com uma máquina Windows.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="5a4f0-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="5a4f0-130">Configuration</span></span>  
 <span data-ttu-id="5a4f0-131">A configuração a seguir pode ser usada em vez do código para configurar o serviço:</span><span class="sxs-lookup"><span data-stu-id="5a4f0-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="5a4f0-132">Cliente</span><span class="sxs-lookup"><span data-stu-id="5a4f0-132">Client</span></span>  
 <span data-ttu-id="5a4f0-133">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5a4f0-134">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5a4f0-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5a4f0-135">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="5a4f0-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5a4f0-136">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5a4f0-137">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5a4f0-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5a4f0-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5a4f0-139">Código</span><span class="sxs-lookup"><span data-stu-id="5a4f0-139">Code</span></span>  
 <span data-ttu-id="5a4f0-140">O código a seguir cria um cliente.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-140">The following code creates a client.</span></span> <span data-ttu-id="5a4f0-141">A associação é a segurança de modo de mensagem e o tipo de credencial de cliente é definido como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="5a4f0-142">Configuração</span><span class="sxs-lookup"><span data-stu-id="5a4f0-142">Configuration</span></span>  
 <span data-ttu-id="5a4f0-143">A configuração a seguir é usada para definir as propriedades de cliente.</span><span class="sxs-lookup"><span data-stu-id="5a4f0-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a4f0-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a4f0-144">See also</span></span>

- [<span data-ttu-id="5a4f0-145">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="5a4f0-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5a4f0-146">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5a4f0-146">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
