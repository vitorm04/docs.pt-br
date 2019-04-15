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
ms.openlocfilehash: 4f70d2aef3bb064a3df9db9c87671040776332a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089816"
---
# <a name="basic-and-digest-authentication"></a>Autenticação Básica e Digest
A implementação <xref:System.Net> da autenticação Básica e Digest está em conformidade com o RFC2617 – Autenticação HTTP: Autenticação Básica e Digest (disponível no site do [World Wide Web Consortium](https://www.w3.org)).  
  
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

- [Autenticação NTLM e Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [Autenticação da Internet](../../../docs/framework/network-programming/internet-authentication.md)
