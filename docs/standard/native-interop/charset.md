---
title: Conjuntos de caracteres e marshaling – .NET
description: Saiba como os diferentes valores de um conjunto de caracteres podem alterar a forma como o .NET realiza marshaling dos dados para o código nativo.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411345"
---
# <a name="charsets-and-marshalling"></a>Conjuntos de caracteres e marshaling

A maneira pela qual os valores `char`, os objetos `string` e os objetos `System.Text.StringBuilder` realizam marshaling depende do valor do campo `CharSet`, no P/Invoke ou na estrutura. Para definir o `CharSet` de um P/Invoke, configure o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> quando declarar o P/Invoke. Para definir o `CharSet` de uma estrutura, configure o campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na declaração do struct. Se esses campos do atributo não estiverem definidos, caberá ao compilador de linguagem determinar qual `CharSet` a ser usado. O C# usa o conjunto de caracteres <xref:System.Runtime.InteropServices.CharSet.Ansi> por padrão.

A tabela a seguir mostra um mapeamento entre cada conjunto de caracteres e como um caractere ou uma cadeia de caracteres são representados quando realizam marshaling com esse conjunto de caracteres:

| CharSet | Windows | Unix | Mono em Unix |
|---------|---------|-------|-------|
| Ansi    | `char` (ANSI)  | `char` (ANSI em macOS, UTF-8 em Linux) | `char` (UTF-8) |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char16_t` (UTF-16) |
| Automático | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char` (UTF-8) |

Quando escolher o conjunto de caracteres, saiba qual será a representação esperada por sua representação nativa.
