---
title: Invocação de plataforma (P/Invoke)
description: Saiba como chamar funções nativas via P/Invoke no .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 1a5f2f9d13429f84d5b5bb58d36f015004fb746b
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517857"
---
# <a name="platform-invoke-pinvoke"></a><span data-ttu-id="5f739-103">Invocação de plataforma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="5f739-103">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="5f739-104">P/Invoke é uma tecnologia que permite acessar structs, retornos de chamada e funções em bibliotecas não gerenciadas de um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-104">P/Invoke is a technology that allows you to access structs, callbacks, and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="5f739-105">A maior parte da API do P/Invoke está contida em dois namespaces: `System` e `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="5f739-105">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="5f739-106">O uso desses dois namespaces fornece as ferramentas que descrevem como você deseja se comunicar com o componente nativo.</span><span class="sxs-lookup"><span data-stu-id="5f739-106">Using these two namespaces give you the tools to describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="5f739-107">Vamos começar com exemplo mais comum, que é chamar funções não gerenciadas no seu código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-107">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="5f739-108">Vamos mostrar uma caixa de mensagem de um aplicativo de linha de comando:</span><span class="sxs-lookup"><span data-stu-id="5f739-108">Let’s show a message box from a command-line application:</span></span>

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll", CharSet = CharSet.Unicode, SetLastError = true)]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="5f739-109">O exemplo anterior é simples, mas mostra o que é necessário para invocar funções não gerenciadas de um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-109">The previous example is simple, but it does show off what's needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="5f739-110">Vamos analisar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="5f739-110">Let’s step through the example:</span></span>

*   <span data-ttu-id="5f739-111">A linha 1 mostra a instrução de uso para o namespace `System.Runtime.InteropServices` que contém todos os itens necessários.</span><span class="sxs-lookup"><span data-stu-id="5f739-111">Line #1 shows the using statement for the `System.Runtime.InteropServices` namespace that holds all the items needed.</span></span>
*   <span data-ttu-id="5f739-112">A linha 7 apresenta o atributo `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="5f739-112">Line #7 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="5f739-113">Esse atributo é crucial, pois informa ao tempo de execução que deve carregar a DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5f739-113">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="5f739-114">A cadeia de caracteres passada é a DLL na qual nossa função de destino está incluída.</span><span class="sxs-lookup"><span data-stu-id="5f739-114">The string passed in is the DLL our target function is in.</span></span> <span data-ttu-id="5f739-115">Além disso, especifica qual [conjunto de caracteres](./charset.md) deve ser usado para realizar marshaling de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5f739-115">Additionally, it specifies which [character set](./charset.md) to use for marshalling the strings.</span></span> <span data-ttu-id="5f739-116">Por fim, especifica que essa função chama [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) e que o tempo de execução deve capturar esse código de erro para que o usuário possa recuperá-lo via <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f739-116">Finally, it specifies that this function calls [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) and that the runtime should capture that error code so the user can retrieve it via <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.</span></span>
*   <span data-ttu-id="5f739-117">A linha 8 é o ponto crucial do trabalho do P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="5f739-117">Line #8 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="5f739-118">Define um método gerenciado que tem **exatamente a mesma assinatura** que o não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-118">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="5f739-119">A declaração tem uma nova palavra-chave que você pode observar, `extern`, que informa ao tempo de execução que é um método externo; quando invocado, o tempo de execução deve encontrá-la na DLL especificada no atributo `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="5f739-119">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="5f739-120">O restante do exemplo é simplesmente chamar o método como você faria com qualquer outro método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-120">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="5f739-121">A amostra é semelhante para macOS.</span><span class="sxs-lookup"><span data-stu-id="5f739-121">The sample is similar for macOS.</span></span> <span data-ttu-id="5f739-122">O nome da biblioteca deve ser alterado no atributo `DllImport`, pois o macOS tem um esquema diferente de nomenclatura para bibliotecas dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="5f739-122">The name of the library in the `DllImport` attribute needs to change since macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="5f739-123">O exemplo a seguir usa a função `getpid(2)` para obter a ID do processo do aplicativo e imprimi-la para o console:</span><span class="sxs-lookup"><span data-stu-id="5f739-123">The following sample uses the `getpid(2)` function to get the process ID of the application and print it out to the console:</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
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

