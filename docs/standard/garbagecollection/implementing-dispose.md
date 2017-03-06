---
title: "Implementando um método Dispose"
description: "Implementando um método Dispose"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: eca6cdc3-6a14-4296-86fb-1eb2f21455b0
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: fcb7944a7a9cce1cf23b42790133ee051c0e05f0

---

# <a name="implementing-a-dispose-method"></a>Implementando um método Dispose

Você implementa um método [Dispose](xref:System.IDisposable.Dispose) para liberar recursos não gerenciados usados pelo seu aplicativo. O coletor de lixo .NET não alocar nem libera memória não gerenciada. 

O padrão para o descarte um objeto, conhecido como padrão Dispose, impõe ordem no tempo de vida de um objeto. O padrão de descarte é usado somente para os objetos que acessam recursos não gerenciados, como identificadores de arquivo e pipe, identificadores de Registro, identificadores de espera ou ponteiros para blocos de memória não gerenciada. Isso ocorre porque o coletor de lixo é muito eficiente para recuperar objetos gerenciados não usados, mas não é capaz de recuperar objetos não gerenciados.

O padrão de descarte tem duas variações:

* Você encapsula cada recurso não gerenciado usado por um tipo em um identificador seguro (ou seja, em uma classe derivada de [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)). Nesse caso, você implementa a interface [IDisposable](xref:System.IDisposable) e um método `Dispose(Boolean)` adicional. Essa é a variação recomendada e não requer a substituição do método [Object.Finalize](xref:System.Object.Finalize). 

> [!NOTE]
> O namespace [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) fornece um conjunto de classes derivadas de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle), que são listadas na seção [Usando identificadores seguros](#using-safe-handles). Se não conseguir encontrar uma classe adequada para liberar seu recurso não gerenciado, você poderá implementar sua própria subclasse de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle). 
 
* Você implementa a interface [IDisposable](xref:System.IDisposable) e um método `Dispose(Boolean`) adicional, além de substituir o método [Object.Finalize](xref:System.Object.Finalize). Você deve substituir [Finalize](xref:System.Object.Finalize) para garantir que os recursos não gerenciados sejam descartados se sua implementação de [IDisposable.Dispose](xref:System.IDisposable.Dispose) não for chamada por um consumidor do seu tipo. Se você usar a técnica recomendada discutida no item anterior, a classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) fará isso em seu nome. 

Para ajudar a garantir que os recursos sejam sempre limpos corretamente, um método [Dispose](xref:System.IDisposable.Dispose) deve poder ser chamado várias vezes sem gerar uma exceção. 

O exemplo de código fornecido para o método [GC.KeepAlive](xref:System.GC.KeepAlive(System.Object)) mostra a agressividade com a qual uma coleta de lixo pode fazer com que um finalizador seja executado enquanto um membro do objeto recuperado ainda está em execução. É uma boa ideia chamar o método [KeepAlive](xref:System.GC.KeepAlive(System.Object)) no final de um método `Dispose` longo.

## <a name="dispose-and-disposeboolean"></a>Dispose() e Dispose(Boolean)

A interface [IDisposable](xref:System.IDisposable) requer a implementação de um único método sem parâmetros, [Dispose](xref:System.IDisposable.Dispose). No entanto, o padrão de descarte requer que dois métodos `Dispose` sejam implementados: 

* Uma implementação pública não virtual (`NonInheritable` no Visual Basic) de [IDisposable.Dispose](xref:System.IDisposable.Dispose) que não tem parâmetros.

* Um método `Overridable` virtual protegido (`Dispose` no Visual Basic) cuja assinatura é:

  ```cs
  protected virtual void Dispose(bool disposing)
  ```

  ```vb
  Protected Overridable Sub Dispose(disposing As Boolean)
  ```

### <a name="the-dispose-overload"></a>A sobrecarga Dispose()

Como o método público, não virtual (`NonInheritable` no Visual Basic) e sem parâmetro `Dispose` é chamado por um consumidor do tipo, sua finalidade é liberar recursos não gerenciados e indicar que o finalizador, se houver um, não precisa ser executado. Por isso, ele tem uma implementação padrão:

```cs
public void Dispose()
{
   // Dispose of unmanaged resources.
   Dispose(true);
   // Suppress finalization.
   GC.SuppressFinalize(this);
}
```

