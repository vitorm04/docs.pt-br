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
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="560c2-103">Opções de configuração em tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="560c2-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="560c2-104">Modo invariante</span><span class="sxs-lookup"><span data-stu-id="560c2-104">Invariant mode</span></span>

- <span data-ttu-id="560c2-105">Determina se um aplicativo .NET Core é executado no modo invariante de globalização sem acesso a dados e comportamentos específicos da cultura ou se ele tem acesso a dados culturais.</span><span class="sxs-lookup"><span data-stu-id="560c2-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="560c2-106">Padrão: Execute o aplicativo com`false`acesso a dados culturais ( ).</span><span class="sxs-lookup"><span data-stu-id="560c2-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="560c2-107">Para obter mais informações, consulte [o modo invariante de globalização .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="560c2-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="560c2-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="560c2-108">Setting name</span></span> | <span data-ttu-id="560c2-109">Valores</span><span class="sxs-lookup"><span data-stu-id="560c2-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="560c2-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="560c2-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="560c2-111">`false`- acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="560c2-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="560c2-112">`true`- executar no modo invariante</span><span class="sxs-lookup"><span data-stu-id="560c2-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="560c2-113">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="560c2-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="560c2-114">`false`- acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="560c2-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="560c2-115">`true`- executar no modo invariante</span><span class="sxs-lookup"><span data-stu-id="560c2-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="560c2-116">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="560c2-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="560c2-117">`0`- acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="560c2-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="560c2-118">`1`- executar no modo invariante</span><span class="sxs-lookup"><span data-stu-id="560c2-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="560c2-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="560c2-119">Examples</span></span>

<span data-ttu-id="560c2-120">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="560c2-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="560c2-121">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="560c2-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="560c2-122">Intervalos de ano de era</span><span class="sxs-lookup"><span data-stu-id="560c2-122">Era year ranges</span></span>

- <span data-ttu-id="560c2-123">Determina se as verificações de intervalo para calendários que suportam várias eras <xref:System.ArgumentOutOfRangeException>são relaxadas ou se as datas que transbordam o intervalo de datas de uma era lançam um .</span><span class="sxs-lookup"><span data-stu-id="560c2-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="560c2-124">Padrão: As verificações`false`de intervalo são relaxadas ().</span><span class="sxs-lookup"><span data-stu-id="560c2-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="560c2-125">Para obter mais informações, consulte [Calendários, eras e faixas de data: Verificações de faixa relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="560c2-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="560c2-126">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="560c2-126">Setting name</span></span> | <span data-ttu-id="560c2-127">Valores</span><span class="sxs-lookup"><span data-stu-id="560c2-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="560c2-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="560c2-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="560c2-129">`false`- verificações de faixa relaxadas</span><span class="sxs-lookup"><span data-stu-id="560c2-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="560c2-130">`true`- transbordamentos causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="560c2-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="560c2-131">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="560c2-131">**Environment variable**</span></span> | <span data-ttu-id="560c2-132">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-132">N/A</span></span> | <span data-ttu-id="560c2-133">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="560c2-134">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="560c2-134">Japanese date parsing</span></span>

- <span data-ttu-id="560c2-135">Determina se uma string que contenha "1" ou "Gannen" como o ano analisa com sucesso ou se apenas "1" é suportada.</span><span class="sxs-lookup"><span data-stu-id="560c2-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="560c2-136">Padrão: Analisar strings que contenham "1" ou "Gannen" como o ano ().`false`</span><span class="sxs-lookup"><span data-stu-id="560c2-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="560c2-137">Para obter mais informações, consulte [Representar datas em calendários com várias eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="560c2-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="560c2-138">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="560c2-138">Setting name</span></span> | <span data-ttu-id="560c2-139">Valores</span><span class="sxs-lookup"><span data-stu-id="560c2-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="560c2-140">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="560c2-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="560c2-141">`false`- "Gannen" ou "1" é suportado</span><span class="sxs-lookup"><span data-stu-id="560c2-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="560c2-142">`true`- apenas "1" é suportado</span><span class="sxs-lookup"><span data-stu-id="560c2-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="560c2-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="560c2-143">**Environment variable**</span></span> | <span data-ttu-id="560c2-144">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-144">N/A</span></span> | <span data-ttu-id="560c2-145">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="560c2-146">Formato do ano japonês</span><span class="sxs-lookup"><span data-stu-id="560c2-146">Japanese year format</span></span>

- <span data-ttu-id="560c2-147">Determina se o primeiro ano de uma era de calendário japonês é formatado como "Gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="560c2-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="560c2-148">Padrão: Formatar o primeiro ano`false`como "Gannen" ( ).</span><span class="sxs-lookup"><span data-stu-id="560c2-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="560c2-149">Para obter mais informações, consulte [Representar datas em calendários com várias eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="560c2-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="560c2-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="560c2-150">Setting name</span></span> | <span data-ttu-id="560c2-151">Valores</span><span class="sxs-lookup"><span data-stu-id="560c2-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="560c2-152">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="560c2-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="560c2-153">`false`- formato como "Gannen"</span><span class="sxs-lookup"><span data-stu-id="560c2-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="560c2-154">`true`- formato como número</span><span class="sxs-lookup"><span data-stu-id="560c2-154">`true` - format as number</span></span> |
| <span data-ttu-id="560c2-155">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="560c2-155">**Environment variable**</span></span> | <span data-ttu-id="560c2-156">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-156">N/A</span></span> | <span data-ttu-id="560c2-157">N/D</span><span class="sxs-lookup"><span data-stu-id="560c2-157">N/A</span></span> |
