---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931512"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="c0811-102">\<> de mensagem \<de > de NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="c0811-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="c0811-103">Define as configurações de segurança da mensagem SOAP `netMsmqBinding` nesta associação.</span><span class="sxs-lookup"><span data-stu-id="c0811-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="c0811-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0811-104">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0811-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0811-105">Attributes and Elements</span></span>

<span data-ttu-id="c0811-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0811-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0811-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0811-107">Attributes</span></span>

|<span data-ttu-id="c0811-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0811-108">Attribute</span></span>|<span data-ttu-id="c0811-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0811-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c0811-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c0811-110">algorithmSuite</span></span>|<span data-ttu-id="c0811-111">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves que são usados para obter segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c0811-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="c0811-112">O valor padrão é `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="c0811-112">The default value is `Aes256`.</span></span> <span data-ttu-id="c0811-113">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="c0811-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="c0811-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="c0811-114">clientCredentialType</span></span>|<span data-ttu-id="c0811-115">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c0811-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="c0811-116">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0811-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c0811-117">None Isso permite que o serviço interaja com clientes anônimos.</span><span class="sxs-lookup"><span data-stu-id="c0811-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="c0811-118">Nem o serviço nem o cliente exigem uma credencial.</span><span class="sxs-lookup"><span data-stu-id="c0811-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="c0811-119">Windows Isso permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="c0811-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="c0811-120">Isso sempre executa a autenticação baseada em Kerberos.</span><span class="sxs-lookup"><span data-stu-id="c0811-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="c0811-121">Usu Isso permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c0811-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="c0811-122">A credencial, nesse caso, precisa ser especificada usando `clientCredentials` o comportamento **cuidado:**  O Windows Communication Foundation (WCF) não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando a senha e o uso dessas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c0811-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="c0811-123">Portanto, o WCF impõe que a troca seja protegida ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c0811-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="c0811-124">Esse modo requer que o certificado de serviço seja especificado no lado do cliente `clientCredential` usando o `serviceCertificate`comportamento e.</span><span class="sxs-lookup"><span data-stu-id="c0811-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="c0811-125">Certificate Isso permite que o serviço exija que o cliente seja autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="c0811-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="c0811-126">Nesse caso, a credencial do cliente precisa ser especificada usando `clientCredentials` o comportamento.</span><span class="sxs-lookup"><span data-stu-id="c0811-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="c0811-127">Nesse caso, a credencial de serviço precisa ser especificada usando `clientCredentials` o comportamento, especificando `serviceCertificate`o.</span><span class="sxs-lookup"><span data-stu-id="c0811-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="c0811-128">CardSpace Isso permite que o serviço exija que o cliente seja autenticado usando um CardSpace.</span><span class="sxs-lookup"><span data-stu-id="c0811-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="c0811-129">O `serviceCertificate` deve ser provisionado `clientCredential` no comportamento.</span><span class="sxs-lookup"><span data-stu-id="c0811-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="c0811-130">O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="c0811-130">The default value is `Windows`.</span></span> <span data-ttu-id="c0811-131">Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c0811-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c0811-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0811-132">Child Elements</span></span>

<span data-ttu-id="c0811-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0811-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0811-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0811-134">Parent Elements</span></span>

|<span data-ttu-id="c0811-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0811-135">Element</span></span>|<span data-ttu-id="c0811-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0811-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0811-137">\<security></span><span class="sxs-lookup"><span data-stu-id="c0811-137">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="c0811-138">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="c0811-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c0811-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0811-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="c0811-140">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="c0811-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="c0811-141">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c0811-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c0811-142">Associações</span><span class="sxs-lookup"><span data-stu-id="c0811-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c0811-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c0811-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c0811-144">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c0811-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c0811-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="c0811-145">\<binding></span></span>](../../../misc/binding.md)