```vb
Public Sub Dispose() _
           Implements IDisposable.Dispose
   ' Dispose of unmanaged resources.
   Dispose(True)
   ' Suppress finalization.
   GC.SuppressFinalize(Me)
End Sub
```

O método `Dispose` executa toda a limpeza do objeto, de modo que o coletor de lixo não precisa mais chamar a substituição dos objetos [Object.Finalize](xref:System.Object.Finalize). Assim, a chamada para o método [GC.SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) impede que o coletor de lixo execute o finalizador. Se o tipo não tiver um finalizador, a chamada para [SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) não terá efeito. Observe que o trabalho real de liberar recursos não gerenciado é executado pela segunda sobrecarga do método `Dispose`.

### <a name="the-disposeboolean-overload"></a>A sobrecarga Dispose(Boolean)

Na segunda sobrecarga, o parâmetro *disposing* é um [Booliano](xref:System.Boolean) que indica se a chamada do método é proveniente de um método [Dispose](xref:System.IDisposable.Dispose) (seu valor é `true`) ou de um finalizador (seu valor é `false`). 

O corpo do método consiste em dois blocos de código: 

* Um bloco que libera recursos não gerenciados. Este bloco é executado independentemente do valor do parâmetro *disposing*. 

* Um bloco condicional que libera recursos gerenciados. Este bloco será executado se o valor de *disposing* for `true`. Os recursos gerenciados que ele libera podem incluir: 

    **Objetos que implementam IDisposable**. O bloco condicional pode ser usado para chamar sua implementação de [Dispose](xref:System.IDisposable.Dispose). Se você usou um indicador seguro para encapsular o recurso não gerenciado, é necessário chamar a implementação de [SafeHandle.Dispose(Boolean](xref:System.Runtime.InteropServices.SafeHandle.Dispose(System.Boolean)) aqui. 

    **Objetos gerenciados que consomem muita memória ou consomem recursos escassos.** Liberar esses objetos explicitamente no método `Dispose` libera-os mais rápido do que se eles fossem recuperados de forma não determinística pelo coletor de lixo. 


Se a chamada do método vier de um finalizador (isto é, se *disposing* for `false`), somente o código que libera os recursos não gerenciados é executado. Como a ordem em que o coletor de lixo destrói objetos gerenciados durante a finalização não é definida, chamar essa sobrecarga `Dispose` com um valor de `false` impede que o finalizador tente liberar os recursos gerenciados que já podem ter sido recuperados. 

## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementando o padrão de descarte para uma classe base

Se você implementar o padrão de descarte para uma classe base, deverá fornecer o seguinte: 

> [!IMPORTANT]
> É preciso implementar esse padrão para todas as classes de base que implementam [IDisposable](xref:System.IDisposable) e não são `sealed`. 
 
* Uma implementação de [Dispose](xref:System.IDisposable.Dispose) que chame o método `Dispose(Boolean)`. 

* Um método `Dispose(Boolean)` que execute o trabalho real de liberar recursos. 

* Uma classe derivada de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) que envolva o recurso não gerenciado (recomendado) ou uma substituição para o método [Object.Finalize](xref:System.Object.Finalize). A classe [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)SafeHandle fornece um finalizador que liberta você da necessidade de codificar um. 

Aqui está o padrão geral para implementar o padrão de descarte para uma classe base que usa um identificador seguro. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub
End Class
```

> [!NOTE] 
> O exemplo anterior usa um objeto [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) para ilustrar o padrão; qualquer objeto derivado de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) poderia ser usado em seu lugar. Observe que o exemplo não cria corretamente uma instância do seu objeto [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle). 
 
Aqui está o padrão geral para implementar o padrão de descarte para uma classe base que substitui [Object.Finalize](xref:System.Object.Finalize). 

```cs
using System;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }

   ~BaseClass()
   {
      Dispose(false);
   }
}
```

```vb
Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)      
   End Sub
