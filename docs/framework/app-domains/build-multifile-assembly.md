---
title: 'How to: Build a multifile assembly'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429562"
---
# <a name="how-to-build-a-multifile-assembly"></a>How to: Build a multifile assembly

Este artigo explica como criar um assembly de vários arquivos e fornece código que ilustra cada etapa no procedimento.

> [!NOTE]
> O IDE do Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único. Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou Visual Studio com o Visual C++. Multifile assemblies are supported by .NET Framework only.

## <a name="create-a-multifile-assembly"></a>Create a multifile assembly

1. Compile todos os arquivos que contêm namespaces referenciados por outros módulos no assembly nos módulos de código. The default extension for code modules is *.netmodule*.

   Por exemplo, digamos que o arquivo `Stringer` tem um namespace chamado `myStringer`, que inclui uma classe chamada `Stringer`. A classe `Stringer` contém um método chamado `StringerMethod` que grava uma única linha no console.

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. Use o comando a seguir para compilar esse código:

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   Especificar o parâmetro *module* com a opção do compilador **/t:** indica que o arquivo deve ser compilado como um módulo em vez de como um assembly. The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.

3. Compile todos os outros módulos, usando as opções do compilador necessárias para indicar os outros módulos que são referenciados no código. Esta etapa usa a opção do compilador **/addmodule**.

   In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. Use o comando a seguir para compilar esse código:

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   Especifique a opção **/t:module** porque este módulo será adicionado a um assembly em uma etapa futura. Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*. The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.

   > [!NOTE]
   > Os compiladores C# e Visual Basic dão suporte à criação de assemblies de vários arquivos diretamente usando as duas sintaxes diferentes a seguir.
   >
   > Duas compilações criam um assembly de dois arquivos:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > Uma compilação cria um assembly de dois arquivos:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. Use o [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) para criar o arquivo de saída que contém o manifesto do assembly. Esse arquivo contém informações de referência para todos os módulos ou recursos que fazem parte do assembly.

    No prompt de comando, digite o seguinte comando:

    **al** \<*nome do módulo*> \<*nome do módulo*> … **/main:** \<*nome do método*>  **/out:** \<*nome de arquivo*>  **/target:** \<*tipo de arquivo do assembly*>

    Neste comando, os argumentos *nome do módulo* especificam o nome de cada módulo a ser incluído no assembly. A opção **/main:** especifica o nome do método que é o ponto de entrada do assembly. A opção **/out:** especifica o nome do arquivo de saída, que contém metadados do assembly. The **/target:** option specifies that the assembly is a console application executable ( *.exe*) file, a Windows executable ( *.win*) file, or a library ( *.lib*) file.

    In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*. The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata. The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Você pode usar o [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) para examinar o conteúdo de um assembly ou determinar se um arquivo é um assembly ou um módulo.

## <a name="see-also"></a>Consulte também

- [Create assemblies](../../standard/assembly/create.md)
- [How to: View assembly contents](../../standard/assembly/view-contents.md)
- [Como o runtime localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Multifile assemblies](multifile-assemblies.md)
