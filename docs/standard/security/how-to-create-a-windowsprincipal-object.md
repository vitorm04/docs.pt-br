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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314445"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="a688b-102">Como: criar um objeto WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="a688b-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="a688b-103">Há duas maneiras de criar um <xref:System.Security.Principal.WindowsPrincipal> do objeto, dependendo se o código deve repetidamente executar a validação baseada em função ou ele deve executar apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="a688b-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="a688b-104">Se o código repetidamente deve executar a validação baseada em função, o primeiro dos procedimentos a seguir produz menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="a688b-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="a688b-105">Quando o código precisa para fazer validações baseado em função, somente uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a688b-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="a688b-106">Para criar um objeto WindowsPrincipal para validação repetida</span><span class="sxs-lookup"><span data-stu-id="a688b-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="a688b-107">Chame o <xref:System.AppDomain.SetPrincipalPolicy%2A> método na <xref:System.AppDomain> objeto que é retornado pelo estático <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> propriedade, passando o método um <xref:System.Security.Principal.PrincipalPolicy> valor de enumeração que indica qual deve ser a nova política.</span><span class="sxs-lookup"><span data-stu-id="a688b-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="a688b-108">Valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="a688b-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="a688b-109">O código a seguir demonstra essa chamada de método.</span><span class="sxs-lookup"><span data-stu-id="a688b-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="a688b-110">Com a política definida, use estático <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> propriedade para recuperar a entidade de segurança que encapsula o usuário atual do Windows.</span><span class="sxs-lookup"><span data-stu-id="a688b-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="a688b-111">Como a propriedade de tipo de retorno é <xref:System.Security.Principal.IPrincipal>, você deve converter o resultado para um <xref:System.Security.Principal.WindowsPrincipal> tipo.</span><span class="sxs-lookup"><span data-stu-id="a688b-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="a688b-112">O código a seguir inicializa uma nova <xref:System.Security.Principal.WindowsPrincipal> objeto para o valor da entidade de segurança associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="a688b-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3. <span data-ttu-id="a688b-113">Quando o objeto de entidade tiver sido criado, você pode usar um dos vários métodos para validá-la.</span><span class="sxs-lookup"><span data-stu-id="a688b-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="a688b-114">Para criar um objeto WindowsPrincipal para uma validação único</span><span class="sxs-lookup"><span data-stu-id="a688b-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="a688b-115">Inicializar uma nova <xref:System.Security.Principal.WindowsIdentity> objeto chamando estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> método, que consulta a conta do Windows atual e coloca informações sobre essa conta para o objeto de identidade recém-criada.</span><span class="sxs-lookup"><span data-stu-id="a688b-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="a688b-116">O código a seguir cria um novo <xref:System.Security.Principal.WindowsIdentity> do objeto e inicializa-o para o usuário autenticado atual.</span><span class="sxs-lookup"><span data-stu-id="a688b-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="a688b-117">Criar um novo <xref:System.Security.Principal.WindowsPrincipal> do objeto e passe-o valor da <xref:System.Security.Principal.WindowsIdentity> objeto criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="a688b-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="a688b-118">Quando o objeto de entidade tiver sido criado, você pode usar um dos vários métodos para validá-la.</span><span class="sxs-lookup"><span data-stu-id="a688b-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a688b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a688b-119">See also</span></span>

- [<span data-ttu-id="a688b-120">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="a688b-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
