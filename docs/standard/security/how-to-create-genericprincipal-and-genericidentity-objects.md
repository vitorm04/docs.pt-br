---
title: 'Como: criar objetos GenericPrincipal e GenericIdentity'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f768242bffe619051779f87e950138ae9fcec6c
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353178"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="e6436-102">Como: criar objetos GenericPrincipal e GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="e6436-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

<span data-ttu-id="e6436-103">Você pode usar a classe <xref:System.Security.Principal.GenericIdentity> em conjunto com a classe <xref:System.Security.Principal.GenericPrincipal> para criar um esquema de autorização que existe independentemente de um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="e6436-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="e6436-104">Para criar um objeto GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="e6436-104">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="e6436-105">Crie uma nova instância da classe Identity e inicialize-a com o nome que você deseja que ela mantenha.</span><span class="sxs-lookup"><span data-stu-id="e6436-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="e6436-106">O código a seguir cria um novo objeto **GenericIdentity** e o inicializa com o nome `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="e6436-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="e6436-107">Crie uma nova instância da classe **GenericPrincipal** e inicialize-a com o objeto **GenericIdentity** criado anteriormente e uma matriz de cadeias de caracteres que representem as funções que você deseja associar a essa entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="e6436-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="e6436-108">O exemplo de código a seguir especifica uma matriz de cadeias de caracteres que representam uma função de administrador e uma função de usuário.</span><span class="sxs-lookup"><span data-stu-id="e6436-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="e6436-109">Em seguida, o **GenericPrincipal** é inicializado com o **GenericIdentity** anterior e a matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6436-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="e6436-110">Use o código a seguir para anexar a entidade de segurança ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="e6436-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="e6436-111">Isso é valioso em situações em que a entidade de segurança deve ser validada várias vezes, deve ser validada por outro código em execução em seu aplicativo ou deve ser validada por um objeto <xref:System.Security.Permissions.PrincipalPermission>.</span><span class="sxs-lookup"><span data-stu-id="e6436-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="e6436-112">Você ainda pode executar a validação baseada em função no objeto principal sem anexá-lo ao thread.</span><span class="sxs-lookup"><span data-stu-id="e6436-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="e6436-113">Para obter mais informações, consulte [substituindo um objeto principal](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="e6436-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="e6436-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6436-114">Example</span></span>

<span data-ttu-id="e6436-115">O exemplo de código a seguir demonstra como criar uma instância de um **GenericPrincipal** e um **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="e6436-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="e6436-116">Esse código exibe os valores desses objetos para o console.</span><span class="sxs-lookup"><span data-stu-id="e6436-116">This code displays the values of these objects to the console.</span></span>

```vb
Imports System
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

<span data-ttu-id="e6436-117">Quando executado, o aplicativo exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="e6436-117">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="e6436-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6436-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="e6436-119">Como substituir um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="e6436-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="e6436-120">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="e6436-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
