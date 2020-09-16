---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556315"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="b7e63-101">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="b7e63-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="b7e63-102">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> Construtor é obsoleto e produz um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b7e63-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="b7e63-103">Não é possível instanciar esse atributo ou aplicá-lo a um método.</span><span class="sxs-lookup"><span data-stu-id="b7e63-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b7e63-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b7e63-104">Change description</span></span>

<span data-ttu-id="b7e63-105">No .NET Framework e no .NET Core, você pode anotar métodos com o <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="b7e63-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="b7e63-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b7e63-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="b7e63-107">A partir do .NET 5,0, você não pode aplicar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo a um método.</span><span class="sxs-lookup"><span data-stu-id="b7e63-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="b7e63-108">O construtor do atributo é obsoleto e produz um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b7e63-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="b7e63-109">Ao contrário de outros avisos do obsoletion, não é possível suprimir o erro.</span><span class="sxs-lookup"><span data-stu-id="b7e63-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b7e63-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b7e63-110">Reason for change</span></span>

<span data-ttu-id="b7e63-111">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> tipo, como outros tipos dos quais a subclasse faz <xref:System.Security.Permissions.SecurityAttribute> parte. Infraestrutura de CAS (segurança de acesso ao código) da rede.</span><span class="sxs-lookup"><span data-stu-id="b7e63-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="b7e63-112">No .NET Framework 2. x-4. x, o tempo de execução impõe <xref:System.Security.Permissions.PrincipalPermissionAttribute> anotações na entrada do método, mesmo que o aplicativo esteja sendo executado em um cenário de confiança total.</span><span class="sxs-lookup"><span data-stu-id="b7e63-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="b7e63-113">O .NET Core e o .NET 5,0 e posterior não dão suporte a atributos de CAS e o tempo de execução os ignora.</span><span class="sxs-lookup"><span data-stu-id="b7e63-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="b7e63-114">Essa diferença no comportamento de .NET Framework para .NET Core e .NET 5,0 pode resultar em um cenário de "falha aberta", em que o acesso deveria ter sido bloqueado, mas, em vez disso, ter sido permitido.</span><span class="sxs-lookup"><span data-stu-id="b7e63-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="b7e63-115">Para evitar o cenário de "falha aberta", você não pode mais aplicar o atributo no código que tem como destino o .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b7e63-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b7e63-116">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b7e63-116">Version introduced</span></span>

<span data-ttu-id="b7e63-117">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="b7e63-117">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b7e63-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b7e63-118">Recommended action</span></span>

<span data-ttu-id="b7e63-119">Se você encontrar o erro obsoletion, deverá executar uma ação.</span><span class="sxs-lookup"><span data-stu-id="b7e63-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="b7e63-120">**Se você estiver aplicando o atributo a um método de ação ASP.NET MVC:**</span><span class="sxs-lookup"><span data-stu-id="b7e63-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="b7e63-121">Considere o uso do ASP. A infraestrutura de autorização interna da rede.</span><span class="sxs-lookup"><span data-stu-id="b7e63-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="b7e63-122">O código a seguir demonstra como anotar um controlador com um <xref:System.Web.Mvc.AuthorizeAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="b7e63-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="b7e63-123">O tempo de execução do ASP.NET autorizará o usuário antes de executar a ação.</span><span class="sxs-lookup"><span data-stu-id="b7e63-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="b7e63-124">Para obter mais informações, consulte [autorização baseada em função no ASP.NET Core](/aspnet/core/security/authorization/roles) e [introdução à autorização no ASP.NET Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="b7e63-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="b7e63-125">**Se você estiver aplicando o atributo ao código de biblioteca fora do contexto de um aplicativo Web:**</span><span class="sxs-lookup"><span data-stu-id="b7e63-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="b7e63-126">Execute as verificações manualmente no início do método.</span><span class="sxs-lookup"><span data-stu-id="b7e63-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="b7e63-127">Isso pode ser feito usando o <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="b7e63-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="b7e63-128">Categoria</span><span class="sxs-lookup"><span data-stu-id="b7e63-128">Category</span></span>

- <span data-ttu-id="b7e63-129">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="b7e63-129">Core .NET libraries</span></span>
- <span data-ttu-id="b7e63-130">Segurança</span><span class="sxs-lookup"><span data-stu-id="b7e63-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b7e63-131">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b7e63-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
