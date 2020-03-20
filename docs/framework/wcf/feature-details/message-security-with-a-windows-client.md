---
title: Segurança de mensagem com um cliente do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: bcfeb5f863b1dd6cf9171a7fc53c8984ea68ecb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184622"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="9a80f-102">Segurança de mensagem com um cliente do Windows</span><span class="sxs-lookup"><span data-stu-id="9a80f-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="9a80f-103">Este cenário mostra um cliente e servidor da Windows Communication Foundation (WCF) protegido pelo modo de segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9a80f-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="9a80f-104">O cliente e o serviço são autenticados usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="9a80f-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="9a80f-105">![Segurança de mensagens com um cliente Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="9a80f-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="9a80f-106">Característica</span><span class="sxs-lookup"><span data-stu-id="9a80f-106">Characteristic</span></span>|<span data-ttu-id="9a80f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a80f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9a80f-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="9a80f-108">Security Mode</span></span>|<span data-ttu-id="9a80f-109">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9a80f-109">Message</span></span>|  
|<span data-ttu-id="9a80f-110">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9a80f-110">Interoperability</span></span>|<span data-ttu-id="9a80f-111">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="9a80f-111">WCF Only</span></span>|  
|<span data-ttu-id="9a80f-112">Autenticação (Servidor)</span><span class="sxs-lookup"><span data-stu-id="9a80f-112">Authentication (Server)</span></span>|<span data-ttu-id="9a80f-113">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="9a80f-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="9a80f-114">Autenticação (Cliente)</span><span class="sxs-lookup"><span data-stu-id="9a80f-114">Authentication (Client)</span></span>|<span data-ttu-id="9a80f-115">Autenticação mútua do servidor e do cliente</span><span class="sxs-lookup"><span data-stu-id="9a80f-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="9a80f-116">Integridade</span><span class="sxs-lookup"><span data-stu-id="9a80f-116">Integrity</span></span>|<span data-ttu-id="9a80f-117">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="9a80f-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="9a80f-118">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="9a80f-118">Confidentiality</span></span>|<span data-ttu-id="9a80f-119">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="9a80f-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="9a80f-120">Transporte</span><span class="sxs-lookup"><span data-stu-id="9a80f-120">Transport</span></span>|<span data-ttu-id="9a80f-121">Net. Tcp</span><span class="sxs-lookup"><span data-stu-id="9a80f-121">NET.TCP</span></span>|  
|<span data-ttu-id="9a80f-122">Associação</span><span class="sxs-lookup"><span data-stu-id="9a80f-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="9a80f-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="9a80f-123">Service</span></span>  
 <span data-ttu-id="9a80f-124">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="9a80f-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9a80f-125">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="9a80f-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="9a80f-126">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="9a80f-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="9a80f-127">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.</span><span class="sxs-lookup"><span data-stu-id="9a80f-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9a80f-128">Código</span><span class="sxs-lookup"><span data-stu-id="9a80f-128">Code</span></span>  
 <span data-ttu-id="9a80f-129">O código a seguir mostra como criar um ponto final de serviço que usa a segurança da mensagem para estabelecer um contexto seguro com uma máquina Windows.</span><span class="sxs-lookup"><span data-stu-id="9a80f-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="9a80f-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="9a80f-130">Configuration</span></span>  
 <span data-ttu-id="9a80f-131">A configuração a seguir pode ser usada em vez do código para configurar o serviço:</span><span class="sxs-lookup"><span data-stu-id="9a80f-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="9a80f-132">Cliente</span><span class="sxs-lookup"><span data-stu-id="9a80f-132">Client</span></span>  
 <span data-ttu-id="9a80f-133">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="9a80f-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="9a80f-134">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="9a80f-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="9a80f-135">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="9a80f-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="9a80f-136">Crie um cliente que não defina nenhum endereço de ponto final.</span><span class="sxs-lookup"><span data-stu-id="9a80f-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="9a80f-137">Em vez disso, use o construtor cliente que toma o nome da configuração como argumento.</span><span class="sxs-lookup"><span data-stu-id="9a80f-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="9a80f-138">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="9a80f-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="9a80f-139">Código</span><span class="sxs-lookup"><span data-stu-id="9a80f-139">Code</span></span>  
 <span data-ttu-id="9a80f-140">O código a seguir cria um cliente.</span><span class="sxs-lookup"><span data-stu-id="9a80f-140">The following code creates a client.</span></span> <span data-ttu-id="9a80f-141">A vinculação é para a segurança do modo mensagem e o tipo de credencial do cliente está definido como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="9a80f-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="9a80f-142">Configuração</span><span class="sxs-lookup"><span data-stu-id="9a80f-142">Configuration</span></span>  
 <span data-ttu-id="9a80f-143">A configuração a seguir é usada para definir as propriedades do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a80f-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a80f-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a80f-144">See also</span></span>

- [<span data-ttu-id="9a80f-145">Visão geral da segurança</span><span class="sxs-lookup"><span data-stu-id="9a80f-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="9a80f-146">[Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9a80f-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
