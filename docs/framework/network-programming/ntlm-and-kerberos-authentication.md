---
title: "Autenticação NTLM e Kerberos"
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
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8cb52a70aa34e1011f12a77ea32ec5077f92c127
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="1853a-102">Autenticação NTLM e Kerberos</span><span class="sxs-lookup"><span data-stu-id="1853a-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="1853a-103">A autenticação padrão NTLM e a autenticação Kerberos usam as credenciais de usuário do Microsoft Windows NT associadas com o aplicativo de chamada para tentar a autenticação com o servidor.</span><span class="sxs-lookup"><span data-stu-id="1853a-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="1853a-104">Ao usar a autenticação NTLM não padrão, o aplicativo define o tipo de autenticação para NTLM e usa um objeto <xref:System.Net.NetworkCredential> para passar o nome de usuário, senha e domínio para o host, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1853a-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="1853a-105">Aplicativos que precisam se conectar a serviços da Internet usando as credenciais do usuário do aplicativo podem fazer isso com as credenciais do usuário padrão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1853a-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="1853a-106">O módulo de autenticação negotiate determina se o servidor remoto está usando a autenticação NTLM ou Kerberos e envia a resposta apropriada.</span><span class="sxs-lookup"><span data-stu-id="1853a-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1853a-107">A autenticação NTLM não funciona por meio de um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="1853a-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1853a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1853a-108">See Also</span></span>  
 <span data-ttu-id="1853a-109">[Autenticação Básica e Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="1853a-109">[Basic and Digest Authentication](../../../docs/framework/network-programming/basic-and-digest-authentication.md) </span></span>  
 [<span data-ttu-id="1853a-110">Autenticação da Internet</span><span class="sxs-lookup"><span data-stu-id="1853a-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)

