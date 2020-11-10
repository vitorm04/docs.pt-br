---
title: Erro de SYSLIB0002
description: Saiba mais sobre o obsoletion que gera erros de tempo de compilação SYSLIB0002.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 53eb51d5e525c463e5698710bdb6fa0c0907e43c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440771"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="850b0-103">SYSLIB0002: PrincipalPermissionattribute está obsoleto</span><span class="sxs-lookup"><span data-stu-id="850b0-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="850b0-104">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> Construtor é obsoleto e produz erro de tempo de compilação `SYSLIB0002` , a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="850b0-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="850b0-105">Não é possível instanciar esse atributo ou aplicá-lo a um método.</span><span class="sxs-lookup"><span data-stu-id="850b0-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="850b0-106">Ao contrário de outros avisos do obsoletion, não é possível suprimir o erro.</span><span class="sxs-lookup"><span data-stu-id="850b0-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="850b0-107">Soluções Alternativas</span><span class="sxs-lookup"><span data-stu-id="850b0-107">Workarounds</span></span>

- <span data-ttu-id="850b0-108">Se você estiver aplicando o atributo a um método de ação ASP.NET MVC:</span><span class="sxs-lookup"><span data-stu-id="850b0-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="850b0-109">Considere o uso do ASP. A infraestrutura de autorização interna da rede.</span><span class="sxs-lookup"><span data-stu-id="850b0-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="850b0-110">O código a seguir demonstra como anotar um controlador com um <xref:System.Web.Mvc.AuthorizeAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="850b0-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="850b0-111">O tempo de execução do ASP.NET autorizará o usuário antes de executar a ação.</span><span class="sxs-lookup"><span data-stu-id="850b0-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="850b0-112">Para obter mais informações, consulte [autorização baseada em função no ASP.NET Core](/aspnet/core/security/authorization/roles) e [introdução à autorização no ASP.NET Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="850b0-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="850b0-113">Se você estiver aplicando o atributo ao código de biblioteca fora do contexto de um aplicativo Web:</span><span class="sxs-lookup"><span data-stu-id="850b0-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="850b0-114">Execute as verificações manualmente no início do método chamando o <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="850b0-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="850b0-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="850b0-115">See also</span></span>

- [<span data-ttu-id="850b0-116">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="850b0-116">PrincipalPermissionAttribute is obsolete as error</span></span>](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
