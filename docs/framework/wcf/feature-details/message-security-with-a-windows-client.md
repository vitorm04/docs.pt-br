---
title: Segurança de mensagem com um cliente do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: c87583bec908c3465dedf7c542e30ce264cd7b47
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553773"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="08b54-102">Segurança de mensagem com um cliente do Windows</span><span class="sxs-lookup"><span data-stu-id="08b54-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="08b54-103">Esse cenário mostra um cliente Windows Communication Foundation (WCF) e um servidor protegido pelo modo de segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="08b54-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="08b54-104">O cliente e o serviço são autenticados usando as credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="08b54-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="08b54-105">![Segurança de mensagem com um cliente Windows](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="08b54-105">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="08b54-106">Característica</span><span class="sxs-lookup"><span data-stu-id="08b54-106">Characteristic</span></span>|<span data-ttu-id="08b54-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08b54-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="08b54-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="08b54-108">Security Mode</span></span>|<span data-ttu-id="08b54-109">Mensagem</span><span class="sxs-lookup"><span data-stu-id="08b54-109">Message</span></span>|  
|<span data-ttu-id="08b54-110">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="08b54-110">Interoperability</span></span>|<span data-ttu-id="08b54-111">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="08b54-111">WCF Only</span></span>|  
|<span data-ttu-id="08b54-112">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="08b54-112">Authentication (Server)</span></span>|<span data-ttu-id="08b54-113">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="08b54-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="08b54-114">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="08b54-114">Authentication (Client)</span></span>|<span data-ttu-id="08b54-115">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="08b54-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="08b54-116">Integridade</span><span class="sxs-lookup"><span data-stu-id="08b54-116">Integrity</span></span>|<span data-ttu-id="08b54-117">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="08b54-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="08b54-118">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="08b54-118">Confidentiality</span></span>|<span data-ttu-id="08b54-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="08b54-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="08b54-120">Transport</span><span class="sxs-lookup"><span data-stu-id="08b54-120">Transport</span></span>|<span data-ttu-id="08b54-121">Virtual. Protocol</span><span class="sxs-lookup"><span data-stu-id="08b54-121">NET.TCP</span></span>|  
|<span data-ttu-id="08b54-122">Associação</span><span class="sxs-lookup"><span data-stu-id="08b54-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="08b54-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="08b54-123">Service</span></span>  
 <span data-ttu-id="08b54-124">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="08b54-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="08b54-125">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="08b54-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="08b54-126">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="08b54-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="08b54-127">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="08b54-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="08b54-128">Código</span><span class="sxs-lookup"><span data-stu-id="08b54-128">Code</span></span>  
 <span data-ttu-id="08b54-129">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem para estabelecer um contexto seguro com um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="08b54-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="08b54-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="08b54-130">Configuration</span></span>  
 <span data-ttu-id="08b54-131">A configuração a seguir pode ser usada em vez do código para configurar o serviço:</span><span class="sxs-lookup"><span data-stu-id="08b54-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="08b54-132">Cliente</span><span class="sxs-lookup"><span data-stu-id="08b54-132">Client</span></span>  
 <span data-ttu-id="08b54-133">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="08b54-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="08b54-134">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="08b54-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="08b54-135">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="08b54-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="08b54-136">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="08b54-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="08b54-137">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="08b54-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="08b54-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="08b54-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="08b54-139">Código</span><span class="sxs-lookup"><span data-stu-id="08b54-139">Code</span></span>  
 <span data-ttu-id="08b54-140">O código a seguir cria um cliente.</span><span class="sxs-lookup"><span data-stu-id="08b54-140">The following code creates a client.</span></span> <span data-ttu-id="08b54-141">A associação é a segurança do modo de mensagem e o tipo de credencial do cliente é definido como `Windows` .</span><span class="sxs-lookup"><span data-stu-id="08b54-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="08b54-142">Configuração</span><span class="sxs-lookup"><span data-stu-id="08b54-142">Configuration</span></span>  
 <span data-ttu-id="08b54-143">A configuração a seguir é usada para definir as propriedades do cliente.</span><span class="sxs-lookup"><span data-stu-id="08b54-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08b54-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="08b54-144">See also</span></span>

- [<span data-ttu-id="08b54-145">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="08b54-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="08b54-146">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="08b54-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
