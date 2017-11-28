---
title: Interoperabilidade nativa
description: Saiba como fazer interface com componentes nativos no .NET.
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 9652986491f087b8fa175e2b4041063c71211178
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="native-interoperability"></a><span data-ttu-id="f5420-104">Interoperabilidade nativa</span><span class="sxs-lookup"><span data-stu-id="f5420-104">Native Interoperability</span></span>

<span data-ttu-id="f5420-105">Neste documento, encontraremos mais detalhes sobre as três maneiras de fazer "interoperabilidade nativa" que estão disponíveis com o uso do .NET.</span><span class="sxs-lookup"><span data-stu-id="f5420-105">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="f5420-106">Existem alguns motivos para chamar em código nativo:</span><span class="sxs-lookup"><span data-stu-id="f5420-106">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="f5420-107">Os sistemas operacionais vêm com um grande volume de APIs que não estão presentes nas bibliotecas de classes gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="f5420-107">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="f5420-108">Um exemplo perfeito para isso seria o acesso a funções de gerenciamento de hardware ou do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f5420-108">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="f5420-109">Comunicação com outros componentes que têm ou podem produzir ABIs de estilo C (ABIs nativas).</span><span class="sxs-lookup"><span data-stu-id="f5420-109">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="f5420-110">Isso abrange, por exemplo, código Java que é exposto por meio da [JNI (Interface Nativa do Java)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou qualquer outra linguagem gerenciada que possa produzir um componente nativo.</span><span class="sxs-lookup"><span data-stu-id="f5420-110">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="f5420-111">No Windows, a maioria dos softwares que são instalados, como o pacote Microsoft Office, registra os componentes que representam seus programas e permitem que sejam automatizados ou usados pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="f5420-111">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="f5420-112">Isso também requer interoperabilidade nativa.</span><span class="sxs-lookup"><span data-stu-id="f5420-112">This also requires native interoperability.</span></span>

<span data-ttu-id="f5420-113">Evidentemente, a lista acima não abrange todas as possíveis situações e cenários em que o desenvolvedor desejaria/gostaria de/precisaria fazer interface com componentes nativos.</span><span class="sxs-lookup"><span data-stu-id="f5420-113">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="f5420-114">A biblioteca de classes do .NET, por exemplo, usa o suporte para interoperabilidade nativa para implementar um número razoável de APIs, como suporte ao console e manipulação, acesso ao sistema de arquivos e outras.</span><span class="sxs-lookup"><span data-stu-id="f5420-114">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="f5420-115">No entanto, é importante observar que há uma opção, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f5420-115">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="f5420-116">A maioria dos exemplos deste documento será apresentada para todas as três plataformas com suporte para .NET Core (Windows, Linux e macOS).</span><span class="sxs-lookup"><span data-stu-id="f5420-116">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="f5420-117">No entanto, para alguns exemplos ilustrativos e curtos, é exibida apenas uma amostra que usa nomes de arquivo e extensões do Windows (ou seja, "dll" para bibliotecas).</span><span class="sxs-lookup"><span data-stu-id="f5420-117">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="f5420-118">Isso não significa que tais recursos não estão disponíveis em Linux ou macOS; foi feito simplesmente para maior conveniência.</span><span class="sxs-lookup"><span data-stu-id="f5420-118">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="f5420-119">Invocação de plataforma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="f5420-119">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="f5420-120">P/Invoke é uma tecnologia que permite acessar structs, retornos de chamada e funções em bibliotecas não gerenciadas do seu código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-120">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="f5420-121">A maior parte da API do P/Invoke está contida em dois namespaces: `System` e `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="f5420-121">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="f5420-122">A utilização desses dois namespaces permitirá acessar os atributos que descrevem como você deseja se comunicar com o componente nativo.</span><span class="sxs-lookup"><span data-stu-id="f5420-122">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="f5420-123">Vamos começar com exemplo mais comum, que é chamar funções não gerenciadas no seu código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-123">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="f5420-124">Vamos mostrar uma caixa de mensagem de um aplicativo de linha de comando:</span><span class="sxs-lookup"><span data-stu-id="f5420-124">Let’s show a message box from a command-line application:</span></span>

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="f5420-125">O exemplo acima é muito simples, mas mostra o que é necessário para invocar funções não gerenciadas do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-125">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="f5420-126">Vamos analisar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="f5420-126">Let’s step through the example:</span></span>

*   <span data-ttu-id="f5420-127">A linha #1 mostra a instrução de uso para o `System.Runtime.InteropServices`, que é o namespace que contém todos os itens de que precisamos.</span><span class="sxs-lookup"><span data-stu-id="f5420-127">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="f5420-128">A linha #5 apresenta o atributo `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="f5420-128">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="f5420-129">Esse atributo é crucial, pois informa ao tempo de execução que deve carregar a DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="f5420-129">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="f5420-130">É a DLL para a qual desejamos invocar.</span><span class="sxs-lookup"><span data-stu-id="f5420-130">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="f5420-131">A linha #6 é o ponto crucial do trabalho do P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="f5420-131">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="f5420-132">Define um método gerenciado que tem **exatamente a mesma assinatura** que o não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-132">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="f5420-133">A declaração tem uma nova palavra-chave que você pode observar, `extern`, que informa ao tempo de execução que é um método externo; quando invocado, o tempo de execução deve encontrá-la na DLL especificada no atributo `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="f5420-133">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="f5420-134">O restante do exemplo é simplesmente chamar o método como você faria com qualquer outro método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-134">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="f5420-135">A amostra é semelhante para macOS.</span><span class="sxs-lookup"><span data-stu-id="f5420-135">The sample is similar for macOS.</span></span> <span data-ttu-id="f5420-136">Uma coisa que precisa ser alterada é, obviamente, o nome da biblioteca no atributo `DllImport`, pois o macOS tem um esquema diferente de nomenclatura de bibliotecas dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="f5420-136">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="f5420-137">O exemplo abaixo usa a função `getpid(2)` para obter a identificação do processo do aplicativo e imprimi-la para o console.</span><span class="sxs-lookup"><span data-stu-id="f5420-137">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

