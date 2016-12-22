---
title: "Criando Interfaces gen&#233;ricas variantes (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Criando Interfaces gen&#233;ricas variantes (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode declarar parâmetros de tipo genérico em interfaces como covariant ou contravariant.*Covariância* permite que os métodos de interface mais derivada tipos de retorno daquele definido pelos parâmetros de tipo genérico.*Contravariância* permite que os métodos de interface com tipos de argumento que são menos derivados que aquele especificado pelos parâmetros genéricos. Uma interface genérica que tenha covariant ou contravariant parâmetros de tipo genérico é chamado *variante*.  
  
> [!NOTE]
>  O .NET framework 4 introduziu o suporte de variação de várias interfaces genéricas existentes. Para obter a lista das interfaces de variantes no .NET Framework, consulte [Variação em Interfaces genéricas \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## Declaração Interfaces genéricas variáveis  
 Você pode declarar interfaces genéricas variáveis usando a `in` e `out` palavras\-chave para parâmetros de tipo genérico.  
  
> [!IMPORTANT]
>  `ref` e `out` parâmetros em c\# não podem ser uma variante. Tipos de valor também têm suporte para variação.  
  
 Você pode declarar um parâmetro de tipo genérico covariante usando o `out` palavra\-chave. O tipo de covariante deve satisfazer as condições a seguir:  
  
-   O tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos do método. Isso é ilustrado no exemplo a seguir, no qual o tipo `R` é declarado covariante.  
  
    ```c#  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Há uma exceção a essa regra. Se você tiver um delegado genérico contravariant como um parâmetro de método, você pode usar o tipo como um parâmetro de tipo genérico para o delegado. Isso é ilustrado pelo tipo `R` no exemplo a seguir. Para obter mais informações, consulte [Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variação para delegações Func e Action genéricas \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```c#  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   O tipo não é usado como uma restrição genérica para os métodos de interface. Isso é ilustrado no código a seguir.  
  
    ```c#  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Você pode declarar um contravariant de parâmetro de tipo genérico usando o `in` palavra\-chave. O tipo contravariant pode ser usado apenas como um tipo de argumentos de método e não como um tipo de retorno dos métodos de interface. O tipo contravariant também pode ser usado para restrições genéricas. O código a seguir mostra como declarar uma interface contravariant e usar uma restrição genérica para um de seus métodos.  
  
```c#  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Também é possível oferecer suporte a covariância e contravariância na mesma interface, mas para os parâmetros de tipo diferente, conforme mostrado no exemplo de código a seguir.  
  
```c#  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## Implementando Interfaces genéricas variáveis  
 Você pode implementar interfaces genéricas variáveis em classes usando a mesma sintaxe que é usada para interfaces invariáveis. O exemplo de código a seguir mostra como implementar uma interface covariante em uma classe genérica.  
  
```c#  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 Classes que implementam interfaces variantes são invariáveis. Por exemplo, considere o código a seguir.  
  
```c#  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## Estendendo Interfaces genéricas variáveis  
 Quando você estende uma interface genérica variante, você deve usar o `in` e `out` palavras\-chave para especificar explicitamente se a interface derivada oferece suporte a variação. O compilador não deduzir a variação da interface que está sendo estendida. Por exemplo, considere as seguintes interfaces.  
  
```c#  
nterface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 No `IInvariant<T>` da interface, o parâmetro de tipo genérico `T` é invariável, enquanto no `IExtCovariant<out T>` o parâmetro de tipo é covariante, embora ambas as interfaces estendem a mesma interface. A mesma regra é aplicada aos parâmetros de tipo genérico contravariant.  
  
 Você pode criar uma interface que estende tanto o interface em que o parâmetro de tipo genérico `T` é covariante e a interface onde é contravariant em caso da estender o parâmetro de tipo genérico de interface `T` é invariável. Isso é ilustrado no exemplo de código a seguir.  
  
```c#  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 No entanto, se um parâmetro de tipo genérico `T` é declarado covariante em uma interface, você não pode declará\-lo contravariant na interface de extensão, ou vice\-versa. Isso é ilustrado no exemplo de código a seguir.  
  
```c#  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### Evitar ambigüidade  
 Ao implementar interfaces genéricas variantes, variação, às vezes, pode levar a ambigüidade. Isso deve ser evitado.  
  
 Por exemplo, se você implementar explicitamente a mesma interface genérica variante com parâmetros de tipo genérico diferentes em uma classe, ele pode criar ambiguidade. O compilador não produz um erro nesse caso, mas ele não estiver especificado qual implementação de interface será escolhida em tempo de execução. Isso pode levar a erros sutis no seu código. Considere o exemplo de código a seguir.  
  
```c#  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 Neste exemplo, ele está especificado como o `pets.GetEnumerator` método escolhe entre `Cat` e `Dog`. Isso pode causar problemas em seu código.  
  
## Consulte também  
 [Variação em Interfaces genéricas \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [Usando variação para delegações Func e Action genéricas \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)