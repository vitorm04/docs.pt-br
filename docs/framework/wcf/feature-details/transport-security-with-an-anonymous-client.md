---
title: Segurança de transporte com um cliente anônimo
description: Examine este cenário WCF, que usa a segurança de transporte para autenticar um servidor usando um certificado que o cliente confia. O cliente não está autenticado.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 5e8bcab4cdd8f27e9ea27e66fe4c848ccd35e99c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556805"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="65554-104">Segurança de transporte com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="65554-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="65554-105">Este cenário de Windows Communication Foundation (WCF) usa a segurança de transporte (HTTPS) para garantir a confidencialidade e a integridade.</span><span class="sxs-lookup"><span data-stu-id="65554-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="65554-106">O servidor deve ser autenticado com um certificado protocolo SSL (SSL) e os clientes devem confiar no certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="65554-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="65554-107">O cliente não é autenticado por nenhum mecanismo e, portanto, é anônimo.</span><span class="sxs-lookup"><span data-stu-id="65554-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="65554-108">Para um aplicativo de exemplo, consulte [segurança de transporte do WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="65554-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="65554-109">Para obter mais informações sobre segurança de transporte, consulte [visão geral de segurança de transporte](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65554-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="65554-110">Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](working-with-certificates.md) e [como configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="65554-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Usando a segurança de transporte com um cliente anônimo](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="65554-112">Característica</span><span class="sxs-lookup"><span data-stu-id="65554-112">Characteristic</span></span>|<span data-ttu-id="65554-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="65554-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="65554-114">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="65554-114">Security Mode</span></span>|<span data-ttu-id="65554-115">Transport</span><span class="sxs-lookup"><span data-stu-id="65554-115">Transport</span></span>|
|<span data-ttu-id="65554-116">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="65554-116">Interoperability</span></span>|<span data-ttu-id="65554-117">Com os serviços Web e clientes existentes</span><span class="sxs-lookup"><span data-stu-id="65554-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="65554-118">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="65554-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="65554-119">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="65554-119">Authentication (Client)</span></span>|<span data-ttu-id="65554-120">Yes</span><span class="sxs-lookup"><span data-stu-id="65554-120">Yes</span></span><br /><br /> <span data-ttu-id="65554-121">Nível do aplicativo (sem suporte do WCF)</span><span class="sxs-lookup"><span data-stu-id="65554-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="65554-122">Integridade</span><span class="sxs-lookup"><span data-stu-id="65554-122">Integrity</span></span>|<span data-ttu-id="65554-123">Yes</span><span class="sxs-lookup"><span data-stu-id="65554-123">Yes</span></span>|
|<span data-ttu-id="65554-124">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="65554-124">Confidentiality</span></span>|<span data-ttu-id="65554-125">Yes</span><span class="sxs-lookup"><span data-stu-id="65554-125">Yes</span></span>|
|<span data-ttu-id="65554-126">Transport</span><span class="sxs-lookup"><span data-stu-id="65554-126">Transport</span></span>|<span data-ttu-id="65554-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="65554-127">HTTPS</span></span>|
|<span data-ttu-id="65554-128">Associação</span><span class="sxs-lookup"><span data-stu-id="65554-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="65554-129">Serviço</span><span class="sxs-lookup"><span data-stu-id="65554-129">Service</span></span>

<span data-ttu-id="65554-130">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="65554-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65554-131">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="65554-131">Do one of the following:</span></span>

- <span data-ttu-id="65554-132">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="65554-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="65554-133">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="65554-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="65554-134">Código</span><span class="sxs-lookup"><span data-stu-id="65554-134">Code</span></span>

<span data-ttu-id="65554-135">O código a seguir mostra como criar um ponto de extremidade usando a segurança de transporte:</span><span class="sxs-lookup"><span data-stu-id="65554-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="65554-136">Configuração</span><span class="sxs-lookup"><span data-stu-id="65554-136">Configuration</span></span>

<span data-ttu-id="65554-137">O código a seguir configura o mesmo ponto de extremidade usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="65554-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="65554-138">O cliente não é autenticado por nenhum mecanismo e, portanto, é anônimo.</span><span class="sxs-lookup"><span data-stu-id="65554-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="65554-139">Cliente</span><span class="sxs-lookup"><span data-stu-id="65554-139">Client</span></span>

<span data-ttu-id="65554-140">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="65554-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65554-141">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="65554-141">Do one of the following:</span></span>

- <span data-ttu-id="65554-142">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="65554-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="65554-143">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="65554-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="65554-144">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="65554-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="65554-145">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="65554-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="65554-146">Código</span><span class="sxs-lookup"><span data-stu-id="65554-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="65554-147">Configuração</span><span class="sxs-lookup"><span data-stu-id="65554-147">Configuration</span></span>

<span data-ttu-id="65554-148">A configuração a seguir pode ser usada em vez do código para configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="65554-148">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="65554-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="65554-149">See also</span></span>

- [<span data-ttu-id="65554-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="65554-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="65554-151">Segurança de transporte WS</span><span class="sxs-lookup"><span data-stu-id="65554-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="65554-152">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="65554-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="65554-153">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="65554-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
