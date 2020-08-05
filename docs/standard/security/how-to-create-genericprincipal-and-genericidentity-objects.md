---
title: 'Como: criar objetos GenericPrincipal e GenericIdentity'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 903d636938c47850951330d7936d95470441607e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557210"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="07109-102">Como: criar objetos GenericPrincipal e GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="07109-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="07109-103">Este artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="07109-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="07109-104">Para obter informações sobre ASP.NET Core, consulte [visão geral da segurança do ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="07109-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](https://docs.microsoft.com/aspnet/core/security/).</span></span>

<span data-ttu-id="07109-105">Você pode usar a <xref:System.Security.Principal.GenericIdentity> classe em conjunto com a <xref:System.Security.Principal.GenericPrincipal> classe para criar um esquema de autorização que existe independentemente de um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="07109-105">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="07109-106">Para criar um objeto GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="07109-106">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="07109-107">Crie uma nova instância da classe Identity e inicialize-a com o nome que você deseja que ela mantenha.</span><span class="sxs-lookup"><span data-stu-id="07109-107">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="07109-108">O código a seguir cria um novo objeto **GenericIdentity** e inicializa-o com o nome `MyUser` .</span><span class="sxs-lookup"><span data-stu-id="07109-108">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="07109-109">Crie uma nova instância da classe **GenericPrincipal** e inicialize-a com o objeto **GenericIdentity** criado anteriormente e uma matriz de cadeias de caracteres que representem as funções que você deseja associar a essa entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="07109-109">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="07109-110">O exemplo de código a seguir especifica uma matriz de cadeias de caracteres que representam uma função de administrador e uma função de usuário.</span><span class="sxs-lookup"><span data-stu-id="07109-110">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="07109-111">Em seguida, o **GenericPrincipal** é inicializado com o **GenericIdentity** anterior e a matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="07109-111">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="07109-112">Use o código a seguir para anexar a entidade de segurança ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="07109-112">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="07109-113">Isso é valioso em situações em que a entidade de segurança deve ser validada várias vezes, ela deve ser validada por outro código em execução em seu aplicativo ou deve ser validada por um <xref:System.Security.Permissions.PrincipalPermission> objeto.</span><span class="sxs-lookup"><span data-stu-id="07109-113">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="07109-114">Você ainda pode executar a validação baseada em função no objeto principal sem anexá-lo ao thread.</span><span class="sxs-lookup"><span data-stu-id="07109-114">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="07109-115">Para obter mais informações, consulte [substituindo um objeto principal](replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="07109-115">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="07109-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07109-116">Example</span></span>

<span data-ttu-id="07109-117">O exemplo de código a seguir demonstra como criar uma instância de um **GenericPrincipal** e um **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="07109-117">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="07109-118">Esse código exibe os valores desses objetos para o console.</span><span class="sxs-lookup"><span data-stu-id="07109-118">This code displays the values of these objects to the console.</span></span>

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="07109-119">Quando executado, o aplicativo exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="07109-119">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="07109-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="07109-120">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="07109-121">Substituindo um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="07109-121">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="07109-122">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="07109-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
