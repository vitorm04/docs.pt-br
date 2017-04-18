---
title: "Funções matemáticas (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2b4db2bfe5e31774452a585b395f655720ad5449
ms.lasthandoff: 03/13/2017

---
# <a name="math-functions-visual-basic"></a>Funções matemáticas (Visual Basic)
Os métodos de <xref:System.Math?displayProperty=fullName>classe fornecer trigonométricas, logarítmicas e outras funções matemáticas comuns.</xref:System.Math?displayProperty=fullName>  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir lista os métodos para a <xref:System.Math?displayProperty=fullName>classe.</xref:System.Math?displayProperty=fullName> Você pode usá-los em um programa do Visual Basic.  
  
|Método do .NET framework|Descrição|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A></xref:System.Math.Abs%2A>|Retorna o valor absoluto de um número.|  
|<xref:System.Math.Acos%2A></xref:System.Math.Acos%2A>|Retorna o ângulo cujo cosseno é o número especificado.|  
|<xref:System.Math.Asin%2A></xref:System.Math.Asin%2A>|Retorna o ângulo cujo seno é o número especificado.|  
|<xref:System.Math.Atan%2A></xref:System.Math.Atan%2A>|Retorna o ângulo cuja tangente é o número especificado.|  
|<xref:System.Math.Atan2%2A></xref:System.Math.Atan2%2A>|Retorna o ângulo cuja tangente é o quociente de dois números especificados.|  
|<xref:System.Math.BigMul%2A></xref:System.Math.BigMul%2A>|Retorna o produto completo de dois números de 32 bits.|  
|<xref:System.Math.Ceiling%2A></xref:System.Math.Ceiling%2A>|Retorna o menor valor integral que é maior que ou igual a especificado `Decimal` ou `Double`.|  
|<xref:System.Math.Cos%2A></xref:System.Math.Cos%2A>|Retorna o cosseno do ângulo especificado.|  
|<xref:System.Math.Cosh%2A></xref:System.Math.Cosh%2A>|Retorna o cosseno hiperbólico do ângulo especificado.|  
|<xref:System.Math.DivRem%2A></xref:System.Math.DivRem%2A>|Retorna o quociente de dois inteiros de 32 bits ou 64 bits assinados e também retorna o resto em um parâmetro de saída.|  
|<xref:System.Math.Exp%2A></xref:System.Math.Exp%2A>|Retorna e (a base dos logaritmos naturais) elevado à potência especificada.|  
|<xref:System.Math.Floor%2A></xref:System.Math.Floor%2A>|Retorna o maior inteiro menor ou igual a especificado `Decimal` ou `Double` número.|  
|<xref:System.Math.IEEERemainder%2A></xref:System.Math.IEEERemainder%2A>|Retorna o resto que resulta da divisão de um número especificado por outro número especificado.|  
|<xref:System.Math.Log%2A></xref:System.Math.Log%2A>|Retorna o logaritmo natural (base e) de um número especificado ou o logaritmo de um número especificado em uma base especificada.|  
|<xref:System.Math.Log10%2A></xref:System.Math.Log10%2A>|Retorna o logaritmo de base 10 de um número especificado.|  
|<xref:System.Math.Max%2A></xref:System.Math.Max%2A>|Retorna o maior dos dois números.|  
|<xref:System.Math.Min%2A></xref:System.Math.Min%2A>|Retorna o menor dos dois números.|  
|<xref:System.Math.Pow%2A></xref:System.Math.Pow%2A>|Retorna um número especificado elevado à potência especificada.|  
|<xref:System.Math.Round%2A></xref:System.Math.Round%2A>|Retorna um `Decimal` ou `Double` valor arredondado para o valor inteiro mais próximo ou para um número especificado de dígitos fracionários.|  
|<xref:System.Math.Sign%2A></xref:System.Math.Sign%2A>|Retorna um `Integer` valor que indica o sinal de um número.|  
|<xref:System.Math.Sin%2A></xref:System.Math.Sin%2A>|Retorna o seno do ângulo especificado.|  
|<xref:System.Math.Sinh%2A></xref:System.Math.Sinh%2A>|Retorna o seno hiperbólico do ângulo especificado.|  
|<xref:System.Math.Sqrt%2A></xref:System.Math.Sqrt%2A>|Retorna a raiz quadrada de um número especificado.|  
|<xref:System.Math.Tan%2A></xref:System.Math.Tan%2A>|Retorna a tangente do ângulo especificado.|  
|<xref:System.Math.Tanh%2A></xref:System.Math.Tanh%2A>|Retorna a tangente hiperbólica do ângulo especificado.|  
|<xref:System.Math.Truncate%2A></xref:System.Math.Truncate%2A>|Calcula a parte integral do especificada `Decimal` ou `Double` número.|  
  
 Para usar estas funções sem restrições, importe o <xref:System.Math?displayProperty=fullName>namespace em seu projeto, adicionando o seguinte código à parte superior do seu arquivo de origem:</xref:System.Math?displayProperty=fullName>  
  
```  
Imports System.Math  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Abs%2A>método o <xref:System.Math>classe para calcular o valor absoluto de um número.</xref:System.Math> </xref:System.Math.Abs%2A>  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Atan%2A>método o <xref:System.Math>classe para calcular o valor de pi.</xref:System.Math> </xref:System.Math.Atan%2A>  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Cos%2A>método o <xref:System.Math>classe para retornar o cosseno de um ângulo.</xref:System.Math> </xref:System.Math.Cos%2A>  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Exp%2A>método o <xref:System.Math>classe para retornar e elevado a uma potência.</xref:System.Math> </xref:System.Math.Exp%2A>  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Log%2A>método o <xref:System.Math>classe para retornar o logaritmo natural de um número.</xref:System.Math> </xref:System.Math.Log%2A>  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Round%2A>método o <xref:System.Math>classe para arredondar um número para o inteiro mais próximo.</xref:System.Math> </xref:System.Math.Round%2A>  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Sign%2A>método o <xref:System.Math>classe para determinar o sinal de um número.</xref:System.Math> </xref:System.Math.Sign%2A>  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Sin%2A>método o <xref:System.Math>classe para retornar o seno de um ângulo.</xref:System.Math> </xref:System.Math.Sin%2A>  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Sqrt%2A>método o <xref:System.Math>classe para calcular a raiz quadrada de um número.</xref:System.Math> </xref:System.Math.Sqrt%2A>  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Math.Tan%2A>método o <xref:System.Math>classe para retornar a tangente de um ângulo.</xref:System.Math> </xref:System.Math.Tan%2A>  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Requisitos  
 **Classe:**<xref:System.Math></xref:System.Math>  
  
 **Namespace:**<xref:System></xref:System>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A></xref:Microsoft.VisualBasic.VBMath.Rnd%2A>   
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A></xref:Microsoft.VisualBasic.VBMath.Randomize%2A>   
 <xref:System.Double.NaN></xref:System.Double.NaN>   
 [Funções matemáticas derivadas](../../../visual-basic/language-reference/keywords/derived-math-functions.md)   
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
