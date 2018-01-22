---
title: '&lt;mensagem&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a7fdb8c6df84a76450aabaa983275f563d342fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="f9a32-102">&lt;mensagem&gt; de &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f9a32-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="f9a32-103">Define as configurações de segurança de mensagem SOAP neste `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="f9a32-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="f9a32-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9a32-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9a32-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f9a32-105">\<bindings></span></span>  
<span data-ttu-id="f9a32-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="f9a32-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="f9a32-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f9a32-107">\<binding></span></span>  
<span data-ttu-id="f9a32-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f9a32-108">\<security></span></span>  
<span data-ttu-id="f9a32-109">\<message></span><span class="sxs-lookup"><span data-stu-id="f9a32-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a32-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9a32-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9a32-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f9a32-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f9a32-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f9a32-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9a32-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9a32-113">Attributes</span></span>  
  
|<span data-ttu-id="f9a32-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f9a32-114">Attribute</span></span>|<span data-ttu-id="f9a32-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9a32-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9a32-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="f9a32-116">algorithmSuite</span></span>|<span data-ttu-id="f9a32-117">Define a mensagem de algoritmos de criptografia e a disposição de chave que são usados para atingir a segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9a32-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="f9a32-118">O valor padrão é `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="f9a32-118">The default value is `Aes256`.</span></span> <span data-ttu-id="f9a32-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="f9a32-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="f9a32-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f9a32-120">clientCredentialType</span></span>|<span data-ttu-id="f9a32-121">Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente para mensagens enviadas por meio do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9a32-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="f9a32-122">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f9a32-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f9a32-123">-Nenhum: Isso permite que o serviço interaja com clientes anônimos.</span><span class="sxs-lookup"><span data-stu-id="f9a32-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="f9a32-124">O serviço, nem o cliente requer uma credencial.</span><span class="sxs-lookup"><span data-stu-id="f9a32-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="f9a32-125">-Windows: Isso permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="f9a32-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="f9a32-126">Isso sempre realiza a autenticação Kerberos.</span><span class="sxs-lookup"><span data-stu-id="f9a32-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="f9a32-127">-Nome de usuário: Isso permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="f9a32-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="f9a32-128">A credencial nesse caso deve ser especificado usando o `clientCredentials` comportamento **cuidado:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] não oferece suporte para enviar uma senha digest ou derivação de chaves usando a senha e essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f9a32-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="f9a32-129">Portanto, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] impõe que o exchange é protegido ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="f9a32-129">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="f9a32-130">Esse modo exige que o certificado de serviço seja especificada no lado cliente usando `clientCredential` comportamento e `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="f9a32-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="f9a32-131">-O certificado: Isso permite que o serviço exigir que o cliente seja autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="f9a32-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="f9a32-132">A credencial do cliente nesse caso deve ser especificado usando o `clientCredentials` comportamento.</span><span class="sxs-lookup"><span data-stu-id="f9a32-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="f9a32-133">A credencial de serviço nesse caso deve ser especificado usando o `clientCredentials` comportamento especificando o `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="f9a32-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="f9a32-134">-CardSpace: Isso permite que o serviço exigir que o cliente seja autenticado usando um CardSpace.</span><span class="sxs-lookup"><span data-stu-id="f9a32-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="f9a32-135">O `serviceCertiifcate` devem ser provisionados no `clientCredential` comportamento.</span><span class="sxs-lookup"><span data-stu-id="f9a32-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="f9a32-136">O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="f9a32-136">The default value is `Windows`.</span></span> <span data-ttu-id="f9a32-137">Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f9a32-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9a32-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9a32-138">Child Elements</span></span>  
 <span data-ttu-id="f9a32-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f9a32-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9a32-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9a32-140">Parent Elements</span></span>  
  
|<span data-ttu-id="f9a32-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9a32-141">Element</span></span>|<span data-ttu-id="f9a32-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9a32-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9a32-143">\<security></span><span class="sxs-lookup"><span data-stu-id="f9a32-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="f9a32-144">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="f9a32-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9a32-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9a32-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="f9a32-146">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="f9a32-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="f9a32-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f9a32-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f9a32-148">Associações</span><span class="sxs-lookup"><span data-stu-id="f9a32-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f9a32-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f9a32-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f9a32-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f9a32-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f9a32-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="f9a32-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
