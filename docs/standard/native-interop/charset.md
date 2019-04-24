---
title: Conjuntos de caracteres e marshaling – .NET
description: Saiba como os diferentes valores de um conjunto de caracteres podem alterar a forma como o .NET realiza marshaling dos dados para o código nativo.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: f436bbbf435df07d242f9bf295b0264c4cfd5b3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480840"
---
# <a name="charsets-and-marshalling"></a>Conjuntos de caracteres e marshaling

A maneira pela qual os valores `char`, os objetos `string` e os objetos `System.Text.StringBuilder` realizam marshaling depende do valor do campo `CharSet`, no P/Invoke ou na estrutura. Para definir o `CharSet` de um P/Invoke, configure o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> quando declarar o P/Invoke. Para definir o `CharSet` de uma estrutura, configure o campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na declaração do struct. Se esses campos do atributo não estiverem definidos, caberá ao compilador de linguagem determinar qual `CharSet` a ser usado. O C# e o Visual Basic usam o conjunto de caracteres <xref:System.Runtime.InteropServices.CharSet.Ansi> por padrão.

A tabela a seguir mostra um mapeamento entre cada conjunto de caracteres e como um caractere ou uma cadeia de caracteres são representados quando realizam marshaling com esse conjunto de caracteres:

| CharSet | Windows            | Unix no .NET Core 2.2 e versões anteriores | Mono e Unix no .NET Core 3.0 e versões posteriores |
|---------|--------------------|-----------------------------|------------------------------------------|
| Ansi    | `char` (ANSI)      | `char` (UTF-8)              | `char` (UTF-8)                           |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char16_t` (UTF-16)                      |
| Automático    | `wchar_t` (UTF-16) | `char16_t` (UTF-16)         | `char` (UTF-8)                           |

Quando escolher o conjunto de caracteres, saiba qual será a representação esperada por sua representação nativa.
