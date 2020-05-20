---
title: Definições de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703131"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="32d6f-103">Opções de configuração de tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="32d6f-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="32d6f-104">Modo invariável</span><span class="sxs-lookup"><span data-stu-id="32d6f-104">Invariant mode</span></span>

- <span data-ttu-id="32d6f-105">Determina se um aplicativo .NET Core é executado no modo inconstante de globalização sem acesso a dados e comportamento específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="32d6f-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="32d6f-106">Padrão: execute o aplicativo com acesso a dados culturais ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="32d6f-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="32d6f-107">Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="32d6f-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="32d6f-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="32d6f-108">Setting name</span></span> | <span data-ttu-id="32d6f-109">Valores</span><span class="sxs-lookup"><span data-stu-id="32d6f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="32d6f-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="32d6f-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="32d6f-111">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="32d6f-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="32d6f-112">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="32d6f-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="32d6f-113">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="32d6f-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="32d6f-114">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="32d6f-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="32d6f-115">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="32d6f-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="32d6f-116">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="32d6f-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="32d6f-117">`0`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="32d6f-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="32d6f-118">`1`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="32d6f-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="32d6f-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="32d6f-119">Examples</span></span>

<span data-ttu-id="32d6f-120">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="32d6f-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="32d6f-121">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="32d6f-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="32d6f-122">Intervalos de ano da era</span><span class="sxs-lookup"><span data-stu-id="32d6f-122">Era year ranges</span></span>

- <span data-ttu-id="32d6f-123">Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="32d6f-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="32d6f-124">Padrão: as verificações de intervalo são relaxadas ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="32d6f-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="32d6f-125">Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="32d6f-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="32d6f-126">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="32d6f-126">Setting name</span></span> | <span data-ttu-id="32d6f-127">Valores</span><span class="sxs-lookup"><span data-stu-id="32d6f-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="32d6f-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="32d6f-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="32d6f-129">`false`-verificações de intervalo relaxadas</span><span class="sxs-lookup"><span data-stu-id="32d6f-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="32d6f-130">`true`-estouros causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="32d6f-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="32d6f-131">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="32d6f-131">**Environment variable**</span></span> | <span data-ttu-id="32d6f-132">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-132">N/A</span></span> | <span data-ttu-id="32d6f-133">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="32d6f-134">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="32d6f-134">Japanese date parsing</span></span>

- <span data-ttu-id="32d6f-135">Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.</span><span class="sxs-lookup"><span data-stu-id="32d6f-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="32d6f-136">Padrão: analise as cadeias de caracteres que contêm "1" ou "gannen" como o ano ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="32d6f-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="32d6f-137">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="32d6f-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="32d6f-138">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="32d6f-138">Setting name</span></span> | <span data-ttu-id="32d6f-139">Valores</span><span class="sxs-lookup"><span data-stu-id="32d6f-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="32d6f-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="32d6f-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="32d6f-141">`false`-"Gannen" ou "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="32d6f-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="32d6f-142">`true`-somente "1" é suportado</span><span class="sxs-lookup"><span data-stu-id="32d6f-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="32d6f-143">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="32d6f-143">**Environment variable**</span></span> | <span data-ttu-id="32d6f-144">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-144">N/A</span></span> | <span data-ttu-id="32d6f-145">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="32d6f-146">Formato de ano japonês</span><span class="sxs-lookup"><span data-stu-id="32d6f-146">Japanese year format</span></span>

- <span data-ttu-id="32d6f-147">Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="32d6f-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="32d6f-148">Padrão: formate o primeiro ano como "gannen" ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="32d6f-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="32d6f-149">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="32d6f-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="32d6f-150">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="32d6f-150">Setting name</span></span> | <span data-ttu-id="32d6f-151">Valores</span><span class="sxs-lookup"><span data-stu-id="32d6f-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="32d6f-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="32d6f-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="32d6f-153">`false`-Formatar como "gannen"</span><span class="sxs-lookup"><span data-stu-id="32d6f-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="32d6f-154">`true`-Formatar como número</span><span class="sxs-lookup"><span data-stu-id="32d6f-154">`true` - format as number</span></span> |
| <span data-ttu-id="32d6f-155">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="32d6f-155">**Environment variable**</span></span> | <span data-ttu-id="32d6f-156">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-156">N/A</span></span> | <span data-ttu-id="32d6f-157">N/D</span><span class="sxs-lookup"><span data-stu-id="32d6f-157">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="32d6f-158">CRIOU</span><span class="sxs-lookup"><span data-stu-id="32d6f-158">NLS</span></span>

- <span data-ttu-id="32d6f-159">Determina se o .NET usa o NLS (suporte a idioma nacional) ou as APIs de globalização do ICU (componentes internacionais para Unicode) para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="32d6f-159">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="32d6f-160">O .NET 5,0 e versões posteriores usam APIs de globalização ICU por padrão no Windows 10 pode ser 2019 atualização e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="32d6f-160">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="32d6f-161">Se você omitir essa configuração, o .NET usará APIs de globalização ICU por padrão.</span><span class="sxs-lookup"><span data-stu-id="32d6f-161">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="32d6f-162">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="32d6f-162">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="32d6f-163">Para obter mais informações, consulte [APIs de globalização usam bibliotecas ICU no Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="32d6f-163">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="32d6f-164">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="32d6f-164">Setting name</span></span> | <span data-ttu-id="32d6f-165">Valores</span><span class="sxs-lookup"><span data-stu-id="32d6f-165">Values</span></span> | <span data-ttu-id="32d6f-166">Incluída</span><span class="sxs-lookup"><span data-stu-id="32d6f-166">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="32d6f-167">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="32d6f-167">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="32d6f-168">`false`-Usar APIs de globalização ICU</span><span class="sxs-lookup"><span data-stu-id="32d6f-168">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="32d6f-169">`true`-Usar APIs de globalização NLS</span><span class="sxs-lookup"><span data-stu-id="32d6f-169">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="32d6f-170">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="32d6f-170">.NET 5.0</span></span> |
| <span data-ttu-id="32d6f-171">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="32d6f-171">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="32d6f-172">`false`-Usar APIs de globalização ICU</span><span class="sxs-lookup"><span data-stu-id="32d6f-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="32d6f-173">`true`-Usar APIs de globalização NLS</span><span class="sxs-lookup"><span data-stu-id="32d6f-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="32d6f-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="32d6f-174">.NET 5.0</span></span> |
