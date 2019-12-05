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
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="fdee1-103">Opções de configuração de tempo de execução para globalização</span><span class="sxs-lookup"><span data-stu-id="fdee1-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="fdee1-104">Modo invariável</span><span class="sxs-lookup"><span data-stu-id="fdee1-104">Invariant mode</span></span>

- <span data-ttu-id="fdee1-105">Determina se um aplicativo .NET Core é executado no modo invariável de globalização sem acesso a dados e comportamento específicos de cultura ou se tem acesso a dados culturais.</span><span class="sxs-lookup"><span data-stu-id="fdee1-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="fdee1-106">Padrão: execute o aplicativo com acesso a dados culturais (`false`).</span><span class="sxs-lookup"><span data-stu-id="fdee1-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="fdee1-107">Para obter mais informações, consulte [modo invariável de globalização do .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="fdee1-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="fdee1-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fdee1-108">Setting name</span></span> | <span data-ttu-id="fdee1-109">Valores</span><span class="sxs-lookup"><span data-stu-id="fdee1-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fdee1-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fdee1-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="fdee1-111">`false`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="fdee1-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="fdee1-112">`true`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="fdee1-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="fdee1-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fdee1-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="fdee1-114">`0`-acesso a dados culturais</span><span class="sxs-lookup"><span data-stu-id="fdee1-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="fdee1-115">`1`-executar em modo invariável</span><span class="sxs-lookup"><span data-stu-id="fdee1-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="fdee1-116">Intervalos de ano da era</span><span class="sxs-lookup"><span data-stu-id="fdee1-116">Era year ranges</span></span>

- <span data-ttu-id="fdee1-117">Determina se o intervalo verifica se os calendários que dão suporte a vários apagamentos são relaxados ou se as datas que excedem o intervalo de datas de uma época lançam um <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="fdee1-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="fdee1-118">Padrão: as verificações de intervalo são relaxadas (`false`).</span><span class="sxs-lookup"><span data-stu-id="fdee1-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="fdee1-119">Para obter mais informações, consulte [calendários, apagar e intervalos de datas: verificações de intervalo relaxadas](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="fdee1-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="fdee1-120">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fdee1-120">Setting name</span></span> | <span data-ttu-id="fdee1-121">Valores</span><span class="sxs-lookup"><span data-stu-id="fdee1-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fdee1-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fdee1-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="fdee1-123">`false`-verificações de intervalo relaxadas</span><span class="sxs-lookup"><span data-stu-id="fdee1-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="fdee1-124">`true`-estouros causam uma exceção</span><span class="sxs-lookup"><span data-stu-id="fdee1-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="fdee1-125">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fdee1-125">**Environment variable**</span></span> | <span data-ttu-id="fdee1-126">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-126">N/A</span></span> | <span data-ttu-id="fdee1-127">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="fdee1-128">Análise de data japonesa</span><span class="sxs-lookup"><span data-stu-id="fdee1-128">Japanese date parsing</span></span>

- <span data-ttu-id="fdee1-129">Determina se uma cadeia de caracteres que contém "1" ou "gannen" como o ano é analisada com êxito ou se apenas "1" tem suporte.</span><span class="sxs-lookup"><span data-stu-id="fdee1-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="fdee1-130">Padrão: analise as cadeias de caracteres que contêm "1" ou "gannen" como o ano (`false`).</span><span class="sxs-lookup"><span data-stu-id="fdee1-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="fdee1-131">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="fdee1-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="fdee1-132">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fdee1-132">Setting name</span></span> | <span data-ttu-id="fdee1-133">Valores</span><span class="sxs-lookup"><span data-stu-id="fdee1-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fdee1-134">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fdee1-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="fdee1-135">`false`-"gannen" ou "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="fdee1-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="fdee1-136">somente `true` "1" tem suporte</span><span class="sxs-lookup"><span data-stu-id="fdee1-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="fdee1-137">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fdee1-137">**Environment variable**</span></span> | <span data-ttu-id="fdee1-138">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-138">N/A</span></span> | <span data-ttu-id="fdee1-139">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="fdee1-140">Formato de ano japonês</span><span class="sxs-lookup"><span data-stu-id="fdee1-140">Japanese year format</span></span>

- <span data-ttu-id="fdee1-141">Determina se o primeiro ano de uma era do calendário japonês é formatado como "gannen" ou como um número.</span><span class="sxs-lookup"><span data-stu-id="fdee1-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="fdee1-142">Padrão: formate o primeiro ano como "gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="fdee1-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="fdee1-143">Para obter mais informações, consulte [representar datas em calendários com vários apagar](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="fdee1-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="fdee1-144">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="fdee1-144">Setting name</span></span> | <span data-ttu-id="fdee1-145">Valores</span><span class="sxs-lookup"><span data-stu-id="fdee1-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fdee1-146">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="fdee1-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="fdee1-147">`false`-Format como "gannen"</span><span class="sxs-lookup"><span data-stu-id="fdee1-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="fdee1-148">`true`-Formatar como número</span><span class="sxs-lookup"><span data-stu-id="fdee1-148">`true` - format as number</span></span> |
| <span data-ttu-id="fdee1-149">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="fdee1-149">**Environment variable**</span></span> | <span data-ttu-id="fdee1-150">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-150">N/A</span></span> | <span data-ttu-id="fdee1-151">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fdee1-151">N/A</span></span> |
