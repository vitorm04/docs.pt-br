---
title: "Como definir e usar provedores de formatos numéricos personalizados"
description: "Como definir e usar provedores de formatos numéricos personalizados"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9b184114-6612-4c1a-a2db-2e24e65b0f77
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fdea0fe76b1c5f1e9ae23582219c847fe80b317f
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Como definir e usar provedores de formatos numéricos personalizados

O .NET oferece controle abrangente sobre a representação de cadeias de caracteres de valores numéricos. Ele dá suporte aos seguintes recursos para personalizar o formato de valores numéricos:

* Cadeias de caracteres de formato numérico padrão, que fornecem um conjunto predefinido de formatos para converter números para suas representações de cadeia de caracteres. Você pode usá-las com qualquer método de formatação numérica, como [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)), que tem um parâmetro de formato. Para obter detalhes, consulte [Cadeias de caracteres de formato numérico padrão](standard-numeric.md).

* Cadeias de caracteres de formato numérico personalizado, que fornecem um conjunto de símbolos que podem ser combinados para definir especificadores de formato numérico personalizado. Eles também podem ser usados com qualquer método de formatação numérica, como [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)), que tem um parâmetro de formato. Para obter detalhes, consulte [Cadeias de caracteres de formato numérico personalizado](custom-numeric.md).

* Objetos [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) personalizados, que definem os símbolos e padrões de formato usados para exibir as representações de cadeia de caracteres de valores numéricos. Você pode usá-las com qualquer método de formatação numérica, como [ToString](xref:System.Int32.ToString(System.IFormatProvider)), que tem um parâmetro *provider*. Normalmente, o parâmetro *provider* é usado para especificar a formatação específica à cultura.

