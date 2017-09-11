---
title: "Autenticação Básica e Digest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
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
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 369a473b2e9172abe10d263bb066b253500f9502
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="df03f-102">Autenticação Básica e Digest</span><span class="sxs-lookup"><span data-stu-id="df03f-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="df03f-103">A implementação <xref:System.Net> da autenticação básica e digest está em conformidade com o RFC2617 – autenticação HTTP: autenticação básica e digest (disponível no site da World Wide Web Consortium em www.w3.org).</span><span class="sxs-lookup"><span data-stu-id="df03f-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the World Wide Web Consortium's Web site at www.w3.org).</span></span>  
  
 <span data-ttu-id="df03f-104">Para usar a autenticação básica e digest, um aplicativo deve fornecer um nome de usuário e uma senha na propriedade <xref:System.Net.WebRequest.Credentials%2A> do objeto <xref:System.Net.WebRequest> usado para solicitar dados da Internet, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="df03f-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="df03f-105">Os dados enviados com a Autenticação Básica e Digest não são criptografados e, portanto, os dados podem ser vistos por um adversário.</span><span class="sxs-lookup"><span data-stu-id="df03f-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="df03f-106">Além disso, as credenciais da Autenticação Básica (nome de usuário e senha) são enviadas de modo transparente e podem ser interceptadas.</span><span class="sxs-lookup"><span data-stu-id="df03f-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df03f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df03f-107">See Also</span></span>  
 <span data-ttu-id="df03f-108">[Autenticação NTLM e Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="df03f-108">[NTLM and Kerberos Authentication](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md) </span></span>  
 [<span data-ttu-id="df03f-109">Autenticação da Internet</span><span class="sxs-lookup"><span data-stu-id="df03f-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)

