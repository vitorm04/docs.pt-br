---
title: Definições de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 7668c345181d7c08cfca9c5cb76b8addd76223ec
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506799"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="be768-103">Opções de configuração de tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="be768-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="be768-104">Modo invariável</span><span class="sxs-lookup"><span data-stu-id="be768-104">Invariant mode</span></span>

- <span data-ttu-id="be768-105">Determina se um aplicativo .NET Core é executado no modo inconstante de globalização sem acesso a dados e comportamento específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="be768-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="be768-106">Padrão: execute o aplicativo com acesso a dados culturais (`false`).</span><span class="sxs-lookup"><span data-stu-id="be768-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="be768-107">Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="be768-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="be768-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="be768-108">Setting name</span></span> | <span data-ttu-id="be768-109">Valores</span><span class="sxs-lookup"><span data-stu-id="be768-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="be768-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="be768-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="be768-111">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="be768-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="be768-112">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="be768-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="be768-113">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="be768-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="be768-114">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="be768-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="be768-115">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="be768-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="be768-116">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="be768-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="be768-117">`0`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="be768-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="be768-118">`1`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="be768-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="be768-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="be768-119">Examples</span></span>

<span data-ttu-id="be768-120">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="be768-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="be768-121">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="be768-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="be768-122">Intervalos de ano da era</span><span class="sxs-lookup"><span data-stu-id="be768-122">Era year ranges</span></span>

- <span data-ttu-id="be768-123">Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="be768-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="be768-124">Padrão: as verificações de intervalo são`false`relaxadas ().</span><span class="sxs-lookup"><span data-stu-id="be768-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="be768-125">Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="be768-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="be768-126">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="be768-126">Setting name</span></span> | <span data-ttu-id="be768-127">Valores</span><span class="sxs-lookup"><span data-stu-id="be768-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="be768-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="be768-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="be768-129">`false`-verificações de intervalo relaxadas</span><span class="sxs-lookup"><span data-stu-id="be768-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="be768-130">`true`-estouros causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="be768-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="be768-131">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="be768-131">**Environment variable**</span></span> | <span data-ttu-id="be768-132">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-132">N/A</span></span> | <span data-ttu-id="be768-133">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="be768-134">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="be768-134">Japanese date parsing</span></span>

- <span data-ttu-id="be768-135">Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.</span><span class="sxs-lookup"><span data-stu-id="be768-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="be768-136">Padrão: analise as cadeias de caracteres que contêm "1" ou "gannen" como`false`o ano ().</span><span class="sxs-lookup"><span data-stu-id="be768-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="be768-137">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="be768-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="be768-138">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="be768-138">Setting name</span></span> | <span data-ttu-id="be768-139">Valores</span><span class="sxs-lookup"><span data-stu-id="be768-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="be768-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="be768-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="be768-141">`false`-"Gannen" ou "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="be768-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="be768-142">`true`-somente "1" é suportado</span><span class="sxs-lookup"><span data-stu-id="be768-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="be768-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="be768-143">**Environment variable**</span></span> | <span data-ttu-id="be768-144">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-144">N/A</span></span> | <span data-ttu-id="be768-145">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="be768-146">Formato de ano japonês</span><span class="sxs-lookup"><span data-stu-id="be768-146">Japanese year format</span></span>

- <span data-ttu-id="be768-147">Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="be768-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="be768-148">Padrão: formate o primeiro ano como "gannen"`false`().</span><span class="sxs-lookup"><span data-stu-id="be768-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="be768-149">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="be768-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="be768-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="be768-150">Setting name</span></span> | <span data-ttu-id="be768-151">Valores</span><span class="sxs-lookup"><span data-stu-id="be768-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="be768-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="be768-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="be768-153">`false`-Formatar como "gannen"</span><span class="sxs-lookup"><span data-stu-id="be768-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="be768-154">`true`-Formatar como número</span><span class="sxs-lookup"><span data-stu-id="be768-154">`true` - format as number</span></span> |
| <span data-ttu-id="be768-155">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="be768-155">**Environment variable**</span></span> | <span data-ttu-id="be768-156">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-156">N/A</span></span> | <span data-ttu-id="be768-157">N/D</span><span class="sxs-lookup"><span data-stu-id="be768-157">N/A</span></span> |