<span data-ttu-id="5f739-124">Também é semelhante no Linux.</span><span class="sxs-lookup"><span data-stu-id="5f739-124">It is also similar on Linux.</span></span> <span data-ttu-id="5f739-125">O nome da função é o mesmo, já que `getpid(2)` é uma chamada do sistema [POSIX](https://en.wikipedia.org/wiki/POSIX) padrão.</span><span class="sxs-lookup"><span data-stu-id="5f739-125">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
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

## <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="5f739-126">Chamando código gerenciado do código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="5f739-126">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="5f739-127">O tempo de execução viabiliza o fluxo da comunicação nas duas direções, o que permite retornar a chamada no código gerenciado das funções nativas usando ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="5f739-127">The runtime allows communication to flow in both directions, enabling you to call back into managed code from native functions by using function pointers.</span></span> <span data-ttu-id="5f739-128">A coisa mais próxima a um ponteiro de função no código gerenciado é um **delegado**; portanto, isso é usado para permitir retornos de chamada do código nativo para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-128">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="5f739-129">A maneira de usar esse recurso é semelhante ao processo gerenciado para nativo, conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5f739-129">The way to use this feature is similar to the managed to native process previously described.</span></span> <span data-ttu-id="5f739-130">Para um retorno de chamada específico, você define um delegado que corresponda à assinatura e o passa para o método externo.</span><span class="sxs-lookup"><span data-stu-id="5f739-130">For a given callback, you define a delegate that matches the signature and pass that into the external method.</span></span> <span data-ttu-id="5f739-131">O tempo de execução cuidará do resto.</span><span class="sxs-lookup"><span data-stu-id="5f739-131">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="5f739-132">Antes de analisar o exemplo, é uma boa ideia examinar as assinaturas das funções não gerenciadas com as quais você precisa trabalhar.</span><span class="sxs-lookup"><span data-stu-id="5f739-132">Before walking through the example, it's good to review the signatures of the unmanaged functions you need to work with.</span></span> <span data-ttu-id="5f739-133">A função a ser chamada para enumerar todas as janelas tem esta assinatura: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="5f739-133">The function to be called to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="5f739-134">O primeiro parâmetro é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="5f739-134">The first parameter is a callback.</span></span> <span data-ttu-id="5f739-135">Esse retorno de chamada tem a seguinte assinatura: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="5f739-135">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="5f739-136">Agora, vamos analisar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="5f739-136">Now, let’s walk through the example:</span></span>

*   <span data-ttu-id="5f739-137">A linha 9 no exemplo define um delegado que corresponde à assinatura do retorno de chamada do código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-137">Line #9 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="5f739-138">Observe como os tipos LPARAM e HWND são representados usando `IntPtr` no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f739-138">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="5f739-139">As linhas 13 e 14 introduzem a função `EnumWindows` da biblioteca user32.dll.</span><span class="sxs-lookup"><span data-stu-id="5f739-139">Lines #13 and #14 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="5f739-140">As linhas de 17 a 20 implementam o delegado.</span><span class="sxs-lookup"><span data-stu-id="5f739-140">Lines #17 - 20 implement the delegate.</span></span> <span data-ttu-id="5f739-141">Neste exemplo simples, queremos apenas produzir o identificador para o console.</span><span class="sxs-lookup"><span data-stu-id="5f739-141">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="5f739-142">Por fim, na linha 24, chamamos o método externo e passamos o delegado.</span><span class="sxs-lookup"><span data-stu-id="5f739-142">Finally, in line #24, the external method is called and passed in the delegate.</span></span>

<span data-ttu-id="5f739-143">Os exemplos de Linux e macOS são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="5f739-143">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="5f739-144">Para eles, usamos a função `ftw` que pode ser encontrada em `libc`, a biblioteca C.</span><span class="sxs-lookup"><span data-stu-id="5f739-144">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="5f739-145">Essa função é usada para percorrer as hierarquias de diretório e leva um ponteiro para uma função como um dos seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5f739-145">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="5f739-146">Essa função tem a seguinte assinatura: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="5f739-146">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="5f739-147">O exemplo do macOS usa a mesma função; a única diferença é o argumento para o atributo `DllImport`, pois o macOS mantém `libc` em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="5f739-147">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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
        // represents that struct in managed code.
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

<span data-ttu-id="5f739-148">Os exemplos anteriores dependem de parâmetros e, em ambos os casos, os parâmetros são fornecidos como tipos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="5f739-148">Both of the previous examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="5f739-149">O tempo de execução faz a "coisa certa" e processa esses parâmetros em seus equivalentes no outro lado.</span><span class="sxs-lookup"><span data-stu-id="5f739-149">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="5f739-150">Saiba mais sobre como os tipos realizam marshaling para código nativo em nossa página, no artigo [Realizar marshaling de tipo](type-marshalling.md).</span><span class="sxs-lookup"><span data-stu-id="5f739-150">Learn about how types are marshalled to native code in our page on [Type marshalling](type-marshalling.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="5f739-151">Mais recursos</span><span class="sxs-lookup"><span data-stu-id="5f739-151">More resources</span></span>

*   <span data-ttu-id="5f739-152">[Wiki do PInvoke.net](https://www.pinvoke.net/) uma wiki excelente com informações sobre as APIs comuns do Windows e como chamá-las.</span><span class="sxs-lookup"><span data-stu-id="5f739-152">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Windows APIs and how to call them.</span></span>
*   [<span data-ttu-id="5f739-153">P/Invoke no MSDN</span><span class="sxs-lookup"><span data-stu-id="5f739-153">P/Invoke on MSDN</span></span>](/cpp/dotnet/native-and-dotnet-interoperability)
*   [<span data-ttu-id="5f739-154">Documentação do Mono no P/Invoke</span><span class="sxs-lookup"><span data-stu-id="5f739-154">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)
