---
title: Conjuntos de caracteres e marshaling – .NET
description: Saiba como os diferentes valores de um conjunto de caracteres podem alterar a forma como o .NET realiza marshaling dos dados para o código nativo.
ms.date: 01/18/2019
ms.openlocfilehash: 4be4bd5a968eb5c0d6959a0f378ee1223ed906ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706381"
---
# <a name="charsets-and-marshaling"></a>Conjuntos de caracteres e marshaling

A maneira como valores `char`, objetos `string` e objetos `System.Text.StringBuilder` são empacotados depende do valor do campo `CharSet` em P/Invoke ou na estrutura. Para definir o `CharSet` de um P/Invoke, configure o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> quando declarar o P/Invoke. Para definir o `CharSet` para um tipo, defina o campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> na sua declaração de classe ou struct. Se esses campos do atributo não estiverem definidos, caberá ao compilador de linguagem determinar qual `CharSet` a ser usado. C#e Visual Basic usar o conjunto de caracteres <xref:System.Runtime.InteropServices.CharSet.Ansi> por padrão.

A tabela a seguir mostra um mapeamento entre cada conjunto de caracteres e como um caractere ou uma cadeia de caracteres é representado quando o é realizado seu marshaling com esse conjunto de caracteres:

| Valor `CharSet` | Portal            | .NET Core 2.2 e anteriores no Unix | .NET Core 3.0 e posteriores e Mono no Unix |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (a [página de códigos do Windows (ANSI)](/windows/win32/intl/code-pages) padrão do sistema)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| Automático            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

Quando escolher o conjunto de caracteres, saiba qual será a representação esperada por sua representação nativa.
