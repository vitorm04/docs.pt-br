---
title: "Covari&#226;ncia e contravari&#226;ncia (c#) | Microsoft Docs"
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
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Covari&#226;ncia e contravari&#226;ncia (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

No c\#, covariância e contravariância Habilitar conversão de referência implícita de tipos de matriz, tipos de delegados e argumentos de tipo genérico. Covariância preserva a compatibilidade de atribuição e contravariância inverte a ele.  
  
 O código a seguir demonstra a diferença entre a compatibilidade da atribuição, covariância e contravariância.  
  
```c#  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 Covariância de matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo derivado. Mas essa operação não é fortemente tipado, conforme mostrado no exemplo de código a seguir.  
  
```c#  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Covariância e contravariância suporte para grupos de método permite assinaturas de método correspondentes com tipos delegados. Isso permite atribuir a delegados não apenas os métodos que têm correspondência assinaturas, mas também métodos que retornam que mais derivado tipos \(covariância\) ou que aceita parâmetros que têm menos tipos derivados \(contravariância\) que o especificado pelo tipo de delegado. Para obter mais informações, consulte [Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variação em delegações \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra a covariância e contravariância suportam para grupos de método.  
  
```c#  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 No .NET Framework 4 ou mais recente c\# oferece suporte a covariância e contravariância em interfaces e delegados genéricos e permite a conversão implícita de parâmetros de tipo genérico. Para obter mais informações, consulte [Variação em Interfaces genéricas \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) e [Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.  
  
```c#  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Uma interface genérica ou representante é chamado *variante* se seus parâmetros genéricos são declarados covariantes ou contravariant. C\# permite que você crie suas próprias interfaces variantes e delegados. Para obter mais informações, consulte [Criando Interfaces genéricas variantes \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) e [Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## Tópicos relacionados  
  
|Título|Descrição|  
|------------|---------------|  
|[Variação em Interfaces genéricas \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Discute a covariância e contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.|  
|[Criando Interfaces genéricas variantes \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Mostra como criar interfaces variantes personalizados.|  
|[Usando variação em Interfaces para coleções genéricas \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Mostra como suportam a covariância e contravariância no <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601> interfaces podem ajudá\-lo a reutilizar o código.|  
|[Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Discute a covariância e contravariância genérica e não genérica delegados e fornece uma lista de variantes delegados genéricos no .NET Framework.|  
|[Usando variação em delegações \(c\#\)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Mostra como usar o suporte a covariância e contravariância delegados não genérico para corresponder assinaturas de método com tipos delegados.|  
|[Usando variação para delegações Func e Action genéricas \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Mostra como suportam a covariância e contravariância no `Func` e `Action` delegados podem ajudá\-lo a reutilizar o código.|