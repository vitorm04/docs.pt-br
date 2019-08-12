---
title: Conjuntos de caracteres e marshaling – .NET
description: Saiba como os diferentes valores de um conjunto de caracteres podem alterar a forma como o .NET realiza marshaling dos dados para o código nativo.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cac71c5d09514dfe1244d16224944e05826edfa9
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817847"
---
# <a name="charsets-and-marshaling"></a>Conjuntos de caracteres e marshaling

A maneira como valores `char`, objetos `string` e objetos `System.Text.StringBuilder` são empacotados depende do valor do campo `CharSet` em P/Invoke ou na estrutura. Para definir o `CharSet` de um P/Invoke, configure o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> quando declarar o P/Invoke. Para definir o `CharSet` de uma estrutura, configure o campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na declaração do struct. Se esses campos do atributo não estiverem definidos, caberá ao compilador de linguagem determinar qual `CharSet` a ser usado. O C# e o Visual Basic usam o conjunto de caracteres <xref:System.Runtime.InteropServices.CharSet.Ansi> por padrão.

A tabela a seguir mostra um mapeamento entre cada conjunto de caracteres e como um caractere ou uma cadeia de caracteres é representado quando o é realizado seu marshaling com esse conjunto de caracteres:

| Valor `CharSet` | Windows            | .NET Core 2.2 e anteriores no Unix | .NET Core 3.0 e posteriores e Mono no Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (a [página de códigos do Windows (ANSI)](/windows/win32/intl/code-pages) padrão do sistema)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Automático            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Quando escolher o conjunto de caracteres, saiba qual será a representação esperada por sua representação nativa.
