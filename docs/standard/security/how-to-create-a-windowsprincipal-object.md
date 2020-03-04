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
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="927f1-102">Como criar um objeto WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="927f1-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="927f1-103">Há duas maneiras de criar um objeto de <xref:System.Security.Principal.WindowsPrincipal>, dependendo se o código deve executar repetidamente a validação baseada em função ou deve executá-la apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="927f1-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="927f1-104">Se o código precisar executar a validação baseada em função repetidamente, o primeiro dos procedimentos a seguir produzirá menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="927f1-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="927f1-105">Quando o código precisa fazer validações baseadas em função apenas uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="927f1-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="927f1-106">Para criar um objeto WindowsPrincipal para validação repetida</span><span class="sxs-lookup"><span data-stu-id="927f1-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="927f1-107">Chame o método <xref:System.AppDomain.SetPrincipalPolicy%2A> no objeto <xref:System.AppDomain> que é retornado pela propriedade <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> estática, passando o método a <xref:System.Security.Principal.PrincipalPolicy> valor de enumeração que indica qual deve ser a nova política.</span><span class="sxs-lookup"><span data-stu-id="927f1-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="927f1-108">Os valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="927f1-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="927f1-109">O código a seguir demonstra essa chamada de método.</span><span class="sxs-lookup"><span data-stu-id="927f1-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="927f1-110">Com a política definida, use a propriedade <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> estática para recuperar a entidade de segurança que encapsula o usuário atual do Windows.</span><span class="sxs-lookup"><span data-stu-id="927f1-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="927f1-111">Como o tipo de retorno da propriedade é <xref:System.Security.Principal.IPrincipal>, você deve converter o resultado em um tipo de <xref:System.Security.Principal.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="927f1-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="927f1-112">O código a seguir inicializa um novo objeto <xref:System.Security.Principal.WindowsPrincipal> para o valor da entidade de segurança associada ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="927f1-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="927f1-113">Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.</span><span class="sxs-lookup"><span data-stu-id="927f1-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="927f1-114">Para criar um objeto WindowsPrincipal para uma única validação</span><span class="sxs-lookup"><span data-stu-id="927f1-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="927f1-115">Inicialize um novo objeto <xref:System.Security.Principal.WindowsIdentity> chamando o método estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, que consulta a conta atual do Windows e coloca as informações sobre essa conta no objeto de identidade recém-criado.</span><span class="sxs-lookup"><span data-stu-id="927f1-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="927f1-116">O código a seguir cria um novo objeto <xref:System.Security.Principal.WindowsIdentity> e o inicializa para o usuário autenticado atual.</span><span class="sxs-lookup"><span data-stu-id="927f1-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="927f1-117">Crie um novo objeto <xref:System.Security.Principal.WindowsPrincipal> e passe-o para o valor do objeto <xref:System.Security.Principal.WindowsIdentity> criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="927f1-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="927f1-118">Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.</span><span class="sxs-lookup"><span data-stu-id="927f1-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927f1-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="927f1-119">See also</span></span>

- [<span data-ttu-id="927f1-120">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="927f1-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
