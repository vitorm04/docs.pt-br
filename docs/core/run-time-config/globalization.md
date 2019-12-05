---
title: Definições de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802774"
---
# <a name="run-time-configuration-options-for-globalization"></a>Opções de configuração de tempo de execução para globalização

## <a name="invariant-mode"></a>Modo invariável

- Determina se um aplicativo .NET Core é executado no modo invariável de globalização sem acesso a dados e comportamento específicos de cultura ou se tem acesso a dados culturais.
- Padrão: execute o aplicativo com acesso a dados culturais (`false`).
- Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`-acesso a dados culturais<br/>`true`-executar em modo invariável |
| **Variável de ambiente** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-acesso a dados culturais<br/>`1`-executar em modo invariável |

## <a name="era-year-ranges"></a>Intervalos de ano da era

- Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException>.
- Padrão: as verificações de intervalo são relaxadas (`false`).
- Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`-verificações de intervalo relaxadas<br/>`true`-estouros causam uma exceção |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |

## <a name="japanese-date-parsing"></a>Análise de data japonesa

- Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.
- Padrão: analise as cadeias de caracteres que contêm "1" ou "gannen" como o ano (`false`).
- Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-"gannen" ou "1" tem suporte<br/>somente `true` "1" tem suporte |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |

## <a name="japanese-year-format"></a>Formato de ano japonês

- Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.
- Padrão: formate o primeiro ano como "gannen" (`false`).
- Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-Format como "gannen"<br/>`true`-Formatar como número |
| **Variável de ambiente** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
