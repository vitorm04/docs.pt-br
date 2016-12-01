---
title: Interoperabilidade nativa
description: Interoperabilidade nativa
keywords: .NET, .NET Core
author: blackdwarf
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
translationtype: Human Translation
ms.sourcegitcommit: 3aeaba5c8cf800c652941b5e6c2bc9f072849893
ms.openlocfilehash: 36041eda54290484741c375ae776b7bf1a74d7a1

---

# <a name="native-interoperability"></a>Interoperabilidade nativa

Neste documento, encontraremos mais detalhes sobre as três maneiras de fazer “interoperabilidade nativa” que estão disponíveis na plataforma .NET.

Existem alguns motivos para chamar em código nativo:

*   Os sistemas operacionais vêm com um grande volume de APIs que não estão presentes nas bibliotecas de classes gerenciadas. Um exemplo perfeito para isso seria o acesso a funções de gerenciamento de hardware ou do sistema operacional.
*   Comunicação com outros componentes que têm ou podem produzir ABIs de estilo C (ABIs nativas). Isso abrange, por exemplo, código Java que é exposto por meio da [JNI (Interface Nativa do Java)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou qualquer outra linguagem gerenciada que possa produzir um componente nativo.
*   No Windows, a maioria dos softwares que são instalados, como o pacote Microsoft Office, registra os componentes que representam seus programas e permitem que sejam automatizados ou usados pelos desenvolvedores. Isso também requer interoperabilidade nativa.

Evidentemente, a lista acima não abrange todas as possíveis situações e cenários em que o desenvolvedor desejaria/gostaria de/precisaria fazer interface com componentes nativos. A biblioteca de classes do .NET, por exemplo, usa o suporte para interoperabilidade nativa para implementar um número razoável de APIs, como suporte ao console e manipulação, acesso ao sistema de arquivos e outras. No entanto, é importante observar que há uma opção, se necessário.

> [!NOTE]
> A maioria dos exemplos deste documento será apresentada para todas as três plataformas com suporte para .NET Core (Windows, Linux e macOS). No entanto, para alguns exemplos ilustrativos e curtos, é exibida apenas uma amostra que usa nomes de arquivo e extensões do Windows (ou seja, “dll” para bibliotecas). Isso não significa que tais recursos não estão disponíveis em Linux ou macOS; foi feito simplesmente para maior conveniência.

## <a name="platform-invoke-pinvoke"></a>Invocação de plataforma (P/Invoke)

P/Invoke é uma tecnologia que permite acessar structs, retornos de chamada e funções em bibliotecas não gerenciadas do seu código gerenciado. A maior parte da API do P/Invoke está contida em dois namespaces: `System` e `System.Runtime.InteropServices`. A utilização desses dois namespaces permitirá acessar os atributos que descrevem como você deseja se comunicar com o componente nativo.

Vamos começar com exemplo mais comum, que é chamar funções não gerenciadas no seu código gerenciado. Vamos mostrar uma caixa de mensagem de um aplicativo de linha de comando:

```cs
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

O exemplo acima é muito simples, mas mostra o que é necessário para invocar funções não gerenciadas do código gerenciado. Vamos analisar o exemplo:

*   A linha #1 mostra a instrução de uso para o `System.Runtime.InteropServices`, que é o namespace que contém todos os itens de que precisamos.
*   A linha #5 apresenta o atributo `DllImport`. Esse atributo é crucial, pois informa ao tempo de execução que deve carregar a DLL não gerenciada. É a DLL para a qual desejamos invocar.
*   A linha #6 é o ponto crucial do trabalho do P/Invoke. Define um método gerenciado que tem **exatamente a mesma assinatura** que o não gerenciado. A declaração tem uma nova palavra-chave que você pode observar, `extern`, que informa ao tempo de execução que é um método externo; quando invocado, o tempo de execução deve encontrá-la na DLL especificada no atributo `DllImport`.

O restante do exemplo é simplesmente chamar o método como você faria com qualquer outro método gerenciado.

A amostra é semelhante para macOS. Uma coisa que precisa ser alterada é, obviamente, o nome da biblioteca no atributo `DllImport`, pois o macOS tem um esquema diferente de nomenclatura de bibliotecas dinâmicas. O exemplo abaixo usa a função `getpid(2)` para obter a identificação do processo do aplicativo e imprimi-la para o console.

```cs
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

É semelhante no Linux, evidentemente. O nome da função é o mesmo, já que `getpid(2)` é uma chamada do sistema [POSIX](https://en.wikipedia.org/wiki/POSIX).

```cs
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

### <a name="invoking-managed-code-from-unmanaged-code"></a>Chamando código gerenciado do código não gerenciado

Naturalmente, o tempo de execução possibilita que a comunicação aconteça em ambas as direções, o que permite chamar artefato gerenciados de funções nativas usando ponteiros de função. A coisa mais próxima a um ponteiro de função no código gerenciado é um **delegado**; portanto, isso é usado para permitir retornos de chamada do código nativo para o código gerenciado.

A maneira de usar esse recurso é semelhante ao processo gerenciado para nativo, descrito acima. Para um retorno de chamada específico, você define um delegado que corresponda à assinatura e o passa para o método externo. O tempo de execução cuidará do resto.

```cs
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC hWnd, IntPtr lParam);

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

Antes de analisarmos nosso exemplo, é bom examinar as assinaturas das funções não gerenciadas com as quais precisamos trabalhar. A função que desejamos chamar para enumerar todas as janelas tem esta assinatura: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

O primeiro parâmetro é um retorno de chamada. Esse retorno de chamada tem a seguinte assinatura: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Com isso em mente, vamos analisar o exemplo:

*   A linha #8 no exemplo define um delegado que corresponde à assinatura do retorno de chamada do código não gerenciado. Observe como os tipos LPARAM e HWND são representados usando `IntPtr` no código gerenciado.
*   As linhas #10 e #11 introduzem a função `EnumWindows` da biblioteca user32.dll.
*   As linhas #13-16 implementam o delegado. Neste exemplo simples, queremos apenas produzir o identificador para o console.
*   Por fim, na linha #19, invocamos o método externo e passamos o delegado.

Os exemplos de Linux e macOS são mostrados abaixo. Para eles, usamos a função `ftw` que pode ser encontrada em `libc`, a biblioteca C. Essa função é usada para percorrer as hierarquias de diretório e leva um ponteiro para uma função como um dos seus parâmetros. Essa função tem a seguinte assinatura: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```cs
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

```cs
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

Os exemplos acima dependem de parâmetros e, em ambos os casos, os parâmetros são fornecidos como tipos gerenciados. O tempo de execução faz a “coisa certa” e processa em equivalentes no outro lado. Como esse processo é realmente importante para escrever código de interoperabilidade nativa de qualidade, vamos ver o que acontece quando o tempo de execução _realiza marshalling_ dos tipos.

## <a name="type-marshalling"></a>Marshalling dos tipos

**Marshalling** é o processo de transformar tipos quando precisam atravessar o limite gerenciado para nativo e vice-versa.

O marshalling é necessário porque os tipos são diferentes, no código gerenciado e não gerenciado. No código gerenciado, por exemplo, você tem um `String`; no mundo não gerenciado, as cadeias de caracteres podem ser Unicode (“horizontais”), não Unicode, finalizadas com null, ASCII, etc. Por padrão, o subsistema do P/Invoke tentará fazer a coisa certa com base no comportamento padrão que você pode ver no [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx). Contudo, nas situações em que você precisa de controle extra, pode utilizar o atributo `MarshalAs` para especificar qual é o tipo esperado no lado não gerenciado. Por exemplo, se quisermos que a cadeia de caracteres seja enviada como uma cadeia de caracteres ANSI finalizada com null, poderemos fazer o seguinte:

```cs
[DllImport("somenativelibrary.dll"]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr) string parameter);

```

### <a name="marshalling-classes-and-structs"></a>Marshalling de classes e structs

Outro aspecto do marshalling de tipos é como passar um struct para um método não gerenciado. Por exemplo, alguns dos métodos não gerenciados requerem um struct como parâmetro. Nesses casos, precisamos criar um struct correspondente ou uma classe na parte gerenciada do mundo para usar como parâmetro. No entanto, definir a classe não é suficiente; também precisamos ensinar o marshaler como mapear campos na classe para o struct não gerenciado. É aí que o atributo `StructLayout` entra em cena.

```cs
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

O exemplo acima mostra um exemplo simples de chamar para a função `GetSystemTime()`. A parte interessante está na linha 4\. O atributo especifica que os campos da classe devem apontar em sequência para o struct no outro lado (não gerenciado). Isso significa que os nomes dos campos não são importantes, apenas sua ordem é importante, já que precisa corresponder ao struct não gerenciado, mostrado abaixo:

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

Já vimos o exemplo de Linux e macOS no exemplo anterior. Ele é mostrado novamente abaixo.

```cs
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

A classe `StatClass` representa uma estrutura que é retornada pela chamada do sistema `stat` em sistemas UNIX. Representa informações sobre um arquivo específico. A classe acima é a representação de struct stat no código gerenciado. Novamente, os campos na classe precisam estar na mesma ordem que o struct nativo (você pode encontrá-los analisando páginas do manual na sua implementação de UNIX favorita) e precisam ser do mesmo tipo subjacente.

## <a name="more-resources"></a>Mais recursos

*   [PInvoke.net wiki](http://www.pinvoke.net) uma wiki excelente com informações sobre as APIs comuns do Win32 e como chamá-las.
*   [P/Invoke no MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Documentação do Mono no P/Invoke](http://www.mono-project.com/docs/advanced/pinvoke/)



<!--HONumber=Dec16_HO1-->


