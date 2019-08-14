---
title: 'Como: criar uma associação duplex federada'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972057"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="3cf3c-102">Como: criar uma associação duplex federada</span><span class="sxs-lookup"><span data-stu-id="3cf3c-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="3cf3c-103"><xref:System.ServiceModel.WSFederationHttpBinding>o só dá suporte aos contratos de troca de datagrama e solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="3cf3c-104">Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="3cf3c-105">Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança do modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="3cf3c-106">O código de exemplo mostrando todas as 3 associações está no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="3cf3c-107">Você também pode criar a associação no código.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-107">You can also create the binding in code.</span></span> <span data-ttu-id="3cf3c-108">Para obter uma descrição da pilha de elementos de associação a ser [criada, consulte Como: Crie uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="3cf3c-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="3cf3c-109">Para criar uma associação personalizada de duplex federado com HTTP</span><span class="sxs-lookup"><span data-stu-id="3cf3c-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="3cf3c-110">No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3cf3c-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3cf3c-111">Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexHttpMessageSecurityBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="3cf3c-112">Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3cf3c-113">Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3cf3c-114">Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="3cf3c-115">Seguindo o [ \<elemento > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , crie um elemento de [ \<> de oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="3cf3c-116">Seguindo o [ \<elemento oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , crie um elemento [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="3cf3c-117">Para criar uma associação personalizada de duplex federado com o modo de segurança de mensagem TCP</span><span class="sxs-lookup"><span data-stu-id="3cf3c-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="3cf3c-118">No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3cf3c-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3cf3c-119">Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexTcpMessageSecurityBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="3cf3c-120">Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3cf3c-121">Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3cf3c-122">Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="3cf3c-123">Para criar uma associação personalizada de duplex federado com o modo de segurança mista TCP</span><span class="sxs-lookup"><span data-stu-id="3cf3c-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="3cf3c-124">No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3cf3c-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="3cf3c-125">Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="3cf3c-126">Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="3cf3c-127">Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="3cf3c-128">Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="3cf3c-129">Seguindo o [ \<elemento > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , crie um elemento [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3cf3c-130">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3cf3c-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="3cf3c-131">Exemplo com 3 associações</span><span class="sxs-lookup"><span data-stu-id="3cf3c-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="3cf3c-132">Insira o código a seguir no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3cf3c-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="3cf3c-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3cf3c-133">Example</span></span>

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
