---
title: "Segurança de mensagem com um cliente do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f2a9f2f44f5dfd44f00ae580423b1d2781ae5bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="dfd34-102">Segurança de mensagem com um cliente do Windows</span><span class="sxs-lookup"><span data-stu-id="dfd34-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="dfd34-103">Este cenário mostra um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e servidor protegido pelo modo de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="dfd34-103">This scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and server secured by message security mode.</span></span> <span data-ttu-id="dfd34-104">O cliente e o serviço são autenticados usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd34-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="dfd34-105">![Segurança com um cliente do Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="dfd34-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="dfd34-106">Característica</span><span class="sxs-lookup"><span data-stu-id="dfd34-106">Characteristic</span></span>|<span data-ttu-id="dfd34-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfd34-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="dfd34-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="dfd34-108">Security Mode</span></span>|<span data-ttu-id="dfd34-109">Mensagem</span><span class="sxs-lookup"><span data-stu-id="dfd34-109">Message</span></span>|  
|<span data-ttu-id="dfd34-110">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="dfd34-110">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfd34-111">Somente</span><span class="sxs-lookup"><span data-stu-id="dfd34-111"> Only</span></span>|  
|<span data-ttu-id="dfd34-112">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="dfd34-112">Authentication (Server)</span></span>|<span data-ttu-id="dfd34-113">Autenticação mútua do servidor e cliente</span><span class="sxs-lookup"><span data-stu-id="dfd34-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="dfd34-114">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="dfd34-114">Authentication (Client)</span></span>|<span data-ttu-id="dfd34-115">Autenticação mútua do servidor e cliente</span><span class="sxs-lookup"><span data-stu-id="dfd34-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="dfd34-116">Integridade</span><span class="sxs-lookup"><span data-stu-id="dfd34-116">Integrity</span></span>|<span data-ttu-id="dfd34-117">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="dfd34-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="dfd34-118">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="dfd34-118">Confidentiality</span></span>|<span data-ttu-id="dfd34-119">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="dfd34-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="dfd34-120">Transporte</span><span class="sxs-lookup"><span data-stu-id="dfd34-120">Transport</span></span>|<span data-ttu-id="dfd34-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="dfd34-121">NET.TCP</span></span>|  
|<span data-ttu-id="dfd34-122">Associação</span><span class="sxs-lookup"><span data-stu-id="dfd34-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="dfd34-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="dfd34-123">Service</span></span>  
 <span data-ttu-id="dfd34-124">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="dfd34-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="dfd34-125">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="dfd34-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="dfd34-126">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="dfd34-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="dfd34-127">Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dfd34-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dfd34-128">Código</span><span class="sxs-lookup"><span data-stu-id="dfd34-128">Code</span></span>  
 <span data-ttu-id="dfd34-129">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem para estabelecer um contexto de seguro com um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="dfd34-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="dfd34-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="dfd34-130">Configuration</span></span>  
 <span data-ttu-id="dfd34-131">A configuração a seguir pode ser usada em vez do código para configurar o serviço:</span><span class="sxs-lookup"><span data-stu-id="dfd34-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="dfd34-132">Cliente</span><span class="sxs-lookup"><span data-stu-id="dfd34-132">Client</span></span>  
 <span data-ttu-id="dfd34-133">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="dfd34-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="dfd34-134">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="dfd34-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="dfd34-135">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="dfd34-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="dfd34-136">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dfd34-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="dfd34-137">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="dfd34-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="dfd34-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="dfd34-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="dfd34-139">Código</span><span class="sxs-lookup"><span data-stu-id="dfd34-139">Code</span></span>  
 <span data-ttu-id="dfd34-140">O código a seguir cria um cliente.</span><span class="sxs-lookup"><span data-stu-id="dfd34-140">The following code creates a client.</span></span> <span data-ttu-id="dfd34-141">A associação é a segurança de modo de mensagem e o tipo de credencial de cliente é definido como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="dfd34-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="dfd34-142">Configuração</span><span class="sxs-lookup"><span data-stu-id="dfd34-142">Configuration</span></span>  
 <span data-ttu-id="dfd34-143">A configuração a seguir é usada para definir propriedades de cliente.</span><span class="sxs-lookup"><span data-stu-id="dfd34-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfd34-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfd34-144">See Also</span></span>  
 [<span data-ttu-id="dfd34-145">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="dfd34-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="dfd34-146">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="dfd34-146">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
