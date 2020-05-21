---
title: Definições de configuração de globalização
description: Saiba mais sobre as configurações de tempo de execução que configuram aspectos de globalização de um aplicativo .NET Core, por exemplo, como ele analisa as datas japonesas.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 56228e9a6cb6dbab6a22bdc00d11212e1019776b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761961"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="c123c-103">Opções de configuração de tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="c123c-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="c123c-104">Modo invariável</span><span class="sxs-lookup"><span data-stu-id="c123c-104">Invariant mode</span></span>

- <span data-ttu-id="c123c-105">Determina se um aplicativo .NET Core é executado no modo inconstante de globalização sem acesso a dados e comportamento específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="c123c-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="c123c-106">Se você omitir essa configuração, o aplicativo será executado com acesso aos dados culturais.</span><span class="sxs-lookup"><span data-stu-id="c123c-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="c123c-107">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c123c-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="c123c-108">Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="c123c-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="c123c-109">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c123c-109">Setting name</span></span> | <span data-ttu-id="c123c-110">Valores</span><span class="sxs-lookup"><span data-stu-id="c123c-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c123c-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c123c-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="c123c-112">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="c123c-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="c123c-113">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="c123c-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="c123c-114">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="c123c-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="c123c-115">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="c123c-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="c123c-116">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="c123c-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="c123c-117">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c123c-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="c123c-118">`0`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="c123c-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="c123c-119">`1`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="c123c-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="c123c-120">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c123c-120">Examples</span></span>

<span data-ttu-id="c123c-121">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="c123c-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="c123c-122">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="c123c-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="c123c-123">Intervalos de ano da era</span><span class="sxs-lookup"><span data-stu-id="c123c-123">Era year ranges</span></span>

- <span data-ttu-id="c123c-124">Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="c123c-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="c123c-125">Se você omitir essa configuração, as verificações de intervalo serão relaxadas.</span><span class="sxs-lookup"><span data-stu-id="c123c-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="c123c-126">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c123c-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="c123c-127">Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="c123c-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="c123c-128">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c123c-128">Setting name</span></span> | <span data-ttu-id="c123c-129">Valores</span><span class="sxs-lookup"><span data-stu-id="c123c-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c123c-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c123c-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="c123c-131">`false`-verificações de intervalo relaxadas</span><span class="sxs-lookup"><span data-stu-id="c123c-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="c123c-132">`true`-estouros causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="c123c-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="c123c-133">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c123c-133">**Environment variable**</span></span> | <span data-ttu-id="c123c-134">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-134">N/A</span></span> | <span data-ttu-id="c123c-135">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="c123c-136">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="c123c-136">Japanese date parsing</span></span>

- <span data-ttu-id="c123c-137">Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.</span><span class="sxs-lookup"><span data-stu-id="c123c-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="c123c-138">Se você omitir essa configuração, as cadeias de caracteres que contêm "1" ou "gannen" como o ano é analisado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c123c-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="c123c-139">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c123c-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="c123c-140">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="c123c-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="c123c-141">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c123c-141">Setting name</span></span> | <span data-ttu-id="c123c-142">Valores</span><span class="sxs-lookup"><span data-stu-id="c123c-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c123c-143">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c123c-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="c123c-144">`false`-"Gannen" ou "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="c123c-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="c123c-145">`true`-somente "1" é suportado</span><span class="sxs-lookup"><span data-stu-id="c123c-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="c123c-146">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c123c-146">**Environment variable**</span></span> | <span data-ttu-id="c123c-147">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-147">N/A</span></span> | <span data-ttu-id="c123c-148">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="c123c-149">Formato de ano japonês</span><span class="sxs-lookup"><span data-stu-id="c123c-149">Japanese year format</span></span>

- <span data-ttu-id="c123c-150">Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="c123c-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="c123c-151">Se você omitir essa configuração, o primeiro ano será formatado como "gannen".</span><span class="sxs-lookup"><span data-stu-id="c123c-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="c123c-152">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c123c-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="c123c-153">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="c123c-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="c123c-154">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c123c-154">Setting name</span></span> | <span data-ttu-id="c123c-155">Valores</span><span class="sxs-lookup"><span data-stu-id="c123c-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c123c-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c123c-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="c123c-157">`false`-Formatar como "gannen"</span><span class="sxs-lookup"><span data-stu-id="c123c-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="c123c-158">`true`-Formatar como número</span><span class="sxs-lookup"><span data-stu-id="c123c-158">`true` - format as number</span></span> |
| <span data-ttu-id="c123c-159">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c123c-159">**Environment variable**</span></span> | <span data-ttu-id="c123c-160">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-160">N/A</span></span> | <span data-ttu-id="c123c-161">N/D</span><span class="sxs-lookup"><span data-stu-id="c123c-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="c123c-162">CRIOU</span><span class="sxs-lookup"><span data-stu-id="c123c-162">NLS</span></span>

- <span data-ttu-id="c123c-163">Determina se o .NET usa o NLS (suporte a idioma nacional) ou as APIs de globalização do ICU (componentes internacionais para Unicode) para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="c123c-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="c123c-164">O .NET 5,0 e versões posteriores usam APIs de globalização ICU por padrão no Windows 10 pode ser 2019 atualização e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="c123c-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="c123c-165">Se você omitir essa configuração, o .NET usará APIs de globalização ICU por padrão.</span><span class="sxs-lookup"><span data-stu-id="c123c-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="c123c-166">Isso é equivalente a definir o valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="c123c-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="c123c-167">Para obter mais informações, consulte [APIs de globalização usam bibliotecas ICU no Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="c123c-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="c123c-168">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="c123c-168">Setting name</span></span> | <span data-ttu-id="c123c-169">Valores</span><span class="sxs-lookup"><span data-stu-id="c123c-169">Values</span></span> | <span data-ttu-id="c123c-170">Incluída</span><span class="sxs-lookup"><span data-stu-id="c123c-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="c123c-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c123c-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="c123c-172">`false`-Usar APIs de globalização ICU</span><span class="sxs-lookup"><span data-stu-id="c123c-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="c123c-173">`true`-Usar APIs de globalização NLS</span><span class="sxs-lookup"><span data-stu-id="c123c-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="c123c-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c123c-174">.NET 5.0</span></span> |
| <span data-ttu-id="c123c-175">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="c123c-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="c123c-176">`false`-Usar APIs de globalização ICU</span><span class="sxs-lookup"><span data-stu-id="c123c-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="c123c-177">`true`-Usar APIs de globalização NLS</span><span class="sxs-lookup"><span data-stu-id="c123c-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="c123c-178">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c123c-178">.NET 5.0</span></span> |
