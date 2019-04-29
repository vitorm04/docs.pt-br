---
title: 'Como: criar um objeto WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f298a7b036857e783efa128ce45ee8634ce993d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795169"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Como: criar um objeto WindowsPrincipal
Há duas maneiras de criar um <xref:System.Security.Principal.WindowsPrincipal> do objeto, dependendo se o código deve repetidamente executar a validação baseada em função ou ele deve executar apenas uma vez.  
  
 Se o código repetidamente deve executar a validação baseada em função, o primeiro dos procedimentos a seguir produz menos sobrecarga. Quando o código precisa para fazer validações baseado em função, somente uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Para criar um objeto WindowsPrincipal para validação repetida  
  
1. Chame o <xref:System.AppDomain.SetPrincipalPolicy%2A> método na <xref:System.AppDomain> objeto que é retornado pelo estático <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> propriedade, passando o método um <xref:System.Security.Principal.PrincipalPolicy> valor de enumeração que indica qual deve ser a nova política. Valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. O código a seguir demonstra essa chamada de método.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Com a política definida, use estático <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> propriedade para recuperar a entidade de segurança que encapsula o usuário atual do Windows. Como a propriedade de tipo de retorno é <xref:System.Security.Principal.IPrincipal>, você deve converter o resultado para um <xref:System.Security.Principal.WindowsPrincipal> tipo. O código a seguir inicializa uma nova <xref:System.Security.Principal.WindowsPrincipal> objeto para o valor da entidade de segurança associado ao thread atual.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. Quando o objeto de entidade tiver sido criado, você pode usar um dos vários métodos para validá-la.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Para criar um objeto WindowsPrincipal para uma validação único  
  
1. Inicializar uma nova <xref:System.Security.Principal.WindowsIdentity> objeto chamando estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> método, que consulta a conta do Windows atual e coloca informações sobre essa conta para o objeto de identidade recém-criada. O código a seguir cria um novo <xref:System.Security.Principal.WindowsIdentity> do objeto e inicializa-o para o usuário autenticado atual.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Criar um novo <xref:System.Security.Principal.WindowsPrincipal> do objeto e passe-o valor da <xref:System.Security.Principal.WindowsIdentity> objeto criado na etapa anterior.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Quando o objeto de entidade tiver sido criado, você pode usar um dos vários métodos para validá-la.  
  
## <a name="see-also"></a>Consulte também

- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
