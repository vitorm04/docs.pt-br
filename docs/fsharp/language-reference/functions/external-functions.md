---
title: Funções externas
description: Saiba mais sobre o F# suporte de linguagem para chamar funções em código nativo.
ms.date: 05/16/2016
ms.openlocfilehash: 86ea78844fb812361233f8360c377465d83be203
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611718"
---
# <a name="external-functions"></a>Funções externas

Este tópico descreve F# suporte de linguagem para chamar funções em código nativo.

## <a name="syntax"></a>Sintaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *argumentos* representa os argumentos que são fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo. O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll. Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas do `System.Runtime.InteropServices.DllImportAttribute` classe, como a convenção de chamada.

Suponha que você tem um C++ DLL que contém a seguinte função exportada nativo.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Você pode chamar essa função do F# usando o código a seguir.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Interoperabilidade com código nativo é conhecida como *de invocação de plataforma* e é um recurso do CLR. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../../docs/framework/interop/index.md). As informações nesta seção são aplicáveis a F#.

## <a name="see-also"></a>Consulte também

- [Funções](index.md)