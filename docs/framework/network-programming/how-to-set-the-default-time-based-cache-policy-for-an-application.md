---
title: 'Como: Definir uma política de cache baseada em tempo padrão para um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: d40b0ffbe514429ed24eaa5d0c2ce2d52c80d37d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608947"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Como: Definir uma política de cache baseada em tempo padrão para um aplicativo
A política de cache baseada em tempo padrão permite que um aplicativo tenha seu comportamento de cache definido pelos cabeçalhos enviados com o recurso em cache e o comportamento de cache definido nas seções 13 e 14 do RFC 2616, disponível no site da [IETF (Internet Engineering Task Force)](https://www.ietf.org/). Esse é o comportamento de cache apropriado para a maioria dos aplicativos.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Para definir a política automática padrão para um aplicativo  
  
1.  Crie um objeto de política com baseado em tempo padrão.  
  
2.  Defina o objeto de política como o padrão para o domínio do aplicativo.  
  
## <a name="example"></a>Exemplo  
 Os dois exemplos nesta seção produzem políticas idênticas.  
  
 O exemplo a seguir cria uma política baseada em tempo padrão e define-a como o padrão para o domínio do aplicativo.  
  
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
  
 Você também pode criar a política de cache baseada em tempo padrão usando a classe <xref:System.Net.Cache.RequestCachePolicy> conforme mostrado no exemplo a seguir:  
  
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
  
## <a name="see-also"></a>Consulte também
- [Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Política de cache](../../../docs/framework/network-programming/cache-policy.md)
- [Políticas de cache baseadas na localização](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Políticas de cache baseadas em tempo](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]