End Class
```

> [!NOTE]
> Em C#, você deve substituir [Object.Finalize](xref:System.Object.Finalize) definindo um `destructor`. 


## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementando o padrão de descarte para uma classe derivada

Uma classe derivada de uma classe que implementa a interface [IDisposable](xref:System.IDisposable) não deve implementar [IDisposable](xref:System.IDisposable) porque a implementação da classe base [IDisposable.Dispose](xref:System.IDisposable.Dispose) é herdada pelas classes derivadas. Em vez disso, para implementar o padrão de descarte para uma classe derivada, você deverá fornecer o seguinte: 

* Um método `protected Dispose(Boolean)` que substitua o método da classe base e execute o trabalho real de liberar os recursos da classe derivada. Esse método também deve chamar o método `Dispose(Boolean)` da classe base e passar para ele um valor de `true` para o argumento *disposing*. 

* Uma classe derivada de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) que envolva o recurso não gerenciado (recomendado) ou uma substituição para o método [Object.Finalize](xref:System.Object.Finalize). A classe [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) fornece um finalizador que liberta você da necessidade de codificar um. Se você fornecer um finalizador, ele deverá chamar a sobrecarga de `Dispose(Boolean)` com um argumento *disposing* de `false`. 

Aqui está o padrão geral para implementar o padrão de descarte para uma classe derivada que usa um identificador seguro: 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //

      disposed = true;
      // Call base class implementation.
      base.Dispose(disposing);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class DerivedClass : Inherits BaseClass 
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call base class implementation.
      MyBase.Dispose(disposing)
   End Sub
End Class
```

> [!NOTE] 
> O exemplo anterior usa um objeto [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) para ilustrar o padrão; qualquer objeto derivado de [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) poderia ser usado em seu lugar. Observe que o exemplo não cria corretamente uma instância do seu objeto [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle). 

Aqui está o padrão geral para implementar o padrão de descarte para uma classe derivada que substitui [Object.Finalize](xref:System.Object.Finalize):

```cs
using System;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;

      // Call the base class implementation.
      base.Dispose(disposing);
   }

   ~DerivedClass()
   {
      Dispose(false);
   }
}
```

```vb
Class DerivedClass : Inherits BaseClass
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call the base class implementation.
      MyBase.Dispose(disposing)
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)
   End Sub 
End Class
```

> [!NOTE]
> Em C#, você deve substituir [Object.Finalize](xref:System.Object.Finalize) definindo um `destructor`.

## <a name="using-safe-handles"></a>Usando identificadores seguros

Escrever código para o finalizador de um objeto é uma tarefa complexa que poderá causar problemas se não for feito corretamente. Assim, recomendamos que você construa objetos [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle), em vez de implementar um finalizador.

As classes derivadas da classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) simplificam problemas de tempo de vida do objeto ao atribuir e liberar identificadores sem interrupção. Elas contêm um finalizador crítico que certamente será executado enquanto um domínio de aplicativo estiver descarregando. As seguintes classes derivadas no namespace [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) fornecem os identificadores seguros: 

* A classe [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle), [SafeMemoryMappedFileHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle) e [SafePipeHandle](xref:Microsoft.Win32.SafeHandles.SafePipeHandle), para arquivos, arquivos mapeados na memória e pipes. 

* A classe [SafeMemoryMappedViewHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle), para exibições de memória. 

* As classes [SafeNCryptKeyHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptkeyhandle(v=vs.110).aspx), [SafeNCryptProviderHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptproviderhandle(v=vs.110).aspx) e [SafeNCryptSecretHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptsecrethandle(v=vs.110).aspx) para construtores de criptografia.

* A classe [SafeRegistryHandle](xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle), para chaves do Registro. 

* A classe [SafeWaitHandle](xref:Microsoft.Win32.SafeHandles.SafeWaitHandle), para identificadores de espera. 

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Usando um identificador seguro para implementar o padrão de descarte para uma classe base

O exemplo a seguir ilustra o padrão de descarte para uma classe base, `DisposableStreamResource`, a qual usa um identificador seguro para encapsular recursos não gerenciados. Define uma classe `DisposableResource` que usa um [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) para encapsular um objeto [Stream](xref:System.IO.Stream) que representa um arquivo aberto. O método `DisposableResource` também inclui uma única propriedade, `Size`, a qual retorna o número total de bytes no fluxo de arquivos. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;

