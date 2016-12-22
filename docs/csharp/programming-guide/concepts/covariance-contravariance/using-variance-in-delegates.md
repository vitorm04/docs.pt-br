---
title: "Usando varia&#231;&#227;o em delega&#231;&#245;es (c#) | Microsoft Docs"
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
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando varia&#231;&#227;o em delega&#231;&#245;es (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você atribui um método a um delegado, *covariância* e *contravariância* fornecem flexibilidade para corresponder a um tipo de delegado com uma assinatura de método. Covariância permite que um método para ter o tipo de retorno que seja mais derivado daquele definido no delegado. Contravariância permite que um método que possui tipos de parâmetro que são menos derivados no tipo delegado.  
  
## Exemplo 1: covariância  
  
### Descrição  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado. O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva de `Mammals` tipo definido no delegado.  
  
### Código  
  
```c#  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## Exemplo 2: contravariância  
  
### Descrição  
 Este exemplo demonstra como delegados podem ser usados com métodos que têm parâmetros de um tipo que são tipos base do tipo de parâmetro de assinatura do delegado. Com contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados. Por exemplo, você pode criar um manipulador de eventos que aceita um `EventArgs` parâmetro de entrada e usá\-la com um `Button.MouseClick` eventos que envia um `MouseEventArgs` tipo como um parâmetro e também com um `TextBox.KeyDown` eventos que envia um `KeyEventArgs` parâmetro.  
  
### Código  
  
```c#  
// Event hander that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## Consulte também  
 [Variação em delegações \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)   
 [Usando variação para delegações Func e Action genéricas \(c\#\)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)