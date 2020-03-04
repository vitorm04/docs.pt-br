---
title: Como criar um objeto WindowsPrincipal
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
ms.openlocfilehash: 30af18b7d7b86621586c7da66eda1b37356d5565
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159774"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Como criar um objeto WindowsPrincipal
Há duas maneiras de criar um objeto de <xref:System.Security.Principal.WindowsPrincipal>, dependendo se o código deve executar repetidamente a validação baseada em função ou deve executá-la apenas uma vez.  
  
 Se o código precisar executar a validação baseada em função repetidamente, o primeiro dos procedimentos a seguir produzirá menos sobrecarga. Quando o código precisa fazer validações baseadas em função apenas uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Para criar um objeto WindowsPrincipal para validação repetida  
  
1. Chame o método <xref:System.AppDomain.SetPrincipalPolicy%2A> no objeto <xref:System.AppDomain> que é retornado pela propriedade <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> estática, passando o método a <xref:System.Security.Principal.PrincipalPolicy> valor de enumeração que indica qual deve ser a nova política. Os valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. O código a seguir demonstra essa chamada de método.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Com a política definida, use a propriedade <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> estática para recuperar a entidade de segurança que encapsula o usuário atual do Windows. Como o tipo de retorno da propriedade é <xref:System.Security.Principal.IPrincipal>, você deve converter o resultado em um tipo de <xref:System.Security.Principal.WindowsPrincipal>. O código a seguir inicializa um novo objeto <xref:System.Security.Principal.WindowsPrincipal> para o valor da entidade de segurança associada ao thread atual.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Para criar um objeto WindowsPrincipal para uma única validação  
  
1. Inicialize um novo objeto <xref:System.Security.Principal.WindowsIdentity> chamando o método estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, que consulta a conta atual do Windows e coloca as informações sobre essa conta no objeto de identidade recém-criado. O código a seguir cria um novo objeto <xref:System.Security.Principal.WindowsIdentity> e o inicializa para o usuário autenticado atual.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Crie um novo objeto <xref:System.Security.Principal.WindowsPrincipal> e passe-o para o valor do objeto <xref:System.Security.Principal.WindowsIdentity> criado na etapa anterior.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.  
  
## <a name="see-also"></a>Confira também

- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
