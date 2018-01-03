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
- csharp
- vb
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c1662e5b0f8afd4ef92d2893a11c25457dbce024
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="34c87-102">Autenticação NTLM e Kerberos</span><span class="sxs-lookup"><span data-stu-id="34c87-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="34c87-103">A autenticação padrão NTLM e a autenticação Kerberos usam as credenciais de usuário do Microsoft Windows NT associadas com o aplicativo de chamada para tentar a autenticação com o servidor.</span><span class="sxs-lookup"><span data-stu-id="34c87-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="34c87-104">Ao usar a autenticação NTLM não padrão, o aplicativo define o tipo de autenticação para NTLM e usa um objeto <xref:System.Net.NetworkCredential> para passar o nome de usuário, senha e domínio para o host, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34c87-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="34c87-105">Aplicativos que precisam se conectar a serviços da Internet usando as credenciais do usuário do aplicativo podem fazer isso com as credenciais do usuário padrão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34c87-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="34c87-106">O módulo de autenticação negotiate determina se o servidor remoto está usando a autenticação NTLM ou Kerberos e envia a resposta apropriada.</span><span class="sxs-lookup"><span data-stu-id="34c87-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34c87-107">A autenticação NTLM não funciona por meio de um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="34c87-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c87-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34c87-108">See Also</span></span>  
 [<span data-ttu-id="34c87-109">Autenticação Básica e Digest</span><span class="sxs-lookup"><span data-stu-id="34c87-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="34c87-110">Autenticação da Internet</span><span class="sxs-lookup"><span data-stu-id="34c87-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
