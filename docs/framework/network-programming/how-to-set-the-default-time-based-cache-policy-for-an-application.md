---
title: Como definir uma política de cache baseada em tempo padrão para um aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: cdb93f802d313c0812bb50236ff5962c44251b4e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182901"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="f5fc1-102">Como definir uma política de cache baseada em tempo padrão para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f5fc1-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="f5fc1-103">A política de cache baseada em tempo padrão permite que um aplicativo tenha seu comportamento de cache definido pelos cabeçalhos enviados com o recurso em cache e o comportamento de cache definido nas seções 13 e 14 do RFC 2616, disponível no site da [IETF (Internet Engineering Task Force)](https://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="f5fc1-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="f5fc1-104">Esse é o comportamento de cache apropriado para a maioria dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f5fc1-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="f5fc1-105">Para definir a política automática padrão para um aplicativo</span><span class="sxs-lookup"><span data-stu-id="f5fc1-105">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="f5fc1-106">Crie um objeto de política com baseado em tempo padrão.</span><span class="sxs-lookup"><span data-stu-id="f5fc1-106">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="f5fc1-107">Defina o objeto de política como o padrão para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5fc1-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5fc1-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5fc1-108">Example</span></span>  
 <span data-ttu-id="f5fc1-109">Os dois exemplos nesta seção produzem políticas idênticas.</span><span class="sxs-lookup"><span data-stu-id="f5fc1-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="f5fc1-110">O exemplo a seguir cria uma política baseada em tempo padrão e define-a como o padrão para o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5fc1-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 <span data-ttu-id="f5fc1-111">Você também pode criar a política de cache baseada em tempo padrão usando a classe <xref:System.Net.Cache.RequestCachePolicy> conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f5fc1-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5fc1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5fc1-112">See Also</span></span>  
 [<span data-ttu-id="f5fc1-113">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="f5fc1-113">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="f5fc1-114">Política de cache</span><span class="sxs-lookup"><span data-stu-id="f5fc1-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="f5fc1-115">Políticas de cache baseadas na localização</span><span class="sxs-lookup"><span data-stu-id="f5fc1-115">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="f5fc1-116">Políticas de cache baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="f5fc1-116">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="f5fc1-117">[\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="f5fc1-117">[\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)</span></span>
