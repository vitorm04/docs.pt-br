---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736752"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="25adc-102">\<> de mensagens de \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="25adc-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="25adc-103">Define as configurações de segurança de mensagem SOAP nesta `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="25adc-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="25adc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="25adc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25adc-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="25adc-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="25adc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="25adc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="25adc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="25adc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="25adc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="25adc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="25adc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="25adc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="25adc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**message >**</span><span class="sxs-lookup"><span data-stu-id="25adc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="25adc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25adc-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="25adc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="25adc-112">Attributes and Elements</span></span>

<span data-ttu-id="25adc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="25adc-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="25adc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="25adc-114">Attributes</span></span>

|<span data-ttu-id="25adc-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="25adc-115">Attribute</span></span>|<span data-ttu-id="25adc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="25adc-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="25adc-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="25adc-117">algorithmSuite</span></span>|<span data-ttu-id="25adc-118">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves que são usados para obter segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="25adc-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="25adc-119">O valor padrão é `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="25adc-119">The default value is `Aes256`.</span></span> <span data-ttu-id="25adc-120">Este atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="25adc-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="25adc-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="25adc-121">clientCredentialType</span></span>|<span data-ttu-id="25adc-122">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="25adc-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="25adc-123">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="25adc-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25adc-124">-Nenhum: isso permite que o serviço interaja com clientes anônimos.</span><span class="sxs-lookup"><span data-stu-id="25adc-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="25adc-125">Nem o serviço nem o cliente exigem uma credencial.</span><span class="sxs-lookup"><span data-stu-id="25adc-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="25adc-126">-Windows: isso permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="25adc-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="25adc-127">Isso sempre executa a autenticação baseada em Kerberos.</span><span class="sxs-lookup"><span data-stu-id="25adc-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="25adc-128">-UserName: isso permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="25adc-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="25adc-129">A credencial, nesse caso, precisa ser especificada usando o comportamento de `clientCredentials` **cuidado:** o Windows Communication Foundation (WCF) não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando a senha e o uso dessas chaves para segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25adc-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="25adc-130">Portanto, o WCF impõe que a troca seja protegida ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="25adc-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="25adc-131">Esse modo requer que o certificado de serviço seja especificado no lado do cliente usando o comportamento `clientCredential` e `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="25adc-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="25adc-132">-Certificate: isso permite que o serviço exija que o cliente seja autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="25adc-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="25adc-133">Nesse caso, a credencial do cliente precisa ser especificada usando o comportamento de `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="25adc-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="25adc-134">Nesse caso, a credencial de serviço precisa ser especificada usando o comportamento de `clientCredentials` especificando o `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="25adc-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="25adc-135">-CardSpace: isso permite que o serviço exija que o cliente seja autenticado usando um CardSpace.</span><span class="sxs-lookup"><span data-stu-id="25adc-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="25adc-136">O `serviceCertificate` deve ser provisionado no comportamento de `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="25adc-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="25adc-137">O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="25adc-137">The default value is `Windows`.</span></span> <span data-ttu-id="25adc-138">Este atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="25adc-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="25adc-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="25adc-139">Child Elements</span></span>

<span data-ttu-id="25adc-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="25adc-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25adc-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="25adc-141">Parent Elements</span></span>

|<span data-ttu-id="25adc-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="25adc-142">Element</span></span>|<span data-ttu-id="25adc-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="25adc-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25adc-144">\<Security ></span><span class="sxs-lookup"><span data-stu-id="25adc-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="25adc-145">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="25adc-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="25adc-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25adc-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="25adc-147">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="25adc-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="25adc-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="25adc-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="25adc-149">Associações</span><span class="sxs-lookup"><span data-stu-id="25adc-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25adc-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="25adc-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="25adc-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="25adc-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="25adc-152">\<binding ></span><span class="sxs-lookup"><span data-stu-id="25adc-152">\<binding></span></span>](bindings.md)
