---
title: Como criar um objeto WindowsPrincipal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f35c7382138c92a5f6618e388b070251516b7b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Como criar um objeto WindowsPrincipal
Há duas maneiras de criar um <xref:System.Security.Principal.WindowsPrincipal> de objeto, dependendo se o código deve repetidamente executar validação baseada em função ou execute-a apenas uma vez.  
  
 Se o código repetidamente deve executar a validação baseada em função, o primeiro dos procedimentos a seguir produz menos sobrecarga. Quando o código precisa para fazer validação baseada em função, somente uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Para criar um objeto WindowsPrincipal para validação repetida  
  
1.  Chamar o <xref:System.AppDomain.SetPrincipalPolicy%2A> método no <xref:System.AppDomain> objeto que é retornado pelo estático <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> propriedade, passando-o um <xref:System.Security.Principal.PrincipalPolicy> valor de enumeração que indica o que deve ser a nova política. Valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. O código a seguir demonstra essa chamada de método.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Com a política definida, use estático <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> propriedade para recuperar o objeto que encapsula o usuário atual do Windows. Como a propriedade de tipo de retorno é <xref:System.Security.Principal.IPrincipal>, você deve converter o resultado em um <xref:System.Security.Principal.WindowsPrincipal> tipo. O código a seguir inicializa uma nova <xref:System.Security.Principal.WindowsPrincipal> objeto para o valor da entidade de segurança associado ao segmento atual.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Quando o objeto tiver sido criado, você pode usar um dos vários métodos para validá-lo.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Para criar um objeto WindowsPrincipal para um único validação  
  
1.  Inicializar uma nova <xref:System.Security.Principal.WindowsIdentity> objeto chamando estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> método, que consulta a conta do Windows atual e coloca informações sobre essa conta para o objeto de identidade recém-criada. O código a seguir cria um novo <xref:System.Security.Principal.WindowsIdentity> do objeto e a inicializa para o usuário autenticado atual.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Criar um novo <xref:System.Security.Principal.WindowsPrincipal> do objeto e passe o valor de <xref:System.Security.Principal.WindowsIdentity> objeto criado na etapa anterior.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Quando o objeto tiver sido criado, você pode usar um dos vários métodos para validá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
