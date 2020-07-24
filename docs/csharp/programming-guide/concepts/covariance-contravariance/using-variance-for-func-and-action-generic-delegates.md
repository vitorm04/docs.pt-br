---
title: Usando variância para delegados genéricos Func e Action (C#)
description: Saiba mais sobre como usar Covariance e contravariância nos delegados de Func e Action Generic para proporcionar mais flexibilidade em seu código.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: d7174b0f734d10ab69d0936cb5ca4aa2f4fafdf7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105707"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="acfec-103">Usando variância para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="acfec-103">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="acfec-104">Esses exemplos demonstram como usar covariância e contravariância nos delegados genéricos `Func` e `Action` para permitir a reutilização dos métodos e fornecer mais flexibilidade em seu código.</span><span class="sxs-lookup"><span data-stu-id="acfec-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="acfec-105">Para obter mais informações sobre covariância e contravariância, consulte [Variação em delegações (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="acfec-105">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="acfec-106">Usando delegados com parâmetros de tipo covariantes</span><span class="sxs-lookup"><span data-stu-id="acfec-106">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="acfec-107">O exemplo a seguir ilustra os benefícios do suporte à covariância nos delegados genéricos `Func`.</span><span class="sxs-lookup"><span data-stu-id="acfec-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="acfec-108">O método `FindByTitle` assume um parâmetro do tipo `String` e retorna um objeto do tipo `Employee`.</span><span class="sxs-lookup"><span data-stu-id="acfec-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="acfec-109">No entanto, você pode atribuir esse método ao delegado `Func<String, Person>` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="acfec-109">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="acfec-110">Usando delegados com parâmetros de tipo contravariantes</span><span class="sxs-lookup"><span data-stu-id="acfec-110">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="acfec-111">O exemplo a seguir ilustra os benefícios do suporte à contravariância nos delegados genéricos `Action`.</span><span class="sxs-lookup"><span data-stu-id="acfec-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="acfec-112">O método `AddToContacts` assume um parâmetro do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="acfec-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="acfec-113">No entanto, você pode atribuir esse método ao delegado `Action<Employee>` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="acfec-113">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="acfec-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="acfec-114">See also</span></span>

- [<span data-ttu-id="acfec-115">Covariância e contravariância (C#)</span><span class="sxs-lookup"><span data-stu-id="acfec-115">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="acfec-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="acfec-116">Generics</span></span>](../../../../standard/generics/index.md)
