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
# <a name="ntlm-and-kerberos-authentication"></a>Autenticação NTLM e Kerberos
A autenticação padrão NTLM e a autenticação Kerberos usam as credenciais de usuário do Microsoft Windows NT associadas com o aplicativo de chamada para tentar a autenticação com o servidor. Ao usar a autenticação NTLM não padrão, o aplicativo define o tipo de autenticação para NTLM e usa um objeto <xref:System.Net.NetworkCredential> para passar o nome de usuário, senha e domínio para o host, conforme mostrado no exemplo a seguir.  
  
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
  
 Aplicativos que precisam se conectar a serviços da Internet usando as credenciais do usuário do aplicativo podem fazer isso com as credenciais do usuário padrão, conforme mostrado no exemplo a seguir.  
  
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
  
 O módulo de autenticação negotiate determina se o servidor remoto está usando a autenticação NTLM ou Kerberos e envia a resposta apropriada.  
  
> [!NOTE]
>  A autenticação NTLM não funciona por meio de um servidor proxy.  
  
## <a name="see-also"></a>Consulte também  
 [Autenticação Básica e Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Autenticação da Internet](../../../docs/framework/network-programming/internet-authentication.md)
