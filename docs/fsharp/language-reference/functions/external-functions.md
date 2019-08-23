---
title: Funções externas
description: Saiba mais sobre F# o suporte de idioma para chamar funções em código nativo.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968727"
---
# <a name="external-functions"></a>Funções externas

Este tópico descreve F# o suporte a idiomas para chamar funções em código nativo.

## <a name="syntax"></a>Sintaxe

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *arguments* representa argumentos que são fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo. O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll. Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas da `System.Runtime.InteropServices.DllImportAttribute` classe, como a Convenção de chamada.

Suponha que você tenha uma C++ DLL nativa que contenha a seguinte função exportada.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Você pode chamar essa função F# usando o código a seguir.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

A interoperabilidade com código nativo é conhecida como invocação de *plataforma* e é um recurso do CLR. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../framework/interop/index.md). As informações contidas nessa seção são aplicáveis F#ao.

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
