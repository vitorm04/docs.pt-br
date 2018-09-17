---
title: Usando variância para delegados genéricos Func e Action (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 903926bc86b1b96cea25b91314e35ed4771bbcb9
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45679126"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="805ae-102">Usando variância para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="805ae-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="805ae-103">Esses exemplos demonstram como usar covariância e contravariância nos delegados genéricos `Func` e `Action` para permitir a reutilização dos métodos e fornecer mais flexibilidade em seu código.</span><span class="sxs-lookup"><span data-stu-id="805ae-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="805ae-104">Para obter mais informações sobre covariância e contravariância, consulte [Variação em delegações (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="805ae-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="805ae-105">Usando delegados com parâmetros de tipo covariantes</span><span class="sxs-lookup"><span data-stu-id="805ae-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="805ae-106">O exemplo a seguir ilustra os benefícios do suporte à covariância nos delegados genéricos `Func`.</span><span class="sxs-lookup"><span data-stu-id="805ae-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="805ae-107">O método `FindByTitle` assume um parâmetro do tipo `String` e retorna um objeto do tipo `Employee`.</span><span class="sxs-lookup"><span data-stu-id="805ae-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="805ae-108">No entanto, você pode atribuir esse método ao delegado `Func<String, Person>` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="805ae-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="805ae-109">Usando delegados com parâmetros de tipo contravariantes</span><span class="sxs-lookup"><span data-stu-id="805ae-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="805ae-110">O exemplo a seguir ilustra os benefícios do suporte à contravariância nos delegados genéricos `Action`.</span><span class="sxs-lookup"><span data-stu-id="805ae-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="805ae-111">O método `AddToContacts` assume um parâmetro do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="805ae-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="805ae-112">No entanto, você pode atribuir esse método ao delegado `Action<Employee>` porque `Employee` herda `Person`.</span><span class="sxs-lookup"><span data-stu-id="805ae-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="805ae-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="805ae-113">See Also</span></span>

- [<span data-ttu-id="805ae-114">Covariância e contravariância (C#)</span><span class="sxs-lookup"><span data-stu-id="805ae-114">Covariance and Contravariance (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
- [<span data-ttu-id="805ae-115">Genéricos</span><span class="sxs-lookup"><span data-stu-id="805ae-115">Generics</span></span>](~/docs/standard/generics/index.md)
