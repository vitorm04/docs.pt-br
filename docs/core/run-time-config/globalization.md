---
title: Definições de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733460"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="13196-103">Opções de configuração de tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="13196-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="13196-104">Modo invariável</span><span class="sxs-lookup"><span data-stu-id="13196-104">Invariant mode</span></span>

- <span data-ttu-id="13196-105">Determina se um aplicativo .NET Core é executado no modo invariável de globalização sem acesso a dados e comportamento específicos de cultura ou se tem acesso a dados culturais.</span><span class="sxs-lookup"><span data-stu-id="13196-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="13196-106">Padrão: execute o aplicativo com acesso a dados culturais (`false`).</span><span class="sxs-lookup"><span data-stu-id="13196-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="13196-107">Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="13196-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="13196-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="13196-108">Setting name</span></span> | <span data-ttu-id="13196-109">Valores</span><span class="sxs-lookup"><span data-stu-id="13196-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="13196-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="13196-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="13196-111">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="13196-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="13196-112">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="13196-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="13196-113">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="13196-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="13196-114">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="13196-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="13196-115">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="13196-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="13196-116">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="13196-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="13196-117">`0`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="13196-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="13196-118">`1`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="13196-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="13196-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="13196-119">Examples</span></span>

<span data-ttu-id="13196-120">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="13196-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="13196-121">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="13196-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="13196-122">Intervalos de ano da era</span><span class="sxs-lookup"><span data-stu-id="13196-122">Era year ranges</span></span>

- <span data-ttu-id="13196-123">Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="13196-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="13196-124">Padrão: as verificações de intervalo são relaxadas (`false`).</span><span class="sxs-lookup"><span data-stu-id="13196-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="13196-125">Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="13196-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="13196-126">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="13196-126">Setting name</span></span> | <span data-ttu-id="13196-127">Valores</span><span class="sxs-lookup"><span data-stu-id="13196-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="13196-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="13196-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="13196-129">`false`-verificações de intervalo relaxadas</span><span class="sxs-lookup"><span data-stu-id="13196-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="13196-130">`true`-estouros causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="13196-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="13196-131">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="13196-131">**Environment variable**</span></span> | <span data-ttu-id="13196-132">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-132">N/A</span></span> | <span data-ttu-id="13196-133">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="13196-134">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="13196-134">Japanese date parsing</span></span>

- <span data-ttu-id="13196-135">Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.</span><span class="sxs-lookup"><span data-stu-id="13196-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="13196-136">Padrão: analise as cadeias de caracteres que contêm "1" ou "gannen" como o ano (`false`).</span><span class="sxs-lookup"><span data-stu-id="13196-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="13196-137">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="13196-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="13196-138">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="13196-138">Setting name</span></span> | <span data-ttu-id="13196-139">Valores</span><span class="sxs-lookup"><span data-stu-id="13196-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="13196-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="13196-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="13196-141">`false`-"gannen" ou "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="13196-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="13196-142">somente `true` "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="13196-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="13196-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="13196-143">**Environment variable**</span></span> | <span data-ttu-id="13196-144">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-144">N/A</span></span> | <span data-ttu-id="13196-145">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="13196-146">Formato de ano japonês</span><span class="sxs-lookup"><span data-stu-id="13196-146">Japanese year format</span></span>

- <span data-ttu-id="13196-147">Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="13196-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="13196-148">Padrão: formate o primeiro ano como "gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="13196-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="13196-149">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="13196-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="13196-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="13196-150">Setting name</span></span> | <span data-ttu-id="13196-151">Valores</span><span class="sxs-lookup"><span data-stu-id="13196-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="13196-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="13196-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="13196-153">`false`-Format como "gannen"</span><span class="sxs-lookup"><span data-stu-id="13196-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="13196-154">`true`-Formatar como número</span><span class="sxs-lookup"><span data-stu-id="13196-154">`true` - format as number</span></span> |
| <span data-ttu-id="13196-155">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="13196-155">**Environment variable**</span></span> | <span data-ttu-id="13196-156">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-156">N/A</span></span> | <span data-ttu-id="13196-157">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13196-157">N/A</span></span> |
