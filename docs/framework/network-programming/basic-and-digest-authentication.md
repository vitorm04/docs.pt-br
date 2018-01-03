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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ca66a65c05da3d515358c0fdb26682fa4ec1438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-and-digest-authentication"></a>Autenticação Básica e Digest
A implementação <xref:System.Net> da autenticação básica e digest está em conformidade com o RFC2617 – autenticação HTTP: autenticação básica e digest (disponível no site da World Wide Web Consortium em www.w3.org).  
  
 Para usar a autenticação básica e digest, um aplicativo deve fornecer um nome de usuário e uma senha na propriedade <xref:System.Net.WebRequest.Credentials%2A> do objeto <xref:System.Net.WebRequest> usado para solicitar dados da Internet, conforme mostrado no exemplo a seguir.  
  
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
>  Os dados enviados com a Autenticação Básica e Digest não são criptografados e, portanto, os dados podem ser vistos por um adversário. Além disso, as credenciais da Autenticação Básica (nome de usuário e senha) são enviadas de modo transparente e podem ser interceptadas.  
  
## <a name="see-also"></a>Consulte também  
 [Autenticação Kerberos e NTLM](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Autenticação da Internet](../../../docs/framework/network-programming/internet-authentication.md)