<span data-ttu-id="f5420-138">É semelhante no Linux, evidentemente.</span><span class="sxs-lookup"><span data-stu-id="f5420-138">It is similar on Linux, of course.</span></span> <span data-ttu-id="f5420-139">O nome da função é o mesmo, já que `getpid(2)` é uma chamada do sistema [POSIX](https://en.wikipedia.org/wiki/POSIX).</span><span class="sxs-lookup"><span data-stu-id="f5420-139">The function name is same, since `getpid(2)` is [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="f5420-140">Chamando código gerenciado do código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="f5420-140">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="f5420-141">Naturalmente, o tempo de execução possibilita que a comunicação aconteça em ambas as direções, o que permite chamar artefato gerenciados de funções nativas usando ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="f5420-141">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="f5420-142">A coisa mais próxima a um ponteiro de função no código gerenciado é um **delegado**; portanto, isso é usado para permitir retornos de chamada do código nativo para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-142">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="f5420-143">A maneira de usar esse recurso é semelhante ao processo gerenciado para nativo, descrito acima.</span><span class="sxs-lookup"><span data-stu-id="f5420-143">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="f5420-144">Para um retorno de chamada específico, você define um delegado que corresponda à assinatura e o passa para o método externo.</span><span class="sxs-lookup"><span data-stu-id="f5420-144">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="f5420-145">O tempo de execução cuidará do resto.</span><span class="sxs-lookup"><span data-stu-id="f5420-145">The runtime will take care of everything else.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

<span data-ttu-id="f5420-146">Antes de analisarmos nosso exemplo, é bom examinar as assinaturas das funções não gerenciadas com as quais precisamos trabalhar.</span><span class="sxs-lookup"><span data-stu-id="f5420-146">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="f5420-147">A função que desejamos chamar para enumerar todas as janelas tem esta assinatura: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f5420-147">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="f5420-148">O primeiro parâmetro é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f5420-148">The first parameter is a callback.</span></span> <span data-ttu-id="f5420-149">Esse retorno de chamada tem a seguinte assinatura: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f5420-149">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="f5420-150">Com isso em mente, vamos analisar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="f5420-150">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="f5420-151">A linha #8 no exemplo define um delegado que corresponde à assinatura do retorno de chamada do código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-151">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="f5420-152">Observe como os tipos LPARAM e HWND são representados usando `IntPtr` no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-152">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="f5420-153">As linhas #10 e #11 introduzem a função `EnumWindows` da biblioteca user32.dll.</span><span class="sxs-lookup"><span data-stu-id="f5420-153">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="f5420-154">As linhas #13-16 implementam o delegado.</span><span class="sxs-lookup"><span data-stu-id="f5420-154">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="f5420-155">Neste exemplo simples, queremos apenas produzir o identificador para o console.</span><span class="sxs-lookup"><span data-stu-id="f5420-155">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="f5420-156">Por fim, na linha #19, invocamos o método externo e passamos o delegado.</span><span class="sxs-lookup"><span data-stu-id="f5420-156">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="f5420-157">Os exemplos de Linux e macOS são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="f5420-157">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="f5420-158">Para eles, usamos a função `ftw` que pode ser encontrada em `libc`, a biblioteca C.</span><span class="sxs-lookup"><span data-stu-id="f5420-158">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="f5420-159">Essa função é usada para percorrer as hierarquias de diretório e leva um ponteiro para uma função como um dos seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f5420-159">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="f5420-160">Essa função tem a seguinte assinatura: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="f5420-160">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

<span data-ttu-id="f5420-161">O exemplo do macOS usa a mesma função; a única diferença é o argumento para o atributo `DllImport`, pois o macOS mantém `libc` em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="f5420-161">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

<span data-ttu-id="f5420-162">Os exemplos acima dependem de parâmetros e, em ambos os casos, os parâmetros são fornecidos como tipos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="f5420-162">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="f5420-163">O tempo de execução faz a "coisa certa" e processa esses parâmetros em seus equivalentes no outro lado.</span><span class="sxs-lookup"><span data-stu-id="f5420-163">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="f5420-164">Como esse processo é realmente importante para escrever código de interoperabilidade nativa de qualidade, vamos ver o que acontece quando o tempo de execução _realiza marshalling_ dos tipos.</span><span class="sxs-lookup"><span data-stu-id="f5420-164">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="f5420-165">Marshalling dos tipos</span><span class="sxs-lookup"><span data-stu-id="f5420-165">Type marshalling</span></span>

<span data-ttu-id="f5420-166">**Marshalling** é o processo de transformar tipos quando precisam atravessar o limite gerenciado para nativo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="f5420-166">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="f5420-167">O marshalling é necessário porque os tipos são diferentes, no código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-167">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="f5420-168">No código gerenciado, por exemplo, você tem uma `String`; no mundo não gerenciado, as cadeias de caracteres podem ser Unicode ("larga"), não Unicode, terminada em nulo, ASCII, etc. Por padrão, o subsistema do P/Invoke tentará fazer a coisa certa com base no comportamento padrão que você pode ver no [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span><span class="sxs-lookup"><span data-stu-id="f5420-168">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span></span> <span data-ttu-id="f5420-169">Contudo, nas situações em que você precisa de controle extra, pode utilizar o atributo `MarshalAs` para especificar qual é o tipo esperado no lado não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-169">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="f5420-170">Por exemplo, se quisermos que a cadeia de caracteres seja enviada como uma cadeia de caracteres ANSI finalizada com null, poderemos fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5420-170">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="f5420-171">Marshalling de classes e structs</span><span class="sxs-lookup"><span data-stu-id="f5420-171">Marshalling classes and structs</span></span>

<span data-ttu-id="f5420-172">Outro aspecto do marshalling de tipos é como passar um struct para um método não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-172">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="f5420-173">Por exemplo, alguns dos métodos não gerenciados requerem um struct como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f5420-173">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="f5420-174">Nesses casos, precisamos criar um struct correspondente ou uma classe na parte gerenciada do mundo para usar como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f5420-174">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="f5420-175">No entanto, definir a classe não é suficiente; também precisamos ensinar o marshaler como mapear campos na classe para o struct não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-175">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="f5420-176">É aí que o atributo `StructLayout` entra em cena.</span><span class="sxs-lookup"><span data-stu-id="f5420-176">This is where the `StructLayout` attribute comes into play.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="f5420-177">O exemplo acima mostra um exemplo simples de chamar para a função `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="f5420-177">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="f5420-178">A parte interessante está na linha 4.</span><span class="sxs-lookup"><span data-stu-id="f5420-178">The interesting bit is on line 4.</span></span> <span data-ttu-id="f5420-179">O atributo especifica que os campos da classe devem ser mapeados em sequência até o struct no outro lado (não gerenciado).</span><span class="sxs-lookup"><span data-stu-id="f5420-179">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="f5420-180">Isso significa que os nomes dos campos não são importantes, apenas sua ordem é importante, já que precisa corresponder ao struct não gerenciado, mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f5420-180">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="f5420-181">Já vimos o exemplo de Linux e macOS no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="f5420-181">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="f5420-182">Ele é mostrado novamente abaixo.</span><span class="sxs-lookup"><span data-stu-id="f5420-182">It is shown again below.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

<span data-ttu-id="f5420-183">A classe `StatClass` representa uma estrutura que é retornada pela chamada do sistema `stat` em sistemas UNIX.</span><span class="sxs-lookup"><span data-stu-id="f5420-183">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="f5420-184">Representa informações sobre um arquivo específico.</span><span class="sxs-lookup"><span data-stu-id="f5420-184">It represents information about a given file.</span></span> <span data-ttu-id="f5420-185">A classe acima é a representação de struct stat no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f5420-185">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="f5420-186">Novamente, os campos na classe precisam estar na mesma ordem que o struct nativo (você pode encontrá-los analisando páginas do manual na sua implementação de UNIX favorita) e precisam ser do mesmo tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="f5420-186">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="f5420-187">Mais recursos</span><span class="sxs-lookup"><span data-stu-id="f5420-187">More resources</span></span>

*   <span data-ttu-id="f5420-188">[PInvoke.net wiki](http://www.pinvoke.net) uma wiki excelente com informações sobre as APIs comuns do Win32 e como chamá-las.</span><span class="sxs-lookup"><span data-stu-id="f5420-188">[PInvoke.net wiki](http://www.pinvoke.net) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="f5420-189">P/Invoke no MSDN</span><span class="sxs-lookup"><span data-stu-id="f5420-189">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="f5420-190">Documentação do Mono no P/Invoke</span><span class="sxs-lookup"><span data-stu-id="f5420-190">Mono documentation on P/Invoke</span></span>](http://www.mono-project.com/docs/advanced/pinvoke/)