Em alguns casos (como quando um aplicativo deve exibir um número de conta formatado, um número de identificação ou um código postal) essas três técnicas são inadequadas. O .NET também permite que você defina um objeto de formatação que não é um objeto [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para determinar como um valor numérico é formatado. Este tópico fornece informações passo a passo para implementar esse tipo de objeto, bem como um exemplo que formata números de telefone.

## <a name="to-define-a-custom-format-provider"></a>Para definir um provedor de formato personalizado

1. Defina uma classe que implementa as interfaces [IFormatProvider](xref:System.IFormatProvider) e [ICustomFormatter](xref:System.ICustomFormatter). 

2. Implemente o método [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) é um método de retorno de chamada que o método de formatação (como o método [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))) invoca para recuperar o objeto que é o responsável por executar a formatação personalizada. Uma implementação típica de [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) faz o seguinte:

    a. Determina se o objeto [Type](xref:System.Type) passado como método de parâmetro representa uma interface [ICustomFormatter](xref:System.ICustomFormatter).
    
    b. Se o parâmetro representar a interface [ICustomFormatter](xref:System.ICustomFormatter), [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna um objeto que implementa a interface [ICustomFormatter](xref:System.ICustomFormatter) que é responsável por fornecer a formatação personalizada. Normalmente, o objeto de formatação personalizado retorna a si próprio. 
    
    c. Se o parâmetro não representar a interface [ICustomFormatter](xref:System.ICustomFormatter), [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna `null`.
    
3. Implementar o método [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)). Este método é chamado elo método [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) e é responsável por retornar a representação de cadeia de caracteres de um número. Implementar o método normalmente envolve o seguinte:

    a. Opcionalmente, verifique se o método é legitimamente destinado a fornecer serviços de formatação examinando o parâmetro *provider*. Para formatar objetos que implementam [IFormatProvider](xref:System.IFormatProvider) e [ICustomFormatter](xref:System.ICustomFormatter), isso envolve testar o parâmetro *provider* para igualdade com o objeto de formatação atual.
    
    b. Determine se o objeto de formatação deve dar suporte a especificadores de formato personalizado. (Por exemplo, um especificador de formato "N" pode indicar que um número de telefone dos EUA deve ser gerado no formato NANP e um "I" pode indicar a saída no formato E.&123; da Recomendação ITU-T.) Se especificadores de formato forem usados, o método deve tratar o especificador de formato específico. Ele é passado para o método no parâmetro de formato. Se nenhum especificador estiver presente, o valor do parâmetro *format* será [String.Empty](xref:System.String#System_String_Empty).
    
    c. Recupere o valor numérico passado para o método como o parâmetro *arg*. Execute as manipulações que forem necessárias para convertê-lo em sua representação de cadeia de caracteres.
    
    d. Retorne a representação de cadeia de caracteres do parâmetro *arg*.
    
## <a name="to-use-a-custom-numeric-formatting-object"></a>Para usar um objeto de formatação numérico personalizado

1. Crie uma nova instância da classe de formatação personalizada.

2. Chame o método de formatação [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) passando a ele o objeto de formatação personalizado, o especificador de formatação (ou [String.Empty](xref:System.String.Empty), se um não for usado) e o valor numérico a ser formatado. 

## <a name="example"></a>Exemplo

O exemplo a seguir define um provedor de formato numérico personalizado chamado `TelephoneFormatter`, que converte um número que representa um número de telefone dos EUA para seu formato NANP ou E.123. O método lida com dois especificadores de formato, "N" (que gera o formato NANP) e "I" (que gera o formato internacional E.123).

```csharp
using System;
using System.Globalization;

public class TelephoneFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   {
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }               

   public string Format(string format, object arg, IFormatProvider formatProvider)
   {
      // Check whether this is an appropriate callback             
      if (! this.Equals(formatProvider))
         return null; 

      // Set default format specifier             
      if (string.IsNullOrEmpty(format)) 
         format = "N";

      string numericString = arg.ToString();

      if (format == "N")
      {
         if (numericString.Length <= 4)
            return numericString;
         else if (numericString.Length == 7)
            return numericString.Substring(0, 3) + "-" + numericString.Substring(3, 4); 
         else if (numericString.Length == 10)
               return "(" + numericString.Substring(0, 3) + ") " +
                      numericString.Substring(3, 3) + "-" + numericString.Substring(6);   
         else
            throw new FormatException( 
                      string.Format("'{0}' cannot be used to format {1}.", 
                                    format, arg.ToString()));
      }
      else if (format == "I")
      {
         if (numericString.Length < 10)
            throw new FormatException(string.Format("{0} does not have 10 digits.", arg.ToString()));
         else
            numericString = "+1 " + numericString.Substring(0, 3) + " " + numericString.Substring(3, 3) + " " + numericString.Substring(6);
      }
      else
      {
         throw new FormatException(string.Format("The {0} format specifier is invalid.", format));
      } 
      return numericString;  
   }
}

public class TestTelephoneFormatter
{
   public static void Main()
   {
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:I}", 4257884748));
   }
}
```

```vb
Public Class TelephoneFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If               
   End Function               

   Public Function Format(fmt As String, arg As Object, _
                          formatProvider As IFormatProvider) As String _
                   Implements ICustomFormatter.Format
      ' Check whether this is an appropriate callback             
      If Not Me.Equals(formatProvider) Then Return Nothing 

      ' Set default format specifier             
      If String.IsNullOrEmpty(fmt) Then fmt = "N"

      Dim numericString As String = arg.ToString

      If fmt = "N" Then
         Select Case numericString.Length
            Case <= 4 
               Return numericString
            Case 7
               Return Left(numericString, 3) & "-" & Mid(numericString, 4) 
            Case 10
               Return "(" & Left(numericString, 3) & ") " & _
                      Mid(numericString, 4, 3) & "-" & Mid(numericString, 7)   
            Case Else
               Throw New FormatException( _
                         String.Format("'{0}' cannot be used to format {1}.", _
                                       fmt, arg.ToString()))
         End Select
      ElseIf fmt = "I" Then
         If numericString.Length < 10 Then
            Throw New FormatException(String.Format("{0} does not have 10 digits.", arg.ToString()))
         Else
            numericString = "+1 " & Left(numericString, 3) & " " & Mid(numericString, 4, 3) & " " & Mid(numericString, 7)
         End If      
      Else
         Throw New FormatException(String.Format("The {0} format specifier is invalid.", fmt))
      End If 
      Return numericString  
   End Function
End Class

Public Module TestTelephoneFormatter
   Public Sub Main
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:I}", 4257884748))
   End Sub
End Module
```

O provedor de formato numérico personalizado pode ser usado apenas com o método [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). As outras sobrecargas de métodos de formatação numérica (como `ToString`) que têm um parâmetro do tipo [IFormatProvider](xref:System.IFormatProvider) passam para a implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) um objeto [Type](xref:System.Type) que representa o tipo [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo). Por sua vez, eles esperam que o método retorne um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo). Se isso não acontecer, o provedor de formato numérico personalizado será ignorado e o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) da cultura atual será usada em seu lugar. No exemplo, o método `TelephoneFormatter.GetFormat` trata da possibilidade de ele ser passado inadequadamente para um método de formatação numérico examinando o parâmetro do método e retornando *null* se ele representar um tipo diferente de [ICustomFormatter](xref:System.ICustomFormatter).

Se um provedor de formato numérico personalizado der suporte a um conjunto de especificadores de formato, forneça um comportamento padrão se nenhum especificador de formato for fornecido no item de formato usado na chamada de método [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). No exemplo, "N" é o especificador de formato padrão. Isso permite que um número a ser convertido em um número de telefone formatado, fornecendo um especificador de formato explícito. O exemplo a seguir ilustra essa chamada de método.

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))
```

Mas também permite que a conversão ocorra se nenhum especificador de formato estiver presente. O exemplo a seguir ilustra essa chamada de método.

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))
```

Se nenhum especificador de formato padrão for definido, sua implementação do método [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) deve incluir código como o seguinte para que o .NET possa fornecer a formatação a que seu código não dá suporte.

```csharp
if (arg is IFormattable) 
   s = ((IFormattable)arg).ToString(format, formatProvider);
else if (arg != null)    
   s = arg.ToString();
```

```vb
If TypeOf(arg) Is IFormattable Then 
   s = DirectCast(arg, IFormattable).ToString(fmt, formatProvider)
ElseIf arg IsNot Nothing Then    
   s = arg.ToString()
End If
```

No caso deste exemplo, o método que implementa [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) se destina a servir como um método de retorno de chamada para o método [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Portanto, ele examina o parâmetro *formatProvider* para determinar se ele contém uma referência ao objeto `TelephoneFormatter` atual. No entanto, o método também pode ser chamado diretamente do código. Nesse caso, você pode usar o parâmetro *formatProvider *para fornecer um objeto [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que fornece informações de formatação específicas da cultura.

## <a name="see-also"></a>Consulte também

[Executando operações de formatação](performing-formatting-operations.md)

