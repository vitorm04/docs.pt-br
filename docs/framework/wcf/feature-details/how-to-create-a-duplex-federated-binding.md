---
title: Como criar uma associação duplex federada
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141724"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="c6e5b-102">Como criar uma associação duplex federada</span><span class="sxs-lookup"><span data-stu-id="c6e5b-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="c6e5b-103"><xref:System.ServiceModel.WSFederationHttpBinding> só dá suporte aos contratos de troca de datagrama e solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="c6e5b-104">Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="c6e5b-105">Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança do modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="c6e5b-106">O código de exemplo mostrando todas as 3 associações está no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="c6e5b-107">Você também pode criar a associação no código.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-107">You can also create the binding in code.</span></span> <span data-ttu-id="c6e5b-108">Para obter uma descrição da pilha de elementos de associação a ser criada, consulte [como: criar uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="c6e5b-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="c6e5b-109">Para criar uma associação personalizada de duplex federado com HTTP</span><span class="sxs-lookup"><span data-stu-id="c6e5b-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="c6e5b-110">No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e5b-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="c6e5b-111">Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="c6e5b-112">Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="c6e5b-113">Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="c6e5b-114">Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="c6e5b-115">Seguindo o elemento [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , crie um elemento [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="c6e5b-116">Seguindo o elemento [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , crie um elemento de [> de\<httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="c6e5b-117">Para criar uma associação personalizada de duplex federado com o modo de segurança de mensagem TCP</span><span class="sxs-lookup"><span data-stu-id="c6e5b-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="c6e5b-118">No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e5b-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="c6e5b-119">Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="c6e5b-120">Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="c6e5b-121">Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="c6e5b-122">Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="c6e5b-123">Para criar uma associação personalizada de duplex federado com o modo de segurança mista TCP</span><span class="sxs-lookup"><span data-stu-id="c6e5b-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="c6e5b-124">No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e5b-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="c6e5b-125">Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="c6e5b-126">Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="c6e5b-127">Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="c6e5b-128">Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vazio.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="c6e5b-129">Seguindo o elemento [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , crie um elemento de [> tcpTransport vazio\<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e5b-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c6e5b-130">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c6e5b-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="c6e5b-131">Exemplo com 3 associações</span><span class="sxs-lookup"><span data-stu-id="c6e5b-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="c6e5b-132">Insira o código a seguir no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c6e5b-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="c6e5b-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6e5b-133">Example</span></span>

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
