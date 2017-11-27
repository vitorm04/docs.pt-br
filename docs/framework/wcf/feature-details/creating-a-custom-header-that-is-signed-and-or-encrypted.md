---
title: "Criar um cabeçalho personalizado que é assinado e- ou criptografado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac43be1978a2a6e80b08e0c4bcd5e0e92043719e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="82a2f-102">Criar um cabeçalho personalizado que é assinado e- ou criptografado</span><span class="sxs-lookup"><span data-stu-id="82a2f-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="82a2f-103">Ao chamar um serviço WCF não usando um cliente WCF, às vezes, é necessário usar cabeçalhos SOAP personalizados.</span><span class="sxs-lookup"><span data-stu-id="82a2f-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="82a2f-104">Há um bug de conversão em formato canônico no WCF que impede a trabalhar com um serviço WCF não cabeçalhos personalizados que são assinados e criptografados.</span><span class="sxs-lookup"><span data-stu-id="82a2f-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="82a2f-105">O problema é causado pela concessão incorreta de namespaces XML padrão.</span><span class="sxs-lookup"><span data-stu-id="82a2f-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="82a2f-106">Isso só será um problema ao chamar serviços WCF não com cabeçalhos personalizados que são assinados e/ou criptografados.</span><span class="sxs-lookup"><span data-stu-id="82a2f-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="82a2f-107">Quando o serviço recebe a mensagem que contém o cabeçalho personalizado assinado e/ou criptografado não é possível verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="82a2f-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="82a2f-108">Essa solução alternativa evita o erro de conversão em formato canônico, permite a interoperabilidade com serviços WCF não, mas não impede que a interoperabilidade com serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="82a2f-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="82a2f-109">Definindo o cabeçalho personalizado</span><span class="sxs-lookup"><span data-stu-id="82a2f-109">Defining the custom header</span></span>  
 <span data-ttu-id="82a2f-110">Cabeçalhos personalizados são definidos com a definição de um contrato de mensagem e marcar os membros que deve ser enviado como cabeçalhos com um <xref:System.ServiceModel.MessageHeaderAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="82a2f-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="82a2f-111">Para solucionar o erro de conversão em formato canônico, você deve garantir que o serializador XML declara o namespace do cabeçalho personalizado com um prefixo, em vez de uma declaração de namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="82a2f-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="82a2f-112">O código a seguir mostra como definir o tipo de dados que será usado como um cabeçalho de mensagem com a declaração de namespace correto.</span><span class="sxs-lookup"><span data-stu-id="82a2f-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="82a2f-113">Esse código declara um novo tipo denominado `msgHeaderElement` que será serializado com o serializador XML.</span><span class="sxs-lookup"><span data-stu-id="82a2f-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="82a2f-114">Quando uma instância desse tipo é serializada, ela definirá um namespace com um prefixo 'h', portanto contornar o erro de conversão em formato canônico.</span><span class="sxs-lookup"><span data-stu-id="82a2f-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="82a2f-115">O contrato de mensagem, em seguida, define uma instância de `msgHeaderElement` e marcá-la com o <xref:System.ServiceModel.MessageHeaderAttribute> atributo conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="82a2f-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="82a2f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a2f-116">See Also</span></span>  
 [<span data-ttu-id="82a2f-117">Contrato de mensagem padrão</span><span class="sxs-lookup"><span data-stu-id="82a2f-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [<span data-ttu-id="82a2f-118">Contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="82a2f-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [<span data-ttu-id="82a2f-119">Usando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="82a2f-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
