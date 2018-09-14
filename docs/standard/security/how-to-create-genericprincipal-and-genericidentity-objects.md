---
title: Como criar objetos GenericPrincipal e GenericIdentity
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
ms.openlocfilehash: 79b5e05fe9133eb2282eedefa001e64ece5e0f57
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517067"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="95c2d-102">Como criar objetos GenericPrincipal e GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="95c2d-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="95c2d-103">Você pode usar o <xref:System.Security.Principal.GenericIdentity> classe junto com o <xref:System.Security.Principal.GenericPrincipal> classe para criar um esquema de autorização que existe independentemente de um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="95c2d-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="95c2d-104">Para criar um objeto GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="95c2d-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="95c2d-105">Criar uma nova instância da classe de identidade e inicializá-lo com o nome que você deseja que ela contenha.</span><span class="sxs-lookup"><span data-stu-id="95c2d-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="95c2d-106">O código a seguir cria um novo **GenericIdentity** do objeto e o inicializa com o nome `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="95c2d-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="95c2d-107">Criar uma nova instância dos **GenericPrincipal** de classe e inicializá-lo com criado anteriormente **GenericIdentity** objeto e uma matriz de cadeias de caracteres que representam as funções que você deseja associadas Essa entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="95c2d-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="95c2d-108">O exemplo de código a seguir especifica uma matriz de cadeias de caracteres que representam uma função de administrador e uma função de usuário.</span><span class="sxs-lookup"><span data-stu-id="95c2d-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="95c2d-109">O **GenericPrincipal** , em seguida, é inicializada com o anterior **GenericIdentity** e a matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="95c2d-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  <span data-ttu-id="95c2d-110">Use o código a seguir para anexar a entidade de segurança ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="95c2d-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="95c2d-111">Isso é útil em situações em que a entidade de segurança deve ser validada várias vezes, ele deve ser validado por outro código em execução em seu aplicativo ou ele deve ser validado por um <xref:System.Security.Permissions.PrincipalPermission> objeto.</span><span class="sxs-lookup"><span data-stu-id="95c2d-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="95c2d-112">Você ainda poderá realizar validação baseada em função no objeto de entidade sem anexá-lo para o thread.</span><span class="sxs-lookup"><span data-stu-id="95c2d-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="95c2d-113">Para obter mais informações, consulte [substituindo um objeto Principal](../../../docs/standard/security/replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="95c2d-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="95c2d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c2d-114">Example</span></span>  
 <span data-ttu-id="95c2d-115">O exemplo de código a seguir demonstra como criar uma instância de um **GenericPrincipal** e uma **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="95c2d-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="95c2d-116">Esse código exibe os valores desses objetos no console.</span><span class="sxs-lookup"><span data-stu-id="95c2d-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
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
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="95c2d-117">Quando executado, o aplicativo exibe a saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="95c2d-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="95c2d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c2d-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>  
- <xref:System.Security.Principal.GenericPrincipal>  
- <xref:System.Security.Permissions.PrincipalPermission>  
- [<span data-ttu-id="95c2d-119">Como substituir um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="95c2d-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)  
- [<span data-ttu-id="95c2d-120">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="95c2d-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