public class DisposableStreamResource : IDisposable
{
   // Define constants.
   protected const uint GENERIC_READ = 0x80000000;
   protected const uint FILE_SHARE_READ = 0x00000001;
   protected const uint OPEN_EXISTING = 3;
   protected const uint FILE_ATTRIBUTE_NORMAL = 0x80;
   protected IntPtr INVALID_HANDLE_VALUE = new IntPtr(-1);
   private const int INVALID_FILE_SIZE = unchecked((int) 0xFFFFFFFF);

   // Define Windows APIs.
   [DllImport("kernel32.dll", EntryPoint = "CreateFileW", CharSet = CharSet.Unicode)]
   protected static extern IntPtr CreateFile (
                                  string lpFileName, uint dwDesiredAccess, 
                                  uint dwShareMode, IntPtr lpSecurityAttributes, 
                                  uint dwCreationDisposition, uint dwFlagsAndAttributes, 
                                  IntPtr hTemplateFile);

   [DllImport("kernel32.dll")]
   private static extern int GetFileSize(SafeFileHandle hFile, out int lpFileSizeHigh);

   // Define locals.
   private bool disposed = false;
   private SafeFileHandle safeHandle; 
   private long bufferSize;
   private int upperWord;

   public DisposableStreamResource(string filename)
   {
      if (filename == null)
         throw new ArgumentNullException("The filename cannot be null.");
      else if (filename == "")
         throw new ArgumentException("The filename cannot be an empty string.");

      IntPtr handle = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                 IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                 IntPtr.Zero);
      if (handle != INVALID_HANDLE_VALUE)
         safeHandle = new SafeFileHandle(handle, true);
      else
         throw new FileNotFoundException(String.Format("Cannot open '{0}'", filename));

      // Get file size.
      bufferSize = GetFileSize(safeHandle, out upperWord); 
      if (bufferSize == INVALID_FILE_SIZE)
         bufferSize = -1;
      else if (upperWord > 0) 
         bufferSize = (((long)upperWord) << 32) + bufferSize;
   }

   public long Size 
   { get { return bufferSize; } }

   public void Dispose()
   {
      Dispose(true);
      GC.SuppressFinalize(this);
   }           

   protected virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Dispose of managed resources here.
      if (disposing)
         safeHandle.Dispose();

      // Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = true;
   }  
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource : Implements IDisposable
   ' Define constants.
   Protected Const GENERIC_READ As UInteger = &H80000000ui
   Protected Const FILE_SHARE_READ As UInteger = &H0000000i
   Protected Const OPEN_EXISTING As UInteger = 3
   Protected Const FILE_ATTRIBUTE_NORMAL As UInteger = &H80
   Protected INVALID_HANDLE_VALUE As New IntPtr(-1)
   Private Const INVALID_FILE_SIZE As Integer = &HFFFFFFFF

   ' Define Windows APIs.
   Protected Declare Function CreateFile Lib "kernel32" Alias "CreateFileA" (
                                         lpFileName As String, dwDesiredAccess As UInt32, 
                                         dwShareMode As UInt32, lpSecurityAttributes As IntPtr, 
                                         dwCreationDisposition As UInt32, dwFlagsAndAttributes As UInt32, 
                                         hTemplateFile As IntPtr) As IntPtr
   Private Declare Function GetFileSize Lib "kernel32" (hFile As SafeFileHandle, 
                                                        ByRef lpFileSizeHigh As Integer) As Integer

   ' Define locals.
   Private disposed As Boolean = False
   Private safeHandle As SafeFileHandle 
   Private bufferSize As Long 
   Private upperWord As Integer

   Public Sub New(filename As String)
      If filename Is Nothing Then
         Throw New ArgumentNullException("The filename cannot be null.")
      Else If filename = ""
         Throw New ArgumentException("The filename cannot be an empty string.")
      End If

      Dim handle As IntPtr = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                        IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                        IntPtr.Zero)
      If handle <> INVALID_HANDLE_VALUE Then
         safeHandle = New SafeFileHandle(handle, True)
      Else
         Throw New FileNotFoundException(String.Format("Cannot open '{0}'", filename))
      End If

      ' Get file size.
      bufferSize = GetFileSize(safeHandle, upperWord) 
      If bufferSize = INVALID_FILE_SIZE Then
         bufferSize = -1
      Else If upperWord > 0 Then 
         bufferSize = (CLng(upperWord) << 32) + bufferSize
      End If     
   End Sub

   Public ReadOnly Property Size As Long
      Get
         Return bufferSize
      End Get
   End Property

   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
   End Sub           

   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Dispose of managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      ' Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = True
   End Sub  
