---
title: Usando objetos que implementam IDisposable
description: Usando objetos que implementam IDisposable
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: df780a6e-734e-44b8-9747-9f7783f79e20
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 42b82c6a906a803b45976c01a55e585cd3b7542f

---

# <a name="using-objects-that-implement-idisposable"></a>Usando objetos que implementam IDisposable

O coletor de lixo do Common Language Runtime recupera a memória usada por objetos não gerenciados, mas os tipos que usam recursos não gerenciados implementam a interface [IDisposable](xref:System.IDisposable) para permitir que essa memória não gerenciada seja recuperada. Após terminar de usar um objeto que implementa a [IDisposable](xref:System.IDisposable), você deverá chamar a implementação de [IDisposable.Dispose](xref:System.IDisposable.Dispose) do objeto. Você pode fazer isso de duas maneiras:

* Com a instrução `using` do C# ou a instrução `Using` do Visual Basic.

* Implementando um bloco `try/finally`. 

## <a name="the-using-statement"></a>A instrução using

A instrução `using` no C# e a instrução `Using` no Visual Basic simplificam o código que você deve escrever para criar e limpar um objeto. A instrução `using` obtém um ou mais recursos, executa as instruções que você especifica e descarta o objeto automaticamente. Entretanto, a instrução `using` é útil apenas para os objetos que são usados no escopo do método no qual eles são criados. 

O exemplo a seguir usa a instrução `using` para criar e liberar um objeto [System.IO.StreamReader](xref:System.IO.StreamReader).

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      using (StreamReader s = new StreamReader("File1.txt")) {
         int charsRead = 0;
         while (s.Peek() != -1) {
            charsRead = s.Read(buffer, 0, buffer.Length);
            //
            // Process characters read.
            //   
         }
         s.Close();    
      }

   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
      Using s As New StreamReader("File1.txt")
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      End Using
   End Sub
End Module
```

Observe que, embora a classe [StreamReader](xref:System.IO.StreamReader) implemente a interface [IDisposable](xref:System.IDisposable), o que indica que ela usa um recurso não gerenciado, o exemplo não chama explicitamente o método [StreamReader.Dispose](xref:System.IO.StreamReader.Dispose(System.Boolean)). Quando o compilador do C# ou do Visual Basic encontra a instrução `using`, ele emite a IL (linguagem intermediária) que equivale ao seguinte código que contém explicitamente um bloco `try/finally`. 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      {
         StreamReader s = new StreamReader("File1.txt"); 
         try {
            int charsRead = 0;
            while (s.Peek() != -1) {
               charsRead = s.Read(buffer, 0, buffer.Length);
               //
               // Process characters read.
               //   
            }
            s.Close();
         }
         finally {
            if (s != null)
               ((IDisposable)s).Dispose();     
         }       
      }
   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
''      Dim s As New StreamReader("File1.txt")
With s As New StreamReader("File1.txt")
      Try
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      Finally
         If s IsNot Nothing Then DirectCast(s, IDisposable).Dispose()
      End Try
End With
   End Sub
End Module
```

A instrução `using` do C# também permite que você adquira vários recursos em uma única instrução, o que é internamente equivalente a instruções using aninhadas. O exemplo a seguir cria instancia dois objetos [StreamReader](xref:System.IO.StreamReader) para ler o conteúdo de dois arquivos diferentes. 

```cs
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer1 = new Char[50], buffer2 = new Char[50];

      using (StreamReader version1 = new StreamReader("file1.txt"),
                          version2 = new StreamReader("file2.txt")) {
         int charsRead1, charsRead2 = 0;
         while (version1.Peek() != -1 && version2.Peek() != -1) {
            charsRead1 = version1.Read(buffer1, 0, buffer1.Length);
            charsRead2 = version2.Read(buffer2, 0, buffer2.Length);
            //
            // Process characters read.
            //
         }
         version1.Close();
         version2.Close();
      }
   }
}
```

## <a name="tryfinally-block"></a>Bloco Try/finally

Em vez de incluir um bloco `try/finally` em uma instrução `using`, você pode optar por implementar diretamente o bloco `try/finally`. Esse pode ser o estilo pessoal de codificação ou talvez você queira fazer isso por um dos seguintes motivos: 

* Para incluir um bloco `catch` para lidar com algumas exceções geradas no bloco `try`. Caso contrário, todas as exceções geradas pela instrução `using` não são manipuladas, assim como em quaisquer exceções geradas dentro do bloco `using` se um bloco `try/catch` não estiver presente. 

* Para criar uma instância de um objeto que implementa [IDisposable](xref:System.IDisposable) cujo escopo não é local para o bloco dentro do qual é declarado. 

O exemplo a seguir é semelhante ao anterior, exceto que ele usa um bloco `try/catch/finally` para criar uma instância, usar e descartar um objeto [StreamReader](xref:System.IO.StreamReader) e também para manipular todas as exceções lançadas pelo construtor [StreamReader](xref:System.IO.StreamReader) e pelo método [ReadToEnd](xref:System.IO.StreamReader.ReadToEnd). Observe que o código no bloco `finally` verifica se o objeto que implementa [IDisposable](xref:System.IDisposable) não é `null` antes de chamar o método [Dispose](xref:System.IDisposable.Dispose). Não fazer isso poderá levar a uma exceção [NullReferenceException](xref:System.NullReferenceException) no tempo de execução. 

```cs
using System;
using System.Globalization;
using System.IO;

public class Example
{
   public static void Main()
   {
      StreamReader sr = null;
      try {
         sr = new StreamReader("file1.txt");
         String contents = sr.ReadToEnd();
         sr.Close();
         Console.WriteLine("The file has {0} text elements.", 
                           new StringInfo(contents).LengthInTextElements);    
      }      
      catch (FileNotFoundException) {
         Console.WriteLine("The file cannot be found.");
      }   
      catch (IOException) {
         Console.WriteLine("An I/O error has occurred.");
      }
      catch (OutOfMemoryException) {
         Console.WriteLine("There is insufficient memory to read the file.");   
      }
      finally {
         if (sr != null) sr.Dispose();     
      }
   }
}
```

```vb
Imports System.Globalization
Imports System.IO

Module Example
   Public Sub Main()
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader("file1.txt")
         Dim contents As String = sr.ReadToEnd()
         sr.Close()
         Console.WriteLine("The file has {0} text elements.", 
                           New StringInfo(contents).LengthInTextElements)    
      Catch e As FileNotFoundException
         Console.WriteLine("The file cannot be found.")
      Catch e As IOException
         Console.WriteLine("An I/O error has occurred.")
      Catch e As OutOfMemoryException
         Console.WriteLine("There is insufficient memory to read the file.")   
      Finally 
         If sr IsNot Nothing Then sr.Dispose()     
      End Try
   End Sub
End Module
```

Você poderá seguir esse padrão básico se optar por implementar ou precisar implementar um bloco `try/finally`, pois a linguagem de programação não dá suporte a uma instrução `using`, mas permite chamadas diretas para o método [Dispose](xref:System.IDisposable.Dispose). 

## <a name="see-also"></a>Consulte também

[Limpando recursos não gerenciados](unmanaged.md)





<!--HONumber=Nov16_HO3-->


