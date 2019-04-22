---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890560"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="17c17-102">\<message> of \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="17c17-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="17c17-103">Define as configurações de segurança de mensagem SOAP sobre isso `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="17c17-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="17c17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17c17-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="17c17-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17c17-105">Attributes and Elements</span></span>

<span data-ttu-id="17c17-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17c17-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="17c17-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="17c17-107">Attributes</span></span>

|<span data-ttu-id="17c17-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="17c17-108">Attribute</span></span>|<span data-ttu-id="17c17-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="17c17-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="17c17-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="17c17-110">algorithmSuite</span></span>|<span data-ttu-id="17c17-111">Define a mensagem de algoritmos de criptografia e encapsulamento de chave que são usados para fins de segurança baseada em mensagens para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="17c17-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="17c17-112">O valor padrão é `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="17c17-112">The default value is `Aes256`.</span></span> <span data-ttu-id="17c17-113">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="17c17-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="17c17-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="17c17-114">clientCredentialType</span></span>|<span data-ttu-id="17c17-115">Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente para mensagens enviadas por meio do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="17c17-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="17c17-116">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="17c17-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="17c17-117">-None: Isso permite que o serviço interaja com clientes anônimos.</span><span class="sxs-lookup"><span data-stu-id="17c17-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="17c17-118">Nem o serviço nem o cliente requer uma credencial.</span><span class="sxs-lookup"><span data-stu-id="17c17-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="17c17-119">-   Windows: Isso permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="17c17-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="17c17-120">Isso sempre executa a autenticação Kerberos.</span><span class="sxs-lookup"><span data-stu-id="17c17-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="17c17-121">-Nome de usuário: Isso permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="17c17-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="17c17-122">A credencial nesse caso, deve ser especificado usando o `clientCredentials` comportamento **cuidado:**  Windows Communication Foundation (WCF) não oferece suporte para enviar um resumo de senha ou derivação de chaves usando a senha e essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="17c17-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="17c17-123">Portanto, o WCF impõe que o exchange esteja protegido ao usar as credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="17c17-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="17c17-124">Esse modo exige que o certificado de serviço seja especificado no lado cliente usando `clientCredential` comportamento e `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="17c17-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="17c17-125">-Certificado: Isso permite que o serviço exigir que o cliente seja autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="17c17-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="17c17-126">A credencial do cliente nesse caso, deve ser especificado usando o `clientCredentials` comportamento.</span><span class="sxs-lookup"><span data-stu-id="17c17-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="17c17-127">A credencial de serviço neste caso deve ser especificado usando o `clientCredentials` comportamento especificando o `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="17c17-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="17c17-128">-CardSpace: Isso permite que o serviço exigir que o cliente seja autenticado usando um CardSpace.</span><span class="sxs-lookup"><span data-stu-id="17c17-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="17c17-129">O `serviceCertificate` devem ser provisionados no `clientCredential` comportamento.</span><span class="sxs-lookup"><span data-stu-id="17c17-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="17c17-130">O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="17c17-130">The default value is `Windows`.</span></span> <span data-ttu-id="17c17-131">Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="17c17-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="17c17-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17c17-132">Child Elements</span></span>

<span data-ttu-id="17c17-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="17c17-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17c17-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17c17-134">Parent Elements</span></span>

|<span data-ttu-id="17c17-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="17c17-135">Element</span></span>|<span data-ttu-id="17c17-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="17c17-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17c17-137">\<security></span><span class="sxs-lookup"><span data-stu-id="17c17-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="17c17-138">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="17c17-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="17c17-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17c17-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="17c17-140">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="17c17-140">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="17c17-141">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="17c17-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="17c17-142">Associações</span><span class="sxs-lookup"><span data-stu-id="17c17-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="17c17-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="17c17-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="17c17-144">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="17c17-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="17c17-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="17c17-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
