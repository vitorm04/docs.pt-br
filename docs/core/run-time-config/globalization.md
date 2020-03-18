---
title: Configurações de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733460"
---
# <a name="run-time-configuration-options-for-globalization"></a>Opções de configuração em tempo de execução para globalização

## <a name="invariant-mode"></a>Modo invariante

- Determina se um aplicativo .NET Core é executado no modo invariante de globalização sem acesso a dados e comportamentos específicos da cultura ou se ele tem acesso a dados culturais.
- Padrão: Execute o aplicativo com`false`acesso a dados culturais ( ).
- Para obter mais informações, consulte [o modo invariante de globalização .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false`- acesso a dados culturais<br/>`true`- executar no modo invariante |
| **Propriedade MSBuild** | `InvariantGlobalization` | `false`- acesso a dados culturais<br/>`true`- executar no modo invariante |
| **Variável de ambiente** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- acesso a dados culturais<br/>`1`- executar no modo invariante |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Intervalos de ano de era

- Determina se as verificações de intervalo para calendários que suportam várias eras <xref:System.ArgumentOutOfRangeException>são relaxadas ou se as datas que transbordam o intervalo de datas de uma era lançam um .
- Padrão: As verificações`false`de intervalo são relaxadas ().
- Para obter mais informações, consulte [Calendários, eras e faixas de data: Verificações de faixa relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- verificações de faixa relaxadas<br/>`true`- transbordamentos causam uma exceção |
| **Variável de ambiente** | N/D | N/D |

## <a name="japanese-date-parsing"></a>Análise de data japonesa

- Determina se uma string que contenha "1" ou "Gannen" como o ano analisa com sucesso ou se apenas "1" é suportada.
- Padrão: Analisar strings que contenham "1" ou "Gannen" como o ano ().`false`
- Para obter mais informações, consulte [Representar datas em calendários com várias eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- "Gannen" ou "1" é suportado<br/>`true`- apenas "1" é suportado |
| **Variável de ambiente** | N/D | N/D |

## <a name="japanese-year-format"></a>Formato do ano japonês

- Determina se o primeiro ano de uma era de calendário japonês é formatado como "Gannen" ou como um número.
- Padrão: Formatar o primeiro ano`false`como "Gannen" ( ).
- Para obter mais informações, consulte [Representar datas em calendários com várias eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nome da configuração | Valores |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- formato como "Gannen"<br/>`true`- formato como número |
| **Variável de ambiente** | N/D | N/D |
