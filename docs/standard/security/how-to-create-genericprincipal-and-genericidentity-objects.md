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
ms.openlocfilehash: b47f4c093acb094188cbd5a8a0a0026c67eb3f2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795155"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Como: criar objetos GenericPrincipal e GenericIdentity

Você pode usar o <xref:System.Security.Principal.GenericIdentity> classe junto com o <xref:System.Security.Principal.GenericPrincipal> classe para criar um esquema de autorização que existe independentemente de um domínio do Windows.

### <a name="to-create-a-genericprincipal-object"></a>Para criar um objeto GenericPrincipal

1. Criar uma nova instância da classe de identidade e inicializá-lo com o nome que você deseja que ela contenha. O código a seguir cria um novo **GenericIdentity** do objeto e o inicializa com o nome `MyUser`.

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. Criar uma nova instância dos **GenericPrincipal** de classe e inicializá-lo com criado anteriormente **GenericIdentity** objeto e uma matriz de cadeias de caracteres que representam as funções que você deseja associadas Essa entidade de segurança. O exemplo de código a seguir especifica uma matriz de cadeias de caracteres que representam uma função de administrador e uma função de usuário. O **GenericPrincipal** , em seguida, é inicializada com o anterior **GenericIdentity** e a matriz de cadeia de caracteres.

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. Use o código a seguir para anexar a entidade de segurança ao thread atual. Isso é útil em situações em que a entidade de segurança deve ser validada várias vezes, ele deve ser validado por outro código em execução em seu aplicativo ou ele deve ser validado por um <xref:System.Security.Permissions.PrincipalPermission> objeto. Você ainda poderá realizar validação baseada em função no objeto de entidade sem anexá-lo para o thread. Para obter mais informações, consulte [substituindo um objeto Principal](../../../docs/standard/security/replacing-a-principal-object.md).

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra como criar uma instância de um **GenericPrincipal** e uma **GenericIdentity**. Esse código exibe os valores desses objetos no console.

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

Quando executado, o aplicativo exibe a saída semelhante à seguinte.

```
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a>Consulte também

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [Como substituir um objeto Principal](../../../docs/standard/security/replacing-a-principal-object.md)
- [Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)
