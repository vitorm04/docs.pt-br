---
title: 'Como: criar um objeto WindowsPrincipal'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: d99d63dc766f37e7cc30888d2e77657595f909af
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557028"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="30a55-102">Como: criar um objeto WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="30a55-102">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="30a55-103">Este artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="30a55-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="30a55-104">Para obter informações sobre ASP.NET Core, consulte [segurança do ASP.NET Core](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="30a55-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="30a55-105">Há duas maneiras de criar um <xref:System.Security.Principal.WindowsPrincipal> objeto, dependendo se o código deve executar repetidamente a validação baseada em função ou deve executá-la apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="30a55-105">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="30a55-106">Se o código precisar executar a validação baseada em função repetidamente, o primeiro dos procedimentos a seguir produzirá menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="30a55-106">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="30a55-107">Quando o código precisa fazer validações baseadas em função apenas uma vez, você pode criar um <xref:System.Security.Principal.WindowsPrincipal> objeto usando o segundo dos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="30a55-107">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="30a55-108">Para criar um objeto WindowsPrincipal para validação repetida</span><span class="sxs-lookup"><span data-stu-id="30a55-108">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="30a55-109">Chame o <xref:System.AppDomain.SetPrincipalPolicy%2A> método no <xref:System.AppDomain> objeto que é retornado pela <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> propriedade estática, passando o método um valor de <xref:System.Security.Principal.PrincipalPolicy> enumeração que indica qual deve ser a nova política.</span><span class="sxs-lookup"><span data-stu-id="30a55-109">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="30a55-110">Os valores com suporte são <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> e <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="30a55-110">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="30a55-111">O código a seguir demonstra essa chamada de método.</span><span class="sxs-lookup"><span data-stu-id="30a55-111">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="30a55-112">Com a política definida, use a <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> propriedade estática para recuperar a entidade de segurança que encapsula o usuário atual do Windows.</span><span class="sxs-lookup"><span data-stu-id="30a55-112">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="30a55-113">Como o tipo de retorno da propriedade é <xref:System.Security.Principal.IPrincipal> , você deve converter o resultado em um <xref:System.Security.Principal.WindowsPrincipal> tipo.</span><span class="sxs-lookup"><span data-stu-id="30a55-113">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="30a55-114">O código a seguir inicializa um novo <xref:System.Security.Principal.WindowsPrincipal> objeto para o valor da entidade de segurança associada ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="30a55-114">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="30a55-115">Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.</span><span class="sxs-lookup"><span data-stu-id="30a55-115">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="30a55-116">Para criar um objeto WindowsPrincipal para uma única validação</span><span class="sxs-lookup"><span data-stu-id="30a55-116">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="30a55-117">Inicialize um novo <xref:System.Security.Principal.WindowsIdentity> objeto chamando o método estático <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> , que consulta a conta atual do Windows e coloca as informações sobre essa conta no objeto de identidade recém-criado.</span><span class="sxs-lookup"><span data-stu-id="30a55-117">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="30a55-118">O código a seguir cria um novo <xref:System.Security.Principal.WindowsIdentity> objeto e o inicializa para o usuário autenticado atual.</span><span class="sxs-lookup"><span data-stu-id="30a55-118">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="30a55-119">Crie um novo <xref:System.Security.Principal.WindowsPrincipal> objeto e passe-o para o valor do <xref:System.Security.Principal.WindowsIdentity> objeto criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="30a55-119">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="30a55-120">Quando o objeto principal tiver sido criado, você poderá usar um dos vários métodos para validá-lo.</span><span class="sxs-lookup"><span data-stu-id="30a55-120">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a55-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="30a55-121">See also</span></span>

- [<span data-ttu-id="30a55-122">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="30a55-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="30a55-123">Segurança de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30a55-123">ASP.NET Core Security</span></span>](https://docs.microsoft.com/aspnet/core/security/)
