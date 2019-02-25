---
title: Invocação de plataforma (P/Invoke)
description: Saiba como chamar funções nativas via P/Invoke no .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: f243fee2b246afff36732d469c6295d7e4b2fd87
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411347"
---
# <a name="platform-invoke-pinvoke"></a>Invocação de plataforma (P/Invoke)

P/Invoke é uma tecnologia que permite acessar structs, retornos de chamada e funções em bibliotecas não gerenciadas de um código gerenciado. A maior parte da API do P/Invoke está contida em dois namespaces: `System` e `System.Runtime.InteropServices`. O uso desses dois namespaces fornece as ferramentas que descrevem como você deseja se comunicar com o componente nativo.

Vamos começar com exemplo mais comum, que é chamar funções não gerenciadas no seu código gerenciado. Vamos mostrar uma caixa de mensagem de um aplicativo de linha de comando:

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

O exemplo anterior é simples, mas mostra o que é necessário para invocar funções não gerenciadas de um código gerenciado. Vamos analisar o exemplo:

*   A linha 1 mostra a instrução de uso para o namespace `System.Runtime.InteropServices` que contém todos os itens necessários.
*   A linha 7 apresenta o atributo `DllImport`. Esse atributo é crucial, pois informa ao tempo de execução que deve carregar a DLL não gerenciada. A cadeia de caracteres passada é a DLL na qual nossa função de destino está incluída.
*   A linha 8 é o ponto crucial do trabalho do P/Invoke. Define um método gerenciado que tem **exatamente a mesma assinatura** que o não gerenciado. A declaração tem uma nova palavra-chave que você pode observar, `extern`, que informa ao tempo de execução que é um método externo; quando invocado, o tempo de execução deve encontrá-la na DLL especificada no atributo `DllImport`.

O restante do exemplo é simplesmente chamar o método como você faria com qualquer outro método gerenciado.

A amostra é semelhante para macOS. O nome da biblioteca deve ser alterado no atributo `DllImport`, pois o macOS tem um esquema diferente de nomenclatura para bibliotecas dinâmicas. O exemplo a seguir usa a função `getpid(2)` para obter a ID do processo do aplicativo e imprimi-la para o console:

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

Também é semelhante no Linux. O nome da função é o mesmo, já que `getpid(2)` é uma chamada do sistema [POSIX](https://en.wikipedia.org/wiki/POSIX) padrão.

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

## <a name="invoking-managed-code-from-unmanaged-code"></a>Chamando código gerenciado do código não gerenciado

O tempo de execução viabiliza o fluxo da comunicação nas duas direções, o que permite retornar a chamada no código gerenciado das funções nativas usando ponteiros de função. A coisa mais próxima a um ponteiro de função no código gerenciado é um **delegado**; portanto, isso é usado para permitir retornos de chamada do código nativo para o código gerenciado.

A maneira de usar esse recurso é semelhante ao processo gerenciado para nativo, conforme descrito anteriormente. Para um retorno de chamada específico, você define um delegado que corresponda à assinatura e o passa para o método externo. O tempo de execução cuidará do resto.

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

Antes de analisar o exemplo, é uma boa ideia examinar as assinaturas das funções não gerenciadas com as quais você precisa trabalhar. A função a ser chamada para enumerar todas as janelas tem esta assinatura: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

O primeiro parâmetro é um retorno de chamada. Esse retorno de chamada tem a seguinte assinatura: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Agora, vamos analisar o exemplo:

*   A linha 9 no exemplo define um delegado que corresponde à assinatura do retorno de chamada do código não gerenciado. Observe como os tipos LPARAM e HWND são representados usando `IntPtr` no código gerenciado.
*   As linhas 13 e 14 introduzem a função `EnumWindows` da biblioteca user32.dll.
*   As linhas de 17 a 20 implementam o delegado. Neste exemplo simples, queremos apenas produzir o identificador para o console.
*   Por fim, na linha 24, chamamos o método externo e passamos o delegado.

Os exemplos de Linux e macOS são mostrados abaixo. Para eles, usamos a função `ftw` que pode ser encontrada em `libc`, a biblioteca C. Essa função é usada para percorrer as hierarquias de diretório e leva um ponteiro para uma função como um dos seus parâmetros. Essa função tem a seguinte assinatura: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

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

O exemplo do macOS usa a mesma função; a única diferença é o argumento para o atributo `DllImport`, pois o macOS mantém `libc` em um local diferente.

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

Os exemplos anteriores dependem de parâmetros e, em ambos os casos, os parâmetros são fornecidos como tipos gerenciados. O tempo de execução faz a "coisa certa" e processa esses parâmetros em seus equivalentes no outro lado. Saiba mais sobre como os tipos realizam marshaling para código nativo em nossa página, no artigo [Realizar marshaling de tipo](type-marshalling.md).


## <a name="more-resources"></a>Mais recursos

*   [PInvoke.net wiki](https://www.pinvoke.net/) uma wiki excelente com informações sobre as APIs comuns do Win32 e como chamá-las.
*   [P/Invoke no MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Documentação do Mono no P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
