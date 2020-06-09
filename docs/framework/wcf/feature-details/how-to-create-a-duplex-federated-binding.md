---
title: Como criar uma associação duplex federada
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598964"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="5a732-102">Como criar uma associação duplex federada</span><span class="sxs-lookup"><span data-stu-id="5a732-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="5a732-103"><xref:System.ServiceModel.WSFederationHttpBinding>o só dá suporte aos contratos de troca de datagrama e solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="5a732-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="5a732-104">Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5a732-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="5a732-105">Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança do modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="5a732-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="5a732-106">O código de exemplo mostrando todas as 3 associações está no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5a732-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="5a732-107">Você também pode criar a associação no código.</span><span class="sxs-lookup"><span data-stu-id="5a732-107">You can also create the binding in code.</span></span> <span data-ttu-id="5a732-108">Para obter uma descrição da pilha de elementos de associação a ser criada, consulte [como: criar uma associação personalizada usando o SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="5a732-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="5a732-109">Para criar uma associação personalizada de duplex federado com HTTP</span><span class="sxs-lookup"><span data-stu-id="5a732-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="5a732-110">No [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5a732-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="5a732-111">Dentro do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento, crie um [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento com o `name` atributo definido como `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="5a732-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="5a732-112">Dentro do [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento, crie um [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="5a732-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="5a732-113">Dentro do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="5a732-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="5a732-114">Seguindo o [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="5a732-115">Seguindo o [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elemento, crie um [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="5a732-116">Seguindo o [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elemento, crie um [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="5a732-117">Para criar uma associação personalizada de duplex federado com o modo de segurança de mensagem TCP</span><span class="sxs-lookup"><span data-stu-id="5a732-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="5a732-118">No [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5a732-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="5a732-119">Dentro do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento, crie um [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento com o `name` atributo definido como `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="5a732-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="5a732-120">Dentro do [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento, crie um [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="5a732-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="5a732-121">Dentro do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="5a732-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="5a732-122">Seguindo o [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="5a732-123">Para criar uma associação personalizada de duplex federado com o modo de segurança mista TCP</span><span class="sxs-lookup"><span data-stu-id="5a732-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="5a732-124">No [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5a732-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="5a732-125">Dentro do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elemento, crie um [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento com o `name` atributo definido como `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="5a732-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="5a732-126">Dentro do [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento, crie um [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="5a732-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="5a732-127">Dentro do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="5a732-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="5a732-128">Seguindo o [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, crie um [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="5a732-129">Seguindo o [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento, crie um [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="5a732-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a732-130">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5a732-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="5a732-131">Exemplo com 3 associações</span><span class="sxs-lookup"><span data-stu-id="5a732-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="5a732-132">Insira o código a seguir no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5a732-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="5a732-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a732-133">Example</span></span>

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