End Class
```

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Usando um identificador seguro para implementar o padrão de descarte para uma classe derivada

O exemplo a seguir ilustra o padrão de descarte para uma classe derivada, `DisposableStreamResource2`, que herda da classe `DisposableStreamResource` apresentada no exemplo anterior. A classe acrescenta um método adicional, `WriteFileInfo`, e usa um objeto [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) para encapsular o identificador do arquivo gravável. 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;
using System.Threading;

public class DisposableStreamResource2 : DisposableStreamResource
{
   // Define additional constants.
   protected const uint GENERIC_WRITE = 0x40000000; 
   protected const uint OPEN_ALWAYS = 4;

   // Define additional APIs.
   [DllImport("kernel32.dll")]   
   protected static extern bool WriteFile(
                                SafeFileHandle safeHandle, string lpBuffer, 
                                int nNumberOfBytesToWrite, out int lpNumberOfBytesWritten,
                                IntPtr lpOverlapped);

   // Define locals.
   private bool disposed = false;
   private string filename;
   private bool created = false;
   private SafeFileHandle safeHandle;

   public DisposableStreamResource2(string filename) : base(filename)
   {
      this.filename = filename;
   }

   public void WriteFileInfo()
   { 
      if (! created) {
         IntPtr hFile = CreateFile(xref:".\FileInfo.txt", GENERIC_WRITE, 0, 
                                   IntPtr.Zero, OPEN_ALWAYS, 
                                   FILE_ATTRIBUTE_NORMAL, IntPtr.Zero);
         if (hFile != INVALID_HANDLE_VALUE)
            safeHandle = new SafeFileHandle(hFile, true);
         else
            throw new IOException("Unable to create output file.");

         created = true;
      }

      string output = String.Format("{0}: {1:N0} bytes\n", filename, Size);
      int bytesWritten;
      bool result = WriteFile(safeHandle, output, output.Length, out bytesWritten, IntPtr.Zero);                                     
   }

   protected new virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Release any managed resources here.
      if (disposing)
         safeHandle.Dispose();

      disposed = true;

      // Release any unmanaged resources not wrapped by safe handles here.

      // Call the base class implementation.
      base.Dispose(true);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource2 : Inherits DisposableStreamResource
   ' Define additional constants.
   Protected Const GENERIC_WRITE As Integer = &H40000000 
   Protected Const OPEN_ALWAYS As Integer = 4

   ' Define additional APIs.
   Protected Declare Function WriteFile Lib "kernel32.dll" (
                              safeHandle As SafeFileHandle, lpBuffer As String, 
                              nNumberOfBytesToWrite As Integer, ByRef lpNumberOfBytesWritten As Integer,
                              lpOverlapped As Object) As Boolean

   ' Define locals.
   Private disposed As Boolean = False
   Private filename As String
   Private created As Boolean = False
   Private safeHandle As SafeFileHandle

   Public Sub New(filename As String)
      MyBase.New(filename)
      Me.filename = filename
   End Sub

   Public Sub WriteFileInfo() 
      If Not created Then
         Dim hFile As IntPtr = CreateFile(".\FileInfo.txt", GENERIC_WRITE, 0, 
                                          IntPtr.Zero, OPEN_ALWAYS, 
                                          FILE_ATTRIBUTE_NORMAL, IntPtr.Zero)
         If hFile <> INVALID_HANDLE_VALUE Then
            safeHandle = New SafeFileHandle(hFile, True)
         Else
            Throw New IOException("Unable to create output file.")
         End If
         created = True
      End If
      Dim output As String = String.Format("{0}: {1:N0} bytes {2}", filename, Size, 
                                           vbCrLf)
      WriteFile(safeHandle, output, output.Length, 0&, Nothing)                                     
   End Sub

   Protected Overloads Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Release any managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      disposed = True
      ' Release any unmanaged resources not wrapped by safe handles here.

      ' Call the base class implementation.
      MyBase.Dispose(True)
   End Sub
End Class
```

## <a name="see-also"></a>Consulte também

[SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object))

[IDisposable](xref:System.IDisposable)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)

[Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles)

[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)



<!--HONumber=Nov16_HO3-->


