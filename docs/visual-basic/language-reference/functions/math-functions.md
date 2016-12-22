---
title: "Fun&#231;&#245;es matem&#225;ticas (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "funções matemáticas, Visual Basic"
  - "operações aritméticas, funções matemáticas"
  - "rotinas de matemática"
  - "Função Atn"
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#245;es matem&#225;ticas (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os métodos da classe de <xref:System.Math?displayProperty=fullName> fornecem funções matemáticas trigonométricas, logarítmicas, e outras comuns.  
  
## Comentários  
 A tabela a seguir lista os métodos da classe de <xref:System.Math?displayProperty=fullName> .  Você pode usar esses em um programa em Visual Basic.  
  
|método do Framework .NET.|Descrição|  
|-------------------------------|---------------|  
|<xref:System.Math.Abs%2A>|Retorna o valor absoluto de um número.|  
|<xref:System.Math.Acos%2A>|Retorna o ângulo cuja o cosseno é o número especificado.|  
|<xref:System.Math.Asin%2A>|Retorna o ângulo cuja o seno é o número especificado.|  
|<xref:System.Math.Atan%2A>|Retorna o ângulo cuja tangente é o número especificado.|  
|<xref:System.Math.Atan2%2A>|Retorna o ângulo cuja tangente é o quociente de dois números especificados.|  
|<xref:System.Math.BigMul%2A>|Retorna o produto completo de dois números de 32 bits.|  
|<xref:System.Math.Ceiling%2A>|Retorna o valor integral o menor que é maior ou igual a `Decimal` especificado ou `Double`.|  
|<xref:System.Math.Cos%2A>|Retorna o cosseno do ângulo especificado.|  
|<xref:System.Math.Cosh%2A>|Retorna o cosseno hiperbólico do ângulo especificado.|  
|<xref:System.Math.DivRem%2A>|Retorna o quociente de dois de 32 bits ou de números inteiros de 64 bits com sinal, e também retorna o restante em um parâmetro de saída.|  
|<xref:System.Math.Exp%2A>|Retorna e \(a base dos logaritmos naturais\) elevado à potência especificada.|  
|<xref:System.Math.Floor%2A>|Retorna o número inteiro maior que é menor ou igual a `Decimal` ou número especificado de `Double` .|  
|<xref:System.Math.IEEERemainder%2A>|Retorna o resto que resulta da divisão de um número especificado por outro número especificado.|  
|<xref:System.Math.Log%2A>|Retorna \(o logaritmo natural de ebase\) de um número especificado como o de um número especificado em uma base.|  
|<xref:System.Math.Log10%2A>|Retorna o logaritmo de base 10 de um número especificado.|  
|<xref:System.Math.Max%2A>|Retorna o mais de dois números.|  
|<xref:System.Math.Min%2A>|Retorna o menor de dois números.|  
|<xref:System.Math.Pow%2A>|Retorna um número especificado gerado à potência especificada.|  
|<xref:System.Math.Round%2A>|Retorna um valor de `Decimal` ou de `Double` arredondado para o valor inteiro mais próximo ou a um número especificado de caracteres de dígitos.|  
|<xref:System.Math.Sign%2A>|Retorna um valor `Integer` indicando o sinal de um número.|  
|<xref:System.Math.Sin%2A>|Retorna o seno de um ângulo especificado.|  
|<xref:System.Math.Sinh%2A>|Retorna o seno hiperbólico do ângulo especificado.|  
|<xref:System.Math.Sqrt%2A>|Retorna a raiz quadrada de um número especificado.|  
|<xref:System.Math.Tan%2A>|Retorna a tangente de um ângulo especificado.|  
|<xref:System.Math.Tanh%2A>|Retorna a tangente hiperbólica do ângulo especificado.|  
|<xref:System.Math.Truncate%2A>|Calcula a parte integral de `Decimal` ou um número especificado de `Double` .|  
  
 Para usar essas funções sem qualificação, importar o namespace de <xref:System.Math?displayProperty=fullName> em seu projeto adicionando o seguinte código à parte superior do arquivo de origem:  
  
```  
Imports System.Math  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Abs%2A> da classe <xref:System.Math> para calcular o valor absoluto de um número.  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Atan%2A> da classe <xref:System.Math> para calcular o valor de pi.  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Cos%2A> da classe <xref:System.Math> para retornar o cosseno de um ângulo.  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Exp%2A> da classe <xref:System.Math> para retornar e elevado a um expoente.  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Log%2A> da classe <xref:System.Math> para retornar o logaritmo natural de um número.  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Round%2A> da classe <xref:System.Math> para arredondar um número para o inteiro mais próximo.  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Sign%2A> da classe <xref:System.Math> para determinar o sinal de um número.  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Sin%2A> da classe <xref:System.Math> para retornar o seno de um ângulo.  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Sqrt%2A> da classe <xref:System.Math> para calcular a raiz quadrada de um número.  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## Exemplo  
 Este exemplo usa o método <xref:System.Math.Tan%2A> da classe <xref:System.Math> para retornar a tangente de um ângulo.  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## Requisitos  
 **Classe:** <xref:System.Math>  
  
 **Namespace** <xref:System>  
  
 **Assembly:** mscorlib \(in mscorlib.dll\)  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>   
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>   
 <xref:System.Double.NaN>   
 [Funções matemáticas derivadas](../../../visual-basic/language-reference/keywords/derived-math-functions.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)