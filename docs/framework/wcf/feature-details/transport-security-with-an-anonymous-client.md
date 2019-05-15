---
title: Segurança de transporte com um cliente anônimo – WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: aac3b2ac6cfcca137bddaefafd290e744ee991eb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637433"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="cf63c-102">Segurança de transporte com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="cf63c-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="cf63c-103">Este cenário do Windows Communication Foundation (WCF) usa a segurança de transporte (HTTPS) para garantir a confidencialidade e integridade.</span><span class="sxs-lookup"><span data-stu-id="cf63c-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="cf63c-104">O servidor deve ser autenticado com um certificado Secure Sockets Layer (SSL) e os clientes devem confiar em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="cf63c-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="cf63c-105">O cliente não está autenticado por qualquer mecanismo e é, portanto, anônimo.</span><span class="sxs-lookup"><span data-stu-id="cf63c-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="cf63c-106">Para um aplicativo de exemplo, consulte [segurança de transporte WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="cf63c-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="cf63c-107">Para obter mais informações sobre a segurança de transporte, consulte [visão geral da segurança de transporte](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf63c-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="cf63c-108">Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](working-with-certificates.md) e [como: Configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="cf63c-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Usando a segurança de transporte com um cliente anônimo](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="cf63c-110">Característica</span><span class="sxs-lookup"><span data-stu-id="cf63c-110">Characteristic</span></span>|<span data-ttu-id="cf63c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf63c-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="cf63c-112">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="cf63c-112">Security Mode</span></span>|<span data-ttu-id="cf63c-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="cf63c-113">Transport</span></span>|
|<span data-ttu-id="cf63c-114">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="cf63c-114">Interoperability</span></span>|<span data-ttu-id="cf63c-115">Com clientes e serviços Web existentes</span><span class="sxs-lookup"><span data-stu-id="cf63c-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="cf63c-116">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="cf63c-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="cf63c-117">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="cf63c-117">Authentication (Client)</span></span>|<span data-ttu-id="cf63c-118">Sim</span><span class="sxs-lookup"><span data-stu-id="cf63c-118">Yes</span></span><br /><br /> <span data-ttu-id="cf63c-119">Nível de aplicativo (não há suporte do WCF)</span><span class="sxs-lookup"><span data-stu-id="cf63c-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="cf63c-120">Integridade</span><span class="sxs-lookup"><span data-stu-id="cf63c-120">Integrity</span></span>|<span data-ttu-id="cf63c-121">Sim</span><span class="sxs-lookup"><span data-stu-id="cf63c-121">Yes</span></span>|
|<span data-ttu-id="cf63c-122">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="cf63c-122">Confidentiality</span></span>|<span data-ttu-id="cf63c-123">Sim</span><span class="sxs-lookup"><span data-stu-id="cf63c-123">Yes</span></span>|
|<span data-ttu-id="cf63c-124">Transporte</span><span class="sxs-lookup"><span data-stu-id="cf63c-124">Transport</span></span>|<span data-ttu-id="cf63c-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="cf63c-125">HTTPS</span></span>|
|<span data-ttu-id="cf63c-126">Associação</span><span class="sxs-lookup"><span data-stu-id="cf63c-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="cf63c-127">Serviço</span><span class="sxs-lookup"><span data-stu-id="cf63c-127">Service</span></span>

<span data-ttu-id="cf63c-128">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="cf63c-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cf63c-129">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="cf63c-129">Do one of the following:</span></span>

- <span data-ttu-id="cf63c-130">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="cf63c-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="cf63c-131">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cf63c-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="cf63c-132">Código</span><span class="sxs-lookup"><span data-stu-id="cf63c-132">Code</span></span>

<span data-ttu-id="cf63c-133">O código a seguir mostra como criar um ponto de extremidade usando a segurança de transporte:</span><span class="sxs-lookup"><span data-stu-id="cf63c-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="cf63c-134">Configuração</span><span class="sxs-lookup"><span data-stu-id="cf63c-134">Configuration</span></span>

<span data-ttu-id="cf63c-135">O código a seguir define o mesmo ponto de extremidade usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="cf63c-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="cf63c-136">O cliente não está autenticado por qualquer mecanismo e, portanto, é anônimo.</span><span class="sxs-lookup"><span data-stu-id="cf63c-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="cf63c-137">Cliente</span><span class="sxs-lookup"><span data-stu-id="cf63c-137">Client</span></span>

<span data-ttu-id="cf63c-138">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="cf63c-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cf63c-139">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="cf63c-139">Do one of the following:</span></span>

- <span data-ttu-id="cf63c-140">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="cf63c-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="cf63c-141">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="cf63c-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="cf63c-142">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="cf63c-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="cf63c-143">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cf63c-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="cf63c-144">Código</span><span class="sxs-lookup"><span data-stu-id="cf63c-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="cf63c-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="cf63c-145">Configuration</span></span>

<span data-ttu-id="cf63c-146">A configuração a seguir pode ser usada em vez do código para configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="cf63c-146">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cf63c-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf63c-147">See also</span></span>

- [<span data-ttu-id="cf63c-148">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="cf63c-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="cf63c-149">Segurança de transporte de WS</span><span class="sxs-lookup"><span data-stu-id="cf63c-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="cf63c-150">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="cf63c-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="cf63c-151">[Modelo de segurança do Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cf63c-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
