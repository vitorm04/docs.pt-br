---
title: Autenticação Básica e Digest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: db39bdcaf2c3a4457028e30f9458a5626aa7e795
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50190665"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="4583e-102">Autenticação Básica e Digest</span><span class="sxs-lookup"><span data-stu-id="4583e-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="4583e-103">A implementação <xref:System.Net> da autenticação básica e digest está em conformidade com o RFC2617 – Autenticação HTTP: Autenticação Básica e Digest (disponível no site da [World Wide Web Consortium](https://www.w3.org)).</span><span class="sxs-lookup"><span data-stu-id="4583e-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="4583e-104">Para usar a autenticação básica e digest, um aplicativo deve fornecer um nome de usuário e uma senha na propriedade <xref:System.Net.WebRequest.Credentials%2A> do objeto <xref:System.Net.WebRequest> usado para solicitar dados da Internet, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4583e-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  <span data-ttu-id="4583e-105">Os dados enviados com a Autenticação Básica e Digest não são criptografados e, portanto, os dados podem ser vistos por um adversário.</span><span class="sxs-lookup"><span data-stu-id="4583e-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="4583e-106">Além disso, as credenciais da Autenticação Básica (nome de usuário e senha) são enviadas de modo transparente e podem ser interceptadas.</span><span class="sxs-lookup"><span data-stu-id="4583e-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4583e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4583e-107">See Also</span></span>  
 [<span data-ttu-id="4583e-108">Autenticação Kerberos e NTLM</span><span class="sxs-lookup"><span data-stu-id="4583e-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="4583e-109">Autenticação da Internet</span><span class="sxs-lookup"><span data-stu-id="4583e-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
