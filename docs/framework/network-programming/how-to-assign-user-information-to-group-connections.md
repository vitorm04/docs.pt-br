---
title: "Como atribuir informações de usuário a conexões de grupo"
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
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 27cc8c14bc0c4418cd7ffbb4eb606c0b2cd7500c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="57ed5-102">Como atribuir informações de usuário a conexões de grupo</span><span class="sxs-lookup"><span data-stu-id="57ed5-102">How to: Assign User Information to Group Connections</span></span>

  
 <span data-ttu-id="57ed5-103">O exemplo a seguir demonstra como atribuir informações de usuário a conexões de grupo, supondo que o aplicativo defina as variáveis *UserName*, *SecurelyStoredPassword* e *Domain* antes que essa seção do código seja chamada e que *UserName* seja exclusivo.</span><span class="sxs-lookup"><span data-stu-id="57ed5-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="57ed5-104">Para atribuir informações de usuário a uma conexão de grupo</span><span class="sxs-lookup"><span data-stu-id="57ed5-104">To assign user information to a group connection</span></span>  
  
1.  <span data-ttu-id="57ed5-105">Crie um nome de grupo de conexão.</span><span class="sxs-lookup"><span data-stu-id="57ed5-105">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2.  <span data-ttu-id="57ed5-106">Crie uma solicitação para uma URL específica.</span><span class="sxs-lookup"><span data-stu-id="57ed5-106">Create a request for a specific URL.</span></span> <span data-ttu-id="57ed5-107">Por exemplo, o código a seguir cria uma solicitação para a URL `http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="57ed5-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3.  <span data-ttu-id="57ed5-108">Defina as credenciais e o GroupName da Conexão para a solicitação da Web e chame **GetResponse** para recuperar um objeto **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="57ed5-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4.  <span data-ttu-id="57ed5-109">Feche o fluxo de resposta depois de usar o objeto WebRespose.</span><span class="sxs-lookup"><span data-stu-id="57ed5-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="57ed5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57ed5-110">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="57ed5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57ed5-111">See Also</span></span>  
 [<span data-ttu-id="57ed5-112">Gerenciando conexões</span><span class="sxs-lookup"><span data-stu-id="57ed5-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="57ed5-113">Agrupamento de conexão</span><span class="sxs-lookup"><span data-stu-id="57ed5-113">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
